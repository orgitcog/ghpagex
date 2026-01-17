# mdBook GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a mdBook site to GitHub Pages.

## About mdBook

mdBook is a utility to create modern online books from Markdown files. It's ideal for creating documentation, tutorials, and technical books.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure your mdBook configuration is set up in your repository
4. Push your changes to trigger the workflow

## Requirements

- A valid `book.toml` configuration file in your repository root
- Markdown source files for your book

## Learn More

- [mdBook Documentation](https://rust-lang.github.io/mdBook/index.html)
- [GitHub Pages Documentation](https://docs.github.com/pages)
