# Eleventy (11ty) GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying an Eleventy site to GitHub Pages.

## About Eleventy

Eleventy (11ty) is a simpler static site generator. It's lightweight, flexible, and can pull data from various sources including APIs like Supabase at build time. Perfect for blogs and documentation sites.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have an Eleventy configuration file (`.eleventy.js` or `eleventy.config.js`)
4. Configure your output directory (default is `_site`)
5. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Eleventy dependencies (`@11ty/eleventy`)
- Eleventy configuration file (`.eleventy.js` or `eleventy.config.js`)
- Content files (Markdown, HTML, etc.)

## Features

- Automatic package manager detection (npm, yarn, or pnpm)
- Configurable output directory
- Node.js 20 support
- Can fetch data from Supabase at build time
- Perfect for content-driven sites

## Learn More

- [Eleventy Documentation](https://www.11ty.dev/docs/)
- [Eleventy Getting Started](https://www.11ty.dev/docs/getting-started/)
- [Eleventy Data Files](https://www.11ty.dev/docs/data/)
