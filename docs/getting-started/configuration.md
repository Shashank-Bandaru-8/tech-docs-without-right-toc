# Configuration

This page documents the settings that change how the sample renders. The only setting that moves the table of contents is the theme feature. The rest exist so the site looks like a real TechDocs repository.

## mkdocs.yml

The file sits at the repository root. TechDocs discovers it from the `backstage.io/techdocs-ref` annotation.

### Site metadata

`site_name` is the title in the generated HTML. `site_description` is metadata only. `repo_url` and `edit_uri` enable the edit link TechDocs shows when both are present.

### Navigation

The `nav` list is explicit. Pages that are not listed are omitted from the left navigation even if the file exists. That matters once headings are integrated, because an unlisted page has nowhere to attach its sections.

### Plugins

`techdocs-core` is required for IDP. It sets the Material theme defaults, search, and the TechDocs-friendly Markdown extensions. Do not replace it with a plain `mkdocs` plugin list.

### Theme features

`toc.integrate` is the feature under test. `navigation.expand` is not set, so left-nav sections can collapse.

## toc.integrate

Material still builds a table of contents from headings. It renders that list inside the primary navigation, under the active page, and does not emit the secondary sidebar.

### Which headings are included

Level-two and level-three headings are included. The page title, which is the level-one heading, is the page node itself and is not repeated.

### What is not included

Bold text, definition lists, and HTML headings that MkDocs does not treat as Markdown headings stay out of the list. Stick to normal Markdown headings.

### Permalinks

`techdocs-core` enables heading permalinks. The paragraph-link icon in the article is independent of the sidebar. Integrating the table of contents does not remove those icons.

## Local versus IDP

Local `mkdocs serve` and the IDP reader do not paint the page the same way.

### Local Material

Locally, integrating the table of contents also gives the article the full content width. There is no second column.

### IDP reader

The IDP reader injects its own stylesheet after the generated CSS. That stylesheet sizes the article as if both sidebars were present. Expect the list to disappear and a band of unused space to remain on the right until the reader itself changes.
