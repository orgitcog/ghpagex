# Vite App GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a custom Vite-based app to GitHub Pages.

## About Vite

Vite is a modern build tool that provides a fast development experience with instant server start and lightning-fast HMR. It's perfect for building apps with direct Supabase API integration.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `vite.config.js` or `vite.config.ts` file
4. Configure the base path in your Vite config for GitHub Pages if needed
5. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Vite dependencies
- Vite configuration file (`vite.config.js` or `vite.config.ts`)
- Application source files

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Fast builds with Vite's optimized bundling
- Node.js 20 support
- Great for small to mid-sized apps
- Direct Supabase API integration support

## Learn More

- [Vite Documentation](https://vitejs.dev/)
- [Vite Getting Started](https://vitejs.dev/guide/)
- [Vite Static Deployment](https://vitejs.dev/guide/static-deploy.html#github-pages)
