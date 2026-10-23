# Operations

Use this page to see a second long outline. Incident steps are headings so they appear in the integrated table of contents.

## Signals

Operators watch three signals. Each one has a page section so you can jump straight to it.

### Availability

The edge gateway reports success rate per tenant. A tenant under 99 percent for five minutes pages the primary.

### Saturation

CPU above 70 percent for ten minutes, or queue depth above ten thousand, pages the worker owner.

### Freshness

Docs bundles older than the default branch by more than a day show a warning. They do not page.

## Incident flow

The flow is the same in every region.

### Declare

The commander opens an incident and names the tenant and the region. Speculation about cause waits until the timeline exists.

### Mitigate

Mitigation is a rollback or a traffic shift. Diagnosis continues after users are healthy.

### Resolve

The incident closes when the success rate holds for thirty minutes and the rollback or fix is recorded.

## Rollback

Rollback restores the previous image and the previous docs bundle together.

### Runtime

The release controller points the deployment at the previous digest. In-flight requests finish on the old pods.

### Docs

The docs pointer moves back one commit. A docs-only rollback skips the runtime stage.

## Evacuation

A region loss is manual. There is no automatic failover.

### Freeze

Stop deploys into the failed region. In-flight builds are cancelled.

### Redirect

Update the edge routing table so hostnames for that region resolve to the designated backup region.

### Tell tenants

Send the status note from the template. Do not promise a restore time that engineering has not confirmed.
