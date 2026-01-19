# VitePress GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a VitePress documentation site to GitHub Pages.

## About VitePress

VitePress is a Vite-powered static site generator designed for building fast, content-focused websites. It's perfect for documentation sites and works well with Vue ecosystem and Supabase API integration.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a VitePress configuration file (`.vitepress/config.js` or `.vitepress/config.ts`)
4. Configure the base URL if deploying to a subpath
5. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with VitePress dependencies
- VitePress configuration in `.vitepress/config.js` or `.vitepress/config.ts`
- Documentation content in Markdown files

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Extremely fast builds with Vite
- Node.js 20 support
- Native Vue ecosystem support
- Optimized for documentation with Supabase backend

## Learn More

- [VitePress Documentation](https://vitepress.dev/)
- [VitePress Getting Started](https://vitepress.dev/guide/getting-started)
- [VitePress Deployment](https://vitepress.dev/guide/deploy#github-pages)
