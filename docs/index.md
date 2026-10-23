# TechDocs without a right-hand table of contents

This site is a long sample so you can see how MkDocs Material behaves when `toc.integrate` is enabled. Every page below has enough headings that a normal TechDocs render would show a table of contents on the right. With this configuration those headings are folded into the left navigation instead.

## What changed

`mkdocs.yml` sets the Material feature `toc.integrate`. The docs generator still builds a table of contents from the headings on the page. The reader no longer paints that list as a second sidebar.

## How to read this sample

Walk the left navigation from top to bottom. Expand a page and you should see its sections listed underneath it. The main column should be the only place the article itself is rendered.

## Pages in this site

The sample is split so the left navigation is busy enough to resemble a real service handbook.

### Getting started

Install steps, configuration, and the first local preview.

### Guides

How authors should write headings, how the integrated table of contents behaves, and how a docs build is published.

### Platform

Architecture, security, and operations write-ups with deep heading trees.

### Reference

The exact MkDocs options used here, the theme feature, and a short FAQ.

## A section with nested headings

Use this page as a quick check that level-two and level-three headings both show up in the integrated list.

### Level three under the nested section

This paragraph exists so the heading is not empty. Integrated navigation links scroll to this anchor.

### Another level three heading

A second child heading makes it obvious that the list is a table of contents, not a flat page title.

## What you should not see

On a wide window there should be no "On this page" column pinned to the right of the article. The Harness IDP reader still reserves some horizontal space for that column, so the article may not stretch all the way to the right edge. The list itself should be gone.
