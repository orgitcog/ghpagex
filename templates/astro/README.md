# Astro GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying an Astro site to GitHub Pages.

## About Astro

Astro is a modern static site builder that delivers lightning-fast performance with a powerful developer experience. Build content-rich websites with your favorite UI frameworks.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Astro configured
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Astro dependencies
- Astro configuration file (`astro.config.mjs`)

## Features

- Automatic package manager detection (npm or yarn)
- Configurable build path
- Node.js 20 support
- Dependency caching for faster builds

## Learn More

- [Astro Documentation](https://docs.astro.build/)
- [Astro GitHub Pages Guide](https://docs.astro.build/en/guides/deploy/github/)
