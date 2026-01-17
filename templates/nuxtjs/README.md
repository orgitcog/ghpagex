# NuxtJS GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a NuxtJS site to GitHub Pages.

## About NuxtJS

Nuxt is the intuitive Vue framework for building web applications. It provides a powerful and flexible foundation for creating server-side rendered, static, or single-page applications.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Nuxt configured
4. Make sure your Nuxt config is set for static site generation
5. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Nuxt dependencies
- Nuxt configuration file (`nuxt.config.js` or `nuxt.config.ts`)
- A `generate` script in your `package.json`

## Features

- Automatic package manager detection (npm or yarn)
- Build caching for faster deployments
- Node.js 20 support
- Automatic router.base injection

## Learn More

- [Nuxt Documentation](https://nuxt.com/docs)
- [Nuxt Static Site Generation](https://nuxt.com/docs/getting-started/deployment#static-hosting)
