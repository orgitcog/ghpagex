# Eleventy (11ty) GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying an Eleventy (11ty) site to GitHub Pages.

## About Eleventy

Eleventy is a simpler static site generator that doesn't impose a framework. It's incredibly flexible and works with multiple template languages (Markdown, Liquid, Nunjucks, etc.). Eleventy is perfect when you want a minimal workflow that transforms Markdown into HTML while allowing custom JavaScript for interactive features.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Eleventy configured
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with `@11ty/eleventy` dependency
- Optional: `.eleventy.js` configuration file
- Content files in supported formats (Markdown, HTML, Liquid, Nunjucks, etc.)

## Features

- Zero-config by default
- Support for multiple template languages
- Fast build times
- No client-side JavaScript required (but optional)
- Powerful data cascade system
- Flexible project structure
- Plugin ecosystem for extended functionality

## OpenCog Use Cases

- Transform Knowledge Cards directory into searchable HTML
- Add interactive AtomSpace graph renderers with vanilla JavaScript
- Create lightweight documentation sites
- Build custom visualization dashboards
- Generate static sites from AtomSpace exports
- Implement custom data pipelines for documentation

## Learn More

- [Eleventy Documentation](https://www.11ty.dev/)
- [Eleventy Quick Tips](https://www.11ty.dev/docs/quicktips/)
- [Deploy Eleventy to GitHub Pages with GitHub Actions](https://www.rockyourcode.com/how-to-deploy-eleventy-to-github-pages-with-github-actions/)
