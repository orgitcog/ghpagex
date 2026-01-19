# SvelteKit GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a SvelteKit site to GitHub Pages.

## About SvelteKit

SvelteKit is a framework for building web applications with Svelte. It features server-side rendering, routing, and code-splitting out of the box. For static deployment, it uses the static adapter to prerender your entire site.

## Deep Tree Echo Alignment

**Why SvelteKit**: SvelteKit allows reactive, lightweight deployments and can easily integrate libraries like `cytoscape.js`, `d3.js`, or `hypergraph.js` for **live hypergraph visualizations**.

**Deep Tree Echo fit**: Perfect for **rendering real-time membrane partitions**, ESN feedback loops, or memory propagation in a visual form.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have `@sveltejs/adapter-static` installed and configured in `svelte.config.js`
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with SvelteKit and `@sveltejs/adapter-static` dependencies
- SvelteKit configuration file (`svelte.config.js`) with static adapter
- Your SvelteKit application source code

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 20 support
- Dependency caching for faster builds
- Supports static adapter for GitHub Pages deployment

## Learn More

- [SvelteKit Documentation](https://kit.svelte.dev/docs)
- [SvelteKit Static Adapter](https://kit.svelte.dev/docs/adapter-static)
- [SvelteKit GitHub Pages Guide](https://kit.svelte.dev/docs/adapter-static#github-pages)
