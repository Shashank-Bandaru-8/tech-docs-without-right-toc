# MkDocs options

These are the options in the root `mkdocs.yml` and why each one is set.

## site_name

MkDocs requires this field. Material would otherwise print it at the top of the left navigation. This sample hides that title with `extra_css`; it has nothing to do with `toc.integrate`.

## docs_dir

Pages live under `docs/`. The config file stays at the repository root so a TechDocs build can find it.

## nav

The left-hand site map. Every file you want readers to open is listed here. Headings inside a listed page are added automatically by `toc.integrate`.

## plugins

`techdocs-core` is the TechDocs plugin. It selects the Material theme and the Markdown extensions IDP expects.

## theme.name

Set to `material`. The integrate feature belongs to that theme.

## theme.features

`toc.integrate` moves the on-page table of contents into the left navigation and omits the right-hand sidebar.

## extra_css

Hides `.md-nav--primary > .md-nav__title` so `site_name` is not stuck at the top of the IDP sidebar.

IDP always sizes the article as if a right-hand table of contents were present (`max-width: calc(100% - 16.5rem * 2)`). That gap is from the reader, not from `toc.integrate`. This sample overrides it so the article uses the remaining width next to the left nav.
