# Docusaurus GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Docusaurus v3 site to GitHub Pages.

## About Docusaurus

Docusaurus is a React-based documentation engine with MDX support that makes it easy to build, deploy, and maintain open source project websites. It's particularly well-suited for hosting Knowledge Cards, interactive diagrams (via React components), and embedding live demos alongside documentation.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `package.json` with Docusaurus configured
4. Push your changes to trigger the workflow

## Requirements

- A `package.json` file with Docusaurus dependencies
- Docusaurus configuration file (`docusaurus.config.js`)
- `docs/` folder with your Markdown/MDX content

## Features

- React + MDX for interactive documentation
- Built-in versioning and i18n support
- Automatic package manager detection (npm, yarn, or pnpm)
- Node.js 20 support
- Dependency caching for faster builds
- Optimized production builds

## OpenCog Use Cases

- Host Knowledge Cards with rich formatting
- Embed interactive AtomSpace diagrams using React components
- Display live MOSES demos alongside documentation
- Create searchable API documentation
- Build interactive tutorials with code playgrounds

## Learn More

- [Docusaurus Documentation](https://docusaurus.io/)
- [Docusaurus GitHub Pages Guide](https://docusaurus.io/docs/deployment#deploying-to-github-pages)
- [How to Set Up Documentation as Code with Docusaurus and GitHub Actions](https://www.freecodecamp.org/news/set-up-docs-as-code-with-docusaurus-and-github-actions/)
