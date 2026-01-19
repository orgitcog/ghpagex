# Redocly GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying API documentation using Redocly to GitHub Pages.

## About Redocly

Redocly is a professional tool for creating beautiful, interactive API documentation from OpenAPI specifications. It treats OpenAPI as the source-of-truth and is ideal for documenting service mesh exposure layers and API surfaces.

**Service Role:** `interface.contractor`

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have an OpenAPI specification file (e.g., `openapi.yaml` or `openapi.json`)
4. Optionally create a `redocly.yaml` configuration file
5. Push your changes to trigger the workflow

## Requirements

- An OpenAPI 3.x specification file (`openapi.yaml`, `openapi.json`, or similar)
- Optional: `redocly.yaml` configuration file for customization
- Optional: `package.json` if using npm-based setup

## Features

- First-class API/service surface documentation
- Interactive API documentation
- OpenAPI specification as source-of-truth
- Beautiful, responsive design
- Supports OpenAPI 3.x specifications
- Node.js 20 support

## Service Sketch

```yaml
APIDocs:
  type: contractor
  source:
    - openapi.yaml
  outputs:
    - interactive.docs
```

## Learn More

- [Redocly Documentation](https://redocly.com/docs/)
- [Redocly CLI](https://redocly.com/docs/cli/)
- [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
