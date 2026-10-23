# Publishing

Publishing turns the Markdown in this repository into the HTML that IDP renders. The theme feature is applied at build time. Changing `mkdocs.yml` does nothing until the next successful build.

## Build inputs

The builder reads a small set of files. Extra files in the repository are ignored unless `nav` or an inclusion links them.

### mkdocs.yml

Parsed first. Plugin and theme settings come from here. A syntax error fails the build before any page is rendered.

### docs directory

Every page in `nav` must exist under `docs/`. A missing file fails the build with the path MkDocs expected.

## Build steps

The pipeline is the same for this sample and for a service repository.

### Fetch

The builder clones this repository. `mkdocs.yml` at the root is the build entry point.

### Install

The TechDocs image already contains MkDocs and `mkdocs-techdocs-core`. You do not commit a lockfile for this sample.

### Generate

`mkdocs build` writes a static site. `toc.integrate` changes the HTML of every page during this step. The published HTML does not contain the secondary sidebar markup.

### Publish

The static site is uploaded to the TechDocs storage bucket configured for the account. IDP reads from that bucket. It does not run MkDocs in the browser.

## Verifying a publish

After the build is green, confirm the feature in the product, not only in the build log.

### Open the site

Open the built site and pick a page with several headings.

### Pick a long page

Open Navigation and the table of contents or Architecture. Short pages hide the difference because they have nothing to list.

### Check both columns

The left navigation should contain the page headings. The right side of the article should not contain a second list. Unused space on the right is expected with the current IDP reader stylesheet.

## When the old sidebar comes back

If the right-hand list is still there, the published HTML was built without the feature.

### Stale bundle

The reader caches the last successful site. Trigger a fresh build and hard-refresh.

### Feature not in the built file

Open the raw generated page if you have access to the bucket, and search for `md-sidebar--secondary`. A `hidden` attribute, or no secondary sidebar at all, means integrate worked. A visible secondary sidebar means the build did not see `toc.integrate`.

### Forked mkdocs.yml

Some repositories keep docs in a subdirectory with their own config. The file that matters is the `mkdocs.yml` at the repository root, not a copy elsewhere in a monorepo.
