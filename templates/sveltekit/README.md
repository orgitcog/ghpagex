# SvelteKit GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a SvelteKit app to GitHub Pages.

## About SvelteKit

SvelteKit is a framework for building web applications of all sizes, with a beautiful development experience and flexible filesystem-based routing. It's lightweight, fast, and works well with APIs like Supabase.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Configure SvelteKit for static site generation in your `svelte.config.js`:
   ```js
   import adapter from '@sveltejs/adapter-static';
   
   export default {
     kit: {
       adapter: adapter({
         pages: 'build',
         assets: 'build',
         fallback: undefined
       })
     }
   };
   ```
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with SvelteKit dependencies
- SvelteKit configuration file (`svelte.config.js`)
- `@sveltejs/adapter-static` installed for static site generation

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Build caching for faster deployments
- Node.js 20 support
- Optimized for static site generation and SSR
- Compatible with Supabase integration

## Learn More

- [SvelteKit Documentation](https://kit.svelte.dev/)
- [SvelteKit Static Adapter](https://kit.svelte.dev/docs/adapter-static)
- [SvelteKit GitHub Pages Deployment](https://kit.svelte.dev/docs/adapter-static#github-pages)
