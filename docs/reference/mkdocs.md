# MkDocs options

These are the options in the root `mkdocs.yml` and why each one is set.

## site_name

Shown as the site title. It does not change the table of contents.

## docs_dir

Pages live under `docs/`. The config file stays at the repository root so a TechDocs build can find it.

## nav

The left-hand site map. Every file you want readers to open is listed here. Headings inside a listed page are added automatically by `toc.integrate`.

## plugins

`techdocs-core` is the TechDocs plugin. It selects the Material theme and the Markdown extensions IDP expects.

## theme.name

Set to `material`. The integrate feature belongs to that theme.

## theme.features

`navigation.expand` keeps sections open. `toc.integrate` moves the on-page table of contents into the left navigation and omits the right-hand sidebar.
