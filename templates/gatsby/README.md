# Gatsby GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Gatsby site to GitHub Pages.

## About Gatsby

Gatsby is a React-based open source framework for creating websites and apps. It provides a powerful toolkit for building blazing-fast websites with modern web technologies.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Gatsby configured
4. Make sure you have a `build` script in your `package.json`
5. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Gatsby dependencies
- Gatsby configuration file (`gatsby-config.js`)
- A `build` script in your `package.json`

## Features

- Automatic package manager detection (npm or yarn)
- Build caching for faster deployments
- Node.js 20 support
- Automatic pathPrefix injection
- Prefix paths enabled for proper GitHub Pages deployment

## Learn More

- [Gatsby Documentation](https://www.gatsbyjs.com/docs/)
- [Gatsby Quick Start](https://www.gatsbyjs.com/docs/quick-start/)
- [Gatsby GitHub Pages Deployment](https://www.gatsbyjs.com/docs/how-to/previews-deploys-hosting/how-gatsby-works-with-github-pages/)
