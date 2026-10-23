# Navigation and the table of contents

This page is the one to stare at while you compare a normal TechDocs site with this one. It describes both navigation systems and then gives you a tall heading tree on purpose.

## Two navigation systems

MkDocs Material renders two lists. TechDocs shows both, and readers often describe the right-hand one as "the table of contents".

### Primary navigation

The primary navigation is the site map from the `nav` key in `mkdocs.yml`. It lists pages and sections. It is the left sidebar in IDP.

### Secondary navigation

The secondary navigation is built from the headings on the current page. Material calls it the table of contents. It is the right sidebar in a default TechDocs page.

### What integrate does

`toc.integrate` keeps both sets of links and draws them in one place. The site map stays as it was. The current page's headings are inserted beneath that page. The secondary sidebar is not rendered.

## How a reader moves

The gestures change slightly, which is the behavior you are checking.

### Jumping inside a page

Click a heading under the current page in the left navigation. The article scrolls to that heading. The address bar gains a hash.

### Changing pages

Click a different page title. The integrated heading list for the previous page collapses away, and the new page's headings appear under the new title.

### Browser back

The hash is a normal URL fragment. Back returns you to the previous heading as well as the previous page.

## A deliberately long outline

The rest of this page exists so the integrated list is long. Read the labels in the left navigation more than the paragraphs.

## Regions

Northwind Runtime is deployed in four regions. Each region is an isolated failure domain.

### us-west

Serves the default tenant traffic. Build artifacts are published here first.

### us-east

Serves the second tenant group. It receives artifacts after us-west is healthy.

### eu-central

Data-residency region. Customer content tagged for the EU stays in this region.

### ap-south

Newest region. Capacity is smaller, and the runbooks still call out manual steps.

## Environments

Each region has the same three environments. The names are stable so links do not rot.

### dev

Shared integration environment. Docs previews for pull requests are published here and nowhere else.

### staging

Production-shaped data with masked fields. Releases sit here for one business day.

### prod

Customer traffic. Changes require the operations checklist later in this site.

## Services

The platform is a handful of services. Listing them here gives the table of contents another block of children.

### edge-gateway

Terminates TLS and routes by hostname. It does not contain business logic.

### identity-broker

Exchanges the corporate identity token for a runtime token. Pages that mention auth mean this service.

### docs-builder

Clones the repository, runs MkDocs, and uploads the site. This sample is an input to that service.

### config-sync

Reads deploy manifests and updates the runtime config index. It does not build docs.

## Release trains

Releases are weekly. The names below are the phases a change passes through. They are headings so you can see a third cluster of links.

### cut

The release branch is cut on Monday. Docs changes merged after the cut wait for the next train unless they are called out as docs-only.

### bake

Staging runs the branch for a day. Broken anchors and missing pages are treated as release defects.

### promote

Production promotion is Wednesday. The docs site and the runtime promote together so a runbook never describes a build that is not live.

### rollback

Rollback restores the previous site bundle as well as the previous runtime image. A docs-only rollback is possible and uses the same pipeline with the runtime stage skipped.
