# Gridsome GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Gridsome site to GitHub Pages.

## About Gridsome

Gridsome is a Vue.js-powered static site generator that makes it easy to build fast websites. It's built for the JAMstack workflow with a powerful data layer that collects content from local files, APIs, CMSs, and databases.

## Deep Tree Echo Alignment

**Why Gridsome**: Powerful for graph-based content sourcing (e.g., Markdown, CMS, APIs), and supports dynamic routing, caching, and performance.

**Deep Tree Echo fit**: Ideal for **deploying thematic node systems**, progressive graphs, and knowledge trail visualization.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Gridsome configured
4. Update `gridsome.config.js` with the correct `pathPrefix` for your repository
5. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Gridsome dependencies
- Gridsome configuration file (`gridsome.config.js`)
- Content sources configured in your Gridsome project

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 18 support (Gridsome compatibility)
- Dependency caching for faster builds
- GraphQL data layer support

## Learn More

- [Gridsome Documentation](https://gridsome.org/docs/)
- [Gridsome Deploy Guide](https://gridsome.org/docs/deployment/)
