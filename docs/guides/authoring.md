# Authoring pages

Write pages as if every heading will become a navigation item. That is true for this site, and it is a good habit even when the right-hand table of contents is visible.

## Page shape

A page has one level-one heading, then sections. The level-one heading must match the title readers expect in the left navigation.

### Title

Use a short noun phrase. "Authoring pages" is a title. "This page explains how to author pages in the portal" is a sentence and makes a poor navigation label.

### Introduction

Two or three sentences under the title tell the reader whether they are on the right page. Do not add a "Introduction" heading for that text. An extra heading only to label the introduction shows up in the integrated list.

### Sections

Level-two headings are the table of contents. Give each one a name that still makes sense when it is indented under the page.

## Heading depth

Three levels is enough for this handbook. Deeper headings become a noisy left navigation once they are integrated.

### Level two

A level-two heading is a section a reader might jump to. Examples: Prerequisites, Clone the repository, Troubleshooting.

### Level three

A level-three heading is a step or a sub-case inside a section. Keep the set small. Four children under one section is a signal to split the section.

### Level four and below

Avoid them. They rarely survive as useful navigation items, and Material's integrated table of contents becomes hard to scan.

## Writing the body

The body under a heading should answer the heading. If it does not, rename the heading or move the text.

### Paragraphs

Prefer short paragraphs. A section that is one long paragraph gives the reader a heading and then no place to rest.

### Lists

Use a list when the items are parallel. Do not use a list as a substitute for headings. List items do not appear in the table of contents.

### Code samples

Fence commands with a language tag. Keep samples copy-pasteable. Explain the sample in the paragraph above it, not in comments inside it.

### Tables

Use a table for a small matrix, such as which environment variable applies where. A table is not a heading, so it will not appear in the integrated navigation. Put a heading above any table a reader needs to find.

## Cross links

Link to another page by its path relative to `docs/`.

### Same section

From this page, the navigation guide is `navigation.md`.

### Another section

The architecture page is `../platform/architecture.md`.

### Anchors

You can link to a heading on another page with the generated anchor, for example `../platform/architecture.md#request-path`. Anchors follow MkDocs slug rules: lowercase, hyphens, punctuation removed.

## Review checklist

Run through this list before you open a pull request. The integrated navigation makes weak headings more visible, not less.

### Titles

The level-one heading matches the `nav` label closely enough that a reader is not surprised.

### Sections

Every level-two heading is something you would put in a table of contents. If you would not, flatten it into body text.

### Length

A page that scrolls for several screens is fine. A page whose integrated list is longer than the window is not. Split it.

### Local preview

Serve the site and open the page. Confirm the new headings appear under the page in the left navigation and that nothing unexpected appears on the right.
