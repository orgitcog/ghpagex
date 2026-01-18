# Quarto GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a Quarto site to GitHub Pages.

## About Quarto

Quarto is an open-source scientific and technical publishing system built on Pandoc. It supports Jupyter notebooks, R Markdown, and plain Markdown, making it perfect for creating reproducible, computational documents. Quarto can render notebooks into beautiful static websites with interactive elements.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `_quarto.yml` configuration file
4. Push your changes to trigger the workflow

## Requirements

- A `_quarto.yml` configuration file in your repository root
- Quarto documents (`.qmd`), Jupyter notebooks (`.ipynb`), or Markdown files
- Optional: `requirements.txt` for Python dependencies

## Features

- Native Jupyter notebook rendering
- Support for multiple languages (Python, R, Julia, Observable)
- Interactive widgets and visualizations
- Code execution during build
- LaTeX math support
- Cross-references and citations
- Customizable themes

## OpenCog Use Cases

- Create step-by-step PLN walkthroughs with executable code
- Display MOSES fitness plots and evolution traces
- Document pattern-mining experiments with reproducible results
- Build interactive tutorials where readers can download and rerun notebooks
- Visualize AtomSpace statistics and metrics
- Share computational research with embedded results

## Learn More

- [Quarto Documentation](https://quarto.org/)
- [Quarto GitHub Pages Guide](https://quarto.org/docs/publishing/github-pages.html)
- [Jupyter Book Documentation](https://jupyterbook.org/) (alternative tool with similar features)
