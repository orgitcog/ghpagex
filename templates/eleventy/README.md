# Eleventy (11ty) GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying an Eleventy site to GitHub Pages.

## About Eleventy

Eleventy is a simpler static site generator. It's extremely flexible, supporting multiple template languages (Markdown, Liquid, Nunjucks, Handlebars, Mustache, EJS, Haml, Pug, and JavaScript), and can be shaped to fit any project structure.

## Deep Tree Echo Alignment

**Why Eleventy**: Extremely flexible static site generator that supports multiple input formats and can be shaped into a **hypergraph-friendly renderer**. Lightweight and modular—perfect for mirroring Deep Tree Echo's distributed membrane logic.

**Deep Tree Echo fit**: Suitable for rendering **temporal node chains**, memory partitions, or thematic threads over time.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Eleventy configured
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Eleventy dependencies
- Eleventy configuration file (`.eleventy.js` or `eleventy.config.js`) - optional but recommended
- Content files in your source directory

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 20 support
- Dependency caching for faster builds
- Configurable output directory

## Learn More

- [Eleventy Documentation](https://www.11ty.dev/docs/)
- [Eleventy Get Started](https://www.11ty.dev/docs/getting-started/)
