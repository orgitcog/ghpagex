# SvelteKit GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a SvelteKit site (in static mode) to GitHub Pages.

## About SvelteKit

Like Astro but even closer to the metal. It encourages building reactive systems with a single mutation ripple, much like tweaking one component in a networked ritual and watching the feedback wave propagate. Perfect for interactive dashboards or reactive control interfaces for Mardukian constructs. Static export works great for GitHub Pages.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with SvelteKit configured with the static adapter
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with SvelteKit (`@sveltejs/kit`) as a dependency
- SvelteKit configuration file (`svelte.config.js`) with `@sveltejs/adapter-static`
- Static adapter configured for GitHub Pages deployment

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Configurable build path
- Node.js 20 support
- Dependency caching for faster builds
- Supports static site generation

## Learn More

- [SvelteKit Documentation](https://kit.svelte.dev/)
- [SvelteKit Static Adapter](https://kit.svelte.dev/docs/adapter-static)
- [SvelteKit GitHub Pages Guide](https://kit.svelte.dev/docs/adapter-static#github-pages)
