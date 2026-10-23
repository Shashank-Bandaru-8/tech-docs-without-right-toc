# TechDocs without the right-hand table of contents

Sample MkDocs site for Harness IDP TechDocs. The theme feature `toc.integrate` removes the right-hand on-page table of contents and lists those headings under the current page in the left navigation.

## What to look for

Open any page that has several headings, for example **Platform → Architecture**. The section links that normally sit on the right (`Runtime`, `Request path`, `Storage`) appear nested under that page in the left sidebar.

Preview locally with `mkdocs serve` after installing `mkdocs-techdocs-core`. Point a TechDocs build at this repository root, where `mkdocs.yml` lives.
