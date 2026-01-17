# Next.js GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Next.js site to GitHub Pages.

## About Next.js

Next.js is a React framework that gives you building blocks to create web applications. It provides a production-ready solution with great developer experience.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Configure Next.js for static export in your `next.config.js`:
   ```js
   module.exports = {
     output: 'export',
   }
   ```
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Next.js dependencies
- Next.js configuration file (`next.config.js` or `next.config.mjs`)
- Next.js configured for static export

## Features

- Automatic package manager detection (npm or yarn)
- Build caching for optimal performance
- Node.js 20 support
- Automatic basePath injection
- Disabled server-side image optimization for static export

## Learn More

- [Next.js Documentation](https://nextjs.org/docs)
- [Next.js Static Exports](https://nextjs.org/docs/app/building-your-application/deploying/static-exports)
