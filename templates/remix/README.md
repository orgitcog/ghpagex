# Remix GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Remix app to GitHub Pages.

## About Remix

Remix is a full stack web framework that lets you focus on the user interface and work back through web standards to deliver a fast, slick, and resilient user experience. It supports both SSR and static generation.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Configure Remix for static export by using a suitable adapter (e.g., `@remix-run/cloudflare-pages` or static export configuration)
4. Ensure your `remix.config.js` is properly configured for GitHub Pages deployment
5. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Remix dependencies
- Remix configuration file (`remix.config.js` or `vite.config.ts`)
- Proper adapter configuration for static deployment

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Build caching for optimal performance
- Node.js 20 support
- SSR and API integration support
- Optimized for Supabase integration

## Learn More

- [Remix Documentation](https://remix.run/docs)
- [Remix Deployment Guide](https://remix.run/docs/en/main/guides/deployment)
- [Remix with GitHub Pages](https://remix.run/docs/en/main/guides/deployment#github-pages)
