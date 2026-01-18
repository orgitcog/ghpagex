# Lume GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Lume site to GitHub Pages.

## About Lume

Lume is a static site generator for Deno, inspired by other static site generators like Jekyll or Eleventy. It's fast, flexible, and uses modern JavaScript/TypeScript with Deno's secure runtime.

## Deep Tree Echo Alignment

**Why Lume**: Native Deno support, modular architecture, and markdown compatibility make Lume a clean foundation for evolving systems.

**Deep Tree Echo fit**: Can be used for publishing membrane-layered documentation where components evolve separately yet stay in sync.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `_config.ts` or `_config.js` file with Lume configuration
4. Push your changes to trigger the workflow

## Requirements

- A Lume configuration file (`_config.ts`, `_config.js`, or `deno.json`)
- Markdown or template files in your source directory
- Deno runtime (automatically installed by the workflow)

## Features

- Latest Deno runtime
- No Node.js or npm required
- Fast build times with Deno's performance
- Native TypeScript support

## Learn More

- [Lume Documentation](https://lume.land/)
- [Lume GitHub Repository](https://github.com/lumeland/lume)
