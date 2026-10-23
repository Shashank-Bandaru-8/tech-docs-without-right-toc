# Overview

This handbook describes a fictional internal platform called Northwind Runtime. The content is invented so the table of contents has something real to attach to. Nothing here is a production runbook.

## Why this site exists

Kaiser asked whether the right-hand table of contents on catalog documents can be removed. This repository is the customer-side experiment: the same docs, built with `toc.integrate`, so the headings move into the left navigation.

## Who it is for

Three audiences use the same site. Each audience cares about a different slice of the left navigation.

### Platform engineers

They own the runtime, the docs pipeline, and the theme settings in `mkdocs.yml`.

### Service owners

They write the pages under Guides and Platform. They need headings that stay useful after the table of contents moves.

### Operators

They use Operations and Security during an incident. They need anchors they can paste into a ticket.

## What the runtime does

Northwind Runtime hosts internal web applications, background workers, and a small set of scheduled jobs. It is not a general compute platform.

### Web applications

Request-driven services with a public ingress, a private admin port, and a health endpoint.

### Background workers

Queue consumers that share the same container image as the web process and a different command.

### Scheduled jobs

Cron-style tasks that run to completion and exit. They do not stay resident.

## Documentation principles

Keep the rules short so authors do not invent a second navigation scheme.

### One topic per page

If a page needs more than about eight level-two headings, split it.

### Headings are the table of contents

After `toc.integrate`, every heading is a navigation item. Write headings as labels, not as sentences.

### No duplicate titles

The page title and the first section should not say the same thing. The page title is already in the left navigation.

## How the sample is organized

The information architecture is fixed so you can compare pages.

### Getting started

Concepts, install, and configuration. Read these before changing theme features.

### Guides

Authoring and publishing. This is the path a service owner follows.

### Platform and reference

Deeper material. These pages are intentionally long so the integrated list gets tall.

## Success criteria for the experiment

Use this checklist when you open the site in IDP.

### Right sidebar

The on-page table of contents is not rendered on the right.

### Left sidebar

The current page lists its sections underneath the page title.

### Content width

The article may still sit in a narrower column, because the IDP reader stylesheet reserves room for both sidebars. That gap is separate from whether the list is visible.
