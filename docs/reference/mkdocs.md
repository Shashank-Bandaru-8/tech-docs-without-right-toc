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

IDP sanitizes TechDocs HTML and only keeps stylesheet links whose href matches `main.<8 hex chars>.min.css` (plus Google Fonts). A normal `extra.css` is stripped, which is why the earlier width override did nothing.

This sample names the file `stylesheets/main.a1b2c3d4.min.css` so it survives that allowlist. That is an experiment only, not a supported Kaiser workaround.

The file hides the leftover `site_name` in the left nav, and it overrides IDP's `max-width: calc(100% - 16.5rem * 2)` plus Material's desktop `margin-right` so the article can fill the space next to the left nav.
