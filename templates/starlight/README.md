# Starlight GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Starlight site to GitHub Pages.

## About Starlight

Starlight is tailored for documentation, but built on Astro's architecture—thus letting you inject complexity gently, like dripping mercury into clockwork. A bit more focused than vanilla Astro, but ideal for modular knowledge graph deployments or pattern-based configuration guides.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Starlight configured
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Starlight (`@astrojs/starlight`) as a dependency
- Astro configuration file (`astro.config.mjs`) with Starlight integration

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Configurable build path
- Node.js 20 support
- Dependency caching for faster builds
- Built on Astro's architecture

## Learn More

- [Starlight Documentation](https://starlight.astro.build/)
- [Astro Documentation](https://docs.astro.build/)
