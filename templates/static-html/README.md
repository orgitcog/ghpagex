# Static HTML GitHub Pages Template

This template provides a GitHub Actions workflow for deploying static HTML files to GitHub Pages without any build process.

## About Static HTML

This is the simplest way to deploy a website to GitHub Pages. It deploys your HTML, CSS, JavaScript, and other static files directly without any build step.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Add your static HTML files to your repository
4. Push your changes to trigger the workflow

## Requirements

- HTML files in your repository
- Optional: CSS, JavaScript, images, and other static assets

## Features

- No build step required
- Deploys entire repository content
- Fastest deployment option
- Perfect for simple websites

## Learn More

- [GitHub Pages Documentation](https://docs.github.com/pages)
- [HTML Basics](https://developer.mozilla.org/en-US/docs/Learn/HTML)
