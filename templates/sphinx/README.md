# Sphinx GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Sphinx documentation site to GitHub Pages.

## About Sphinx

Sphinx is a powerful documentation generator that makes it easy to create intelligent and beautiful documentation. It supports multiple output formats, automatic API documentation generation, and extensive customization. With Breathe and Doxygen integration, Sphinx can generate comprehensive API documentation from C++ source code.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `docs/conf.py` Sphinx configuration file
4. Push your changes to trigger the workflow

## Requirements

- Sphinx configuration file (`docs/conf.py` or `source/conf.py`)
- reStructuredText or Markdown source files
- Optional: `docs/requirements.txt` for Sphinx extensions and themes
- Optional: Doxygen configuration for C++ API documentation

## Features

- Automatic API documentation from docstrings
- Support for multiple markup formats (reStructuredText, Markdown)
- Breathe extension for C++ API documentation via Doxygen
- Extensive theming options (ReadTheDocs, Book, PyData, etc.)
- Cross-referencing and automatic index generation
- Math support via MathJax or KaTeX

## OpenCog Use Cases

- Generate API documentation from C++ headers
- Document custom AtomSpace Links and evaluators
- Create comprehensive developer guides
- Build searchable reference documentation
- Document low-level primitives alongside high-level concepts

## Learn More

- [Sphinx Documentation](https://www.sphinx-doc.org/)
- [Breathe Documentation](https://breathe.readthedocs.io/)
- [Doxygen Manual](https://www.doxygen.nl/manual/)
- [sphinx-notes/pages GitHub Action](https://github.com/marketplace/actions/sphinx-to-github-pages)
