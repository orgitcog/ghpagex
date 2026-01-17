# Jekyll with GitHub Pages Dependencies Template

This template provides a GitHub Actions workflow for building and deploying a Jekyll site to GitHub Pages with the GitHub Pages dependencies preinstalled.

## About Jekyll with GitHub Pages

This workflow uses the official GitHub Pages Jekyll action which comes with all the GitHub Pages dependencies pre-installed, making it easier to use Jekyll with GitHub Pages.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a Jekyll site structure with `_config.yml`
4. Push your changes to trigger the workflow

## Requirements

- Jekyll site structure with `_config.yml`
- No `Gemfile` required (GitHub Pages dependencies are preinstalled)

## Features

- Uses official `actions/jekyll-build-pages` action
- GitHub Pages dependencies preinstalled
- No need to manage Ruby or bundle dependencies manually
- Simplified setup compared to standard Jekyll workflow

## Difference from Standard Jekyll

This workflow is simpler and uses the `actions/jekyll-build-pages` action which includes all GitHub Pages dependencies. Use this if you want a GitHub Pages-compatible Jekyll setup without managing dependencies yourself.

## Learn More

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Jekyll Action](https://github.com/actions/jekyll-build-pages)
