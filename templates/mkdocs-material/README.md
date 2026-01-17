# MkDocs Material GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a MkDocs site with Material theme to GitHub Pages.

## About MkDocs Material

MkDocs is a fast, simple and downright gorgeous static site generator that's geared towards building project documentation. The Material theme provides a modern, responsive design. MkDocs is Python-based and renders Markdown "as-is", with excellent support for Python notebooks via `mkdocs-jupyter`.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `mkdocs.yml` configuration file
4. Push your changes to trigger the workflow

## Requirements

- A `mkdocs.yml` configuration file in your repository root
- `docs/` folder with your Markdown content
- Optional: `requirements.txt` for additional MkDocs plugins

## Features

- Material theme with modern design
- Built-in search functionality
- Support for Python notebooks via mkdocs-jupyter
- Navigation with automatic page discovery
- Code highlighting and formatting
- Mobile-responsive design

## OpenCog Use Cases

- Document Python scripts that query AtomSpace
- Display PLN traces alongside documentation
- Render Jupyter notebooks with interactive examples
- Create technical documentation for Python-based OpenCog components
- Build searchable knowledge bases from Markdown files

## Learn More

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Deploying MkDocs with GitHub Actions](https://squidfunk.github.io/mkdocs-material/publishing-your-site/)
