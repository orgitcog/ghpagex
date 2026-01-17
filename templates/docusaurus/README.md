# Docusaurus GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Docusaurus site to GitHub Pages.

## About Docusaurus

Docusaurus is Facebook's doc-centric React framework—excellent for highly interlinked documentation with versioning and multilingual support. Perfect for when your experiments require version-controlled documentation of branching timelines. Also supports plugins and search indexing.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Docusaurus configured
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Docusaurus (`@docusaurus/core`) as a dependency
- Docusaurus configuration file (`docusaurus.config.js`)

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 20 support
- Dependency caching for faster builds
- Supports versioning and i18n

## Learn More

- [Docusaurus Documentation](https://docusaurus.io/)
- [Docusaurus Deployment Guide](https://docusaurus.io/docs/deployment)
