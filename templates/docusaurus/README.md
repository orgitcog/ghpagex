# Docusaurus GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Docusaurus site to GitHub Pages.

## About Docusaurus

Docusaurus is a modern static website generator designed for building documentation websites. It's built with React and provides a rich plugin ecosystem, versioning, i18n support, and an excellent developer experience.

## Deep Tree Echo Alignment

**Why Docusaurus**: Great for knowledge graphs, interactive documentation, and persistent memory systems. Works well for presenting **dynamic nodes and cognitive schemas** as evolving documentation or idea spaces.

**Deep Tree Echo fit**: Ideal for projecting knowledge structures, memory beacons, and ESN schema walkthroughs.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Docusaurus configured
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Docusaurus dependencies
- Docusaurus configuration file (`docusaurus.config.js`)
- Content in the `docs/` and/or `blog/` directories

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 20 support
- Dependency caching for faster builds
- Built-in support for Docusaurus build output

## Learn More

- [Docusaurus Documentation](https://docusaurus.io/docs)
- [Docusaurus GitHub Pages Guide](https://docusaurus.io/docs/deployment#deploying-to-github-pages)
