# ghpagex

GitHub Pages workflow examples and templates for various static site generators and frameworks.

## Available Templates

This repository contains ready-to-use GitHub Actions workflow templates for deploying static sites to GitHub Pages. Each template is in its own folder with documentation and a workflow file.

### 📚 [mdBook](templates/mdbook/)
Package and deploy a site using mdBook, a utility to create modern online books from Markdown files.

### 🌸 [Jekyll](templates/jekyll/)
Build and deploy a Jekyll site with custom Ruby setup and dependencies.

### ⚡ [Hugo](templates/hugo/)
Package and deploy a Hugo site with extended features and Dart Sass support.

### 🚀 [Astro](templates/astro/)
Deploy an Astro site with automatic package manager detection.

### 💚 [NuxtJS](templates/nuxtjs/)
Package and deploy a NuxtJS site with static site generation.

### ⚫ [Next.js](templates/nextjs/)
Package and deploy a Next.js site with static export configuration.

### 📄 [Static HTML](templates/static-html/)
Deploy static HTML files without any build process - the simplest option.

### 🌸 [Jekyll with GitHub Pages](templates/jekyll-gh-pages/)
Deploy a Jekyll site with GitHub Pages dependencies preinstalled.

### 🟣 [Gatsby](templates/gatsby/)
Package and deploy a Gatsby site with build caching and optimization.

## Usage

1. Browse to the template folder for your framework
2. Read the README in that folder for specific instructions
3. Copy the `deploy.yml` file to `.github/workflows/` in your repository
4. Update the branch name in the workflow file to match your default branch
5. Push to your repository to trigger the deployment

## Prerequisites

- A GitHub repository with your site's source code
- GitHub Pages enabled in your repository settings
- Appropriate configuration files for your chosen framework (e.g., `package.json`, `config.yml`, etc.)

## Contributing

Feel free to submit pull requests to improve these templates or add new ones!

## License

See [LICENSE](LICENSE) file for details.
