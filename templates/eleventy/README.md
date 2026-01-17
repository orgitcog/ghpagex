# Eleventy (11ty) GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying an Eleventy site to GitHub Pages.

## About Eleventy

Eleventy is a simpler static site generator and an alternative to Jekyll. It's unopinionated and ideal for service graph assembly with data-driven builds from JSON/YAML/JS for declarative topology. Perfect for monorepos and multi-service outputs.

**Service Role:** `composition.worker`

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Eleventy configured
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Eleventy (`@11ty/eleventy`) as a dependency
- Eleventy configuration file (`.eleventy.js` or `eleventy.config.js`) - optional
- Template files (HTML, Markdown, Nunjucks, etc.)

## Features

- Unopinionated and flexible architecture
- Data-driven builds from JSON/YAML/JS
- Excellent for service graph composition
- Works well with monorepos
- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 20 support
- Dependency caching for faster builds

## Service Sketch

```yaml
EleventyPipeline:
  type: worker
  inputs:
    - service_graphs/*.json
    - templates/*
  transforms:
    - graph_to_pages
```

## Learn More

- [Eleventy Documentation](https://www.11ty.dev/docs/)
- [Eleventy Getting Started](https://www.11ty.dev/docs/getting-started/)
- [Eleventy Data Files](https://www.11ty.dev/docs/data/)
