# Zola GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Zola site to GitHub Pages.

## About Zola

A lightning-fast static site generator in Rust. Why Zola? Because we like our systems to compile like spells—instantaneous and unflinching. Rust enforces discipline in madness. High-speed, content-driven, Markdown-powered. Excellent for building manifestos of recursive experimentation.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `config.toml` configuration file
4. Push your changes to trigger the workflow

## Requirements

- A `config.toml` configuration file in your repository root
- Content files (typically in a `content/` directory)
- Optional: A theme (in the `themes/` directory)

## Features

- Uses Zola 0.19.1
- Lightning-fast build times
- No dependencies to install
- Supports themes and templates
- Markdown-based content

## Learn More

- [Zola Documentation](https://www.getzola.org/documentation/)
- [Zola GitHub Pages Guide](https://www.getzola.org/documentation/deployment/github-pages/)
