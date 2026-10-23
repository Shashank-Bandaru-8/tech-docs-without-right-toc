# Architecture

Northwind Runtime is a small platform with a deliberate shape. This page is long so the integrated table of contents has a realistic outline: several level-two sections, each with a few level-three children.

## Runtime

The runtime is the set of processes that serve tenant traffic. It is distinct from the docs builder and the catalog sync, which are control-plane tools.

### Processes

A deployment is one container image and two process types. The web process serves HTTP. The worker process consumes a queue. They share configuration and differ by command.

### Isolation

Each tenant gets a namespace. Network policy denies cross-namespace traffic except through the edge gateway. A noisy tenant cannot open connections to another tenant's pods.

### Scaling

The web process scales on CPU and on concurrent requests. The worker scales on queue depth. Scheduled jobs do not scale; a second replica would double-run the job.

## Request path

A user request crosses three hops. Knowing the hops makes the later security and operations pages easier to follow.

### Client to edge

The client talks only to the edge gateway. TLS terminates there. The gateway checks the hostname against the tenant routing table and rejects unknown hosts.

### Edge to broker

Authenticated routes call the identity broker before they call the application. The broker validates the corporate token and mints a short-lived runtime token. The application never sees the corporate token.

### Broker to application

The application receives the runtime token and the tenant id. It does not call the corporate identity provider itself. That keeps application teams from inventing a second login.

## Storage

State is split by how long it must live and by who is allowed to read it.

### Primary database

Each tenant has a schema in a regional Postgres cluster. The application role can read and write its schema and nothing else. Migrations run as a separate role during deploy.

### Object storage

Large artifacts, including published TechDocs bundles, live in object storage. Docs bundles are keyed by account, entity, and commit. A rollback points the entity at the previous commit's prefix.

### Cache

A regional cache holds routing data and rendered feature flags. It is disposable. Losing the cache slows requests and does not lose data.

## Control plane

The control plane is everything that is not on the request path. It can be down without taking tenant traffic down, with one exception noted below.

### Config sync

Config sync polls Git remotes for deploy manifests. It updates the runtime config index. It does not build documentation.

### Docs builder

The docs builder watches this repository for commits that change `mkdocs.yml` or `docs/`. It builds the site and writes the bundle. If it is down, existing docs stay readable and new commits do not appear.

### Release controller

The release controller is the exception. It rolls deployments. If it is down, you cannot ship, but already-running processes keep serving.

## Failure domains

Design reviews for this platform start from failure domains rather than from component boxes.

### Zone

A zone loss drops one replica of each web deployment. The service stays up if at least two zones were healthy. Workers are zone-spread the same way. Jobs are pinned to one zone and retried in another on failure.

### Region

A region loss is a customer-visible event for tenants homed there. There is no transparent cross-region failover. The operations page describes the manual evacuation.

### Control plane

A control-plane loss stops deploys and docs builds. It does not stop the request path. Incident commanders should say that out loud, because responders often assume the opposite.

## Extension points

Application teams can extend the runtime in three ways. Each way has a docs page they are expected to update.

### Configuration

Environment-specific values live in the deploy manifest. They are not compiled into the image. A change to configuration is still a release.

### Hooks

A service may register a startup hook and a shutdown hook. Hooks have a time budget. A hook that exceeds the budget fails the deploy.

### Sidecars

Sidecars are allowed for logging and for a corporate proxy. Other sidecars need a platform review because they share the pod's network identity.
