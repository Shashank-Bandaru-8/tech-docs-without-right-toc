# Install

These steps prepare a laptop to preview the sample the same way TechDocs will build it. They assume macOS or Linux and a working Python 3.11 environment.

## Prerequisites

Install the tools before you clone anything. The docs build fails in confusing ways when one of them is missing.

### Python

Use Python 3.11 or newer. TechDocs container images vary, but 3.11 matches the current MkDocs releases this sample was written against.

### pip

`pip` must be able to install packages into a virtual environment. System Python on some corporate laptops blocks that. Use a virtual environment either way.

### Git

You need Git to clone this repository.

## Clone the repository

The sample lives in a single repository. There is no separate docs remote.

### Clone command

```bash
git clone https://github.com/Shashank-Bandaru-8/tech-docs-without-right-toc.git
cd tech-docs-without-right-toc
```

### What you should see

A `mkdocs.yml` at the repository root and a `docs/` directory.

## Create a virtual environment

Keep MkDocs out of the system interpreter.

### Create and activate

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

### Install the docs toolchain

```bash
pip install mkdocs-techdocs-core
```

`mkdocs-techdocs-core` pulls MkDocs and the Material theme. That is the same plugin named in `mkdocs.yml`.

## Preview locally

Serve the site and click through the long pages. Local preview is the fastest way to confirm `toc.integrate` before an IDP build.

### Start the server

```bash
mkdocs serve
```

Open the printed local URL. The default port is 8000.

### Pages to click

Open Platform, then Architecture. Scroll the left navigation. The sections Runtime, Request path, and Storage should be nested under Architecture, not pinned to the right of the article.

## Troubleshooting

Most local failures are environment problems, not content problems.

### Plugin not found

If MkDocs reports that `techdocs-core` is missing, the virtual environment is not active or `mkdocs-techdocs-core` did not install.

### Theme feature ignored

`toc.integrate` only applies when `theme.name` is `material`. This sample sets that explicitly. If you delete the `theme` block, the plugin still selects Material, but you must keep `features` or the right-hand list comes back.

### Port already in use

Pass `--dev-addr 127.0.0.1:8001` to `mkdocs serve` when 8000 is taken.
