# Jekyll GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Jekyll site to GitHub Pages with custom Ruby setup.

## About Jekyll

Jekyll is a simple, blog-aware, static site generator. It takes text written in your favorite markup language and uses layouts to create a static website.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `Gemfile` with your Jekyll dependencies
4. Push your changes to trigger the workflow

## Requirements

- A `Gemfile` with Jekyll and required dependencies
- Jekyll site structure with `_config.yml`
- Optional: `.ruby-version` file to specify Ruby version

## Learn More

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Jekyll on GitHub Pages](https://jekyllrb.com/docs/github-pages/)
