# Quartz GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Quartz site to GitHub Pages.

## About Quartz

Quartz is a fast, batteries-included static site generator that transforms your Markdown notes into a published website. It's specifically designed for publishing Obsidian vaults and Zettelkasten-style note collections with bidirectional linking, graph views, and full-text search.

## Deep Tree Echo Alignment

**Why Quartz**: Great for **publishing Zettelkasten-style notes** and dynamic thought graphs. Quartz can mirror how Deep Tree Echo forms and revisits mental nodes across distributed cognition.

**Deep Tree Echo fit**: Ideal for projecting evolving thought-chains, internal monologues, or "gestalt-building" processes with backlink support.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `quartz.config.ts` and your Markdown notes in the `content/` directory
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Quartz dependencies
- Quartz configuration file (`quartz.config.ts`)
- Markdown content in the `content/` directory

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 20 support
- Dependency caching for faster builds
- Full support for bidirectional links and graph visualization

## Learn More

- [Quartz Documentation](https://quartz.jzhao.xyz/)
- [Quartz GitHub Repository](https://github.com/jackyzha0/quartz)
