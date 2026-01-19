# MkDocs GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a MkDocs site with Material theme to GitHub Pages.

## About MkDocs

MkDocs is a fast, simple static site generator that's geared towards building project documentation. With the Material theme, it excels at creating hierarchical system maps and control plane UIs with an outstanding plugin ecosystem.

**Service Role:** `control-plane.ui`

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `mkdocs.yml` configuration file
4. Ensure you have a `requirements.txt` or the workflow will install MkDocs with Material theme
5. Push your changes to trigger the workflow

## Requirements

- An `mkdocs.yml` configuration file
- Documentation content in Markdown format
- Optional: `requirements.txt` with MkDocs and plugin dependencies

## Features

- Material theme for beautiful, hierarchical documentation
- Extremely fast and predictable builds
- Strong plugin ecosystem (diagrams, search, versioning)
- Python 3.11 support
- Dependency caching for faster builds

## Service Sketch

```yaml
MkDocsSite:
  type: supervisor
  plugins:
    - diagrams
    - search.indexer
    - version.aliaser
```

## Learn More

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [MkDocs Plugins](https://github.com/mkdocs/mkdocs/wiki/MkDocs-Plugins)
