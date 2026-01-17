# Docusaurus GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Docusaurus site to GitHub Pages.

## About Docusaurus

Docusaurus is a modern static website generator optimized for building documentation websites. It features native multi-versioning, sidebar navigation as service domain graphs, and MDX support for executable documentation primitives.

**Service Role:** `docs.orchestrator`

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Docusaurus configured
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Docusaurus dependencies
- Docusaurus configuration file (`docusaurus.config.js`)
- Documentation content in Markdown/MDX format

## Features

- Multi-version documentation support for service evolution timelines
- Sidebar navigation as bounded context graphs
- MDX compilation for interactive documentation
- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 20 support
- Dependency caching for faster builds

## Service Sketch

```yaml
DocusaurusSite:
  type: orchestrator
  workers:
    - docs.versioner
    - nav.graph.renderer
    - mdx.compiler
```

## Learn More

- [Docusaurus Documentation](https://docusaurus.io/docs)
- [Docusaurus Deployment Guide](https://docusaurus.io/docs/deployment)
