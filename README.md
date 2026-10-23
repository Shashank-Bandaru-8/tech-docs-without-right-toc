# TechDocs without the right-hand table of contents

Sample MkDocs site for Harness IDP TechDocs. The theme feature `toc.integrate` removes the right-hand on-page table of contents and lists those headings under the current page in the left navigation.

## What to look for

Open any page that has several headings, for example **Platform → Architecture**. The section links that normally sit on the right (`Runtime`, `Request path`, `Storage`) appear nested under that page in the left sidebar.

`site_name` is required by MkDocs. IDP already removes the MkDocs header, so that title would otherwise sit at the top of the left nav. That is unrelated to `toc.integrate`.

A normal `extra.css` does not load in IDP. The sanitizer drops stylesheet links that are not MkDocs hashed theme CSS (`main.<8 hex>.min.css`). This sample uses `docs/stylesheets/main.a1b2c3d4.min.css` so the override can actually apply. Rebuild TechDocs after pulling.

Preview locally with `mkdocs serve` after installing `mkdocs-techdocs-core`. Point a TechDocs build at this repository root, where `mkdocs.yml` lives.
