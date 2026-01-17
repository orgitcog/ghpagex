# Hugo GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Hugo site to GitHub Pages.

## About Hugo

Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure your Hugo configuration file (`config.toml`, `config.yaml`, or `config.json`) is set up
4. Push your changes to trigger the workflow

## Requirements

- A valid Hugo configuration file in your repository root
- Hugo content and theme files

## Features

- Uses Hugo Extended version 0.128.0
- Supports Dart Sass for advanced styling
- Handles git submodules for themes
- Minified output for optimal performance

## Learn More

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Hugo Quick Start](https://gohugo.io/getting-started/quick-start/)
