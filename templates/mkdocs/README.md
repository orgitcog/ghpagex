# MkDocs GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a MkDocs site to GitHub Pages.

## About MkDocs

MkDocs, especially with `mkdocs-material`, becomes a knowledge-engine worth housing eldritch blueprints. Think of it as the grimoire compiler for engineers. Glorious for layered documentation systems, nested wikis, modular diagrams. Perfect for storing evolving Marduk protocol layers.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `mkdocs.yml` configuration file
4. Push your changes to trigger the workflow

## Requirements

- A `mkdocs.yml` configuration file in your repository root
- Markdown documentation files (typically in a `docs/` directory)
- Optional: `requirements.txt` for Python dependencies (e.g., mkdocs-material theme)

## Features

- Python 3.x support
- Automatic installation of MkDocs and dependencies
- Supports Material theme and other plugins
- Dependency caching for faster builds

## Learn More

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
