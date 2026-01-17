# TiddlyWiki GitHub Pages Template

This template provides a GitHub Actions workflow for building and deploying a TiddlyWiki site to GitHub Pages.

## About TiddlyWiki

TiddlyWiki is a unique non-linear personal web notebook. It's a single HTML file that contains all the data, CSS, and JavaScript needed to run a complete wiki system. Each piece of information ("tiddler") can be individually edited, tagged, and linked.

## Deep Tree Echo Alignment

**Why TiddlyWiki**: A **personal, self-contained knowledge system** that can be hosted via GitHub Pages. Each "tiddler" can represent a node or reservoir.

**Deep Tree Echo fit**: Use it for persistent internal state modeling, personal memory encoding, or recursive rule visualizations.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a TiddlyWiki folder structure with `tiddlywiki.info` configuration
4. Push your changes to trigger the workflow

## Requirements

- A `tiddlywiki.info` file in your wiki folder with an `index` build target defined
- Tiddlers in the `tiddlers/` directory
- Node.js (automatically installed by the workflow)

**Note**: The workflow uses the `--build index` command. Ensure your `tiddlywiki.info` file has an `index` build target configured, or modify the workflow to use your custom build target. Example `tiddlywiki.info` with build target:

```json
{
  "description": "My Wiki",
  "plugins": [],
  "themes": [],
  "build": {
    "index": [
      "--rendertiddler", "$:/plugins/tiddlywiki/tiddlyweb/save/offline", "index.html", "text/plain"
    ]
  }
}
```

## Features

- Builds a static HTML version of your TiddlyWiki
- Node.js 20 support
- Single self-contained output file
- Full wiki functionality on GitHub Pages

## Learn More

- [TiddlyWiki Documentation](https://tiddlywiki.com/)
- [TiddlyWiki on Node.js](https://tiddlywiki.com/static/TiddlyWiki%2520on%2520Node.js.html)
