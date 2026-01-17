# Pelican GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Pelican site to GitHub Pages.

## About Pelican

Pelican is an old but elegant Python-based static site generator, with plugin hooks and templating galore. Slightly dusty... but that's where the necromancy lies. Perfect for projects with backend data pipelines or when you want to use your experimental Python packages during build.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `pelicanconf.py` configuration file
4. Push your changes to trigger the workflow

## Requirements

- A `pelicanconf.py` configuration file in your repository root
- Content files (typically in a `content/` directory)
- Optional: `requirements.txt` for Python dependencies (themes, plugins, etc.)

## Features

- Python 3.x support
- Automatic installation of Pelican and dependencies
- Supports themes and plugins
- Dependency caching for faster builds

## Learn More

- [Pelican Documentation](https://docs.getpelican.com/)
- [Pelican Themes](https://github.com/getpelican/pelican-themes)
- [Pelican Plugins](https://github.com/pelican-plugins)
