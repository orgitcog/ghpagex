# Quartz GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Quartz site to GitHub Pages.

## About Quartz

Quartz is a fast, batteries-included static-site generator that transforms Obsidian vaults into beautiful, fully-functional websites. It features graph-based navigation that mirrors service dependency graphs, with backlinks representing service call relationships - excellent for emergent architectures.

**Service Role:** `knowledge.mesh`

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have Quartz configured in your repository
4. Add your content in Markdown format
5. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Quartz dependencies
- Quartz configuration file (`quartz.config.ts`)
- Content in Markdown format (Obsidian-compatible)

## Features

- Graph-based navigation mirroring service dependencies
- Backlinks for service relationship mapping
- Obsidian vault compatibility
- Beautiful, fast static sites
- Full-text search
- Dark mode support
- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 20 support
- Dependency caching for faster builds

## Service Sketch

```yaml
QuartzMesh:
  type: mesh
  nodes:
    - markdown.notes
  edges:
    - backlinks
```

## Learn More

- [Quartz Documentation](https://quartz.jzhao.xyz/)
- [Obsidian](https://obsidian.md/)
- [Quartz Features](https://quartz.jzhao.xyz/features/)
