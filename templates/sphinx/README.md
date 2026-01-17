# Sphinx GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Sphinx documentation site to GitHub Pages.

## About Sphinx

Sphinx is a powerful documentation generator that makes it easy to create intelligent and beautiful documentation. It excels at formal specifications, RFCs, and protocol definitions with support for MyST Markdown and reStructuredText for strict schemas.

**Service Role:** `specification.daemon`

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `requirements.txt` or `docs/requirements.txt` with Sphinx dependencies
4. Ensure you have a `conf.py` configuration file in your docs directory
5. Push your changes to trigger the workflow

## Requirements

- A `requirements.txt` file with Sphinx and required extensions
- Sphinx configuration file (`conf.py`)
- Documentation source files in reStructuredText or MyST Markdown

## Features

- Support for MyST Markdown and reStructuredText
- Excellent for API documentation and service contracts
- Extensible with numerous plugins and themes
- Python 3.11 support
- Dependency caching for faster builds

## Service Sketch

```yaml
SphinxBuild:
  type: daemon
  inputs:
    - specs/*
    - contracts/*
  outputs:
    - html
    - pdf
```

## Learn More

- [Sphinx Documentation](https://www.sphinx-doc.org/)
- [MyST Parser](https://myst-parser.readthedocs.io/)
- [Read the Docs Theme](https://sphinx-rtd-theme.readthedocs.io/)
