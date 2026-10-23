# Security

This page is long on purpose. Its headings should show up under Security in the left navigation, not in a column on the right.

## Identity

Every request carries a token issued by the identity broker. The runtime does not accept raw corporate passwords.

### Token lifetime

Access tokens last fifteen minutes. Refresh tokens last twelve hours and are rotated on use.

### Service identity

A workload uses a projected service account token. That token is not a user token and cannot call user-only APIs.

## Network

Traffic enters through the edge gateway. Pods do not expose public addresses.

### Ingress

Only ports 443 and 8443 are open on the gateway. Admin traffic uses 8443 and a separate hostname.

### East-west

Namespaces cannot talk to each other except through the gateway. The policy is default deny.

## Data

Customer content is encrypted at rest and in transit. Keys are regional.

### At rest

Object storage and the database use separate keys. Rotating one does not rewrap the other.

### In transit

TLS is required inside the cluster as well as at the edge. Plaintext listeners fail the deploy.

## Secrets

Secrets live in the platform secret store. They are not committed to this repository.

### Injection

A pod receives secrets as files, not as environment variables. The files are memory-backed.

### Rotation

Database passwords rotate every thirty days. The workload picks up the new file without a restart.
