# Cobalt - Rust Static Site Generator

Deploy static sites built with Cobalt, a fast and simple Rust-based static site generator.

## Overview

Cobalt is a static site generator written in Rust, inspired by Jekyll but designed for simplicity and speed. It offers similar functionality to Jekyll with better performance and modern conventions.

## Features

- **Fast Builds**: Compiled Rust binary provides excellent performance
- **Liquid Templates**: Familiar template syntax (compatible with Jekyll)
- **Markdown Content**: Write in Markdown with frontmatter
- **Sass Support**: Built-in SASS/SCSS compilation
- **Live Reload**: Development server with automatic rebuilding
- **Zero Dependencies**: Single binary, no Ruby/Node.js required

## Use Cases

- **Personal Blogs**: Simple, fast blogging platform
- **Documentation Sites**: Technical documentation with search
- **Project Websites**: Open source project landing pages
- **Portfolios**: Developer portfolios with project showcases
- **Migration from Jekyll**: Easy transition with minimal changes

## Prerequisites

- Cobalt installed (`cargo install cobalt-bin`)
- Markdown content files
- Liquid template files

## Quick Start

### 1. Install Cobalt

```bash
cargo install cobalt-bin
```

### 2. Create New Site

```bash
cobalt new mysite
cd mysite
```

### 3. Build

```bash
cobalt build
```

### 4. Deploy

Use the provided GitHub Actions workflow.

## Deployment Workflow

```yaml
name: Deploy Cobalt Site

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Rust
        uses: dtolnay/rust-toolchain@stable
      
      - name: Install Cobalt
        run: cargo install cobalt-bin
      
      - name: Build site
        run: cobalt build
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '_site'
  
  deploy:
    needs: build
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## Project Structure

```
your-site/
├── _cobalt.yml               # Configuration file
├── _layouts/                 # Layout templates
│   ├── default.liquid
│   └── post.liquid
├── _includes/                # Reusable components
│   ├── header.liquid
│   └── footer.liquid
├── _sass/                    # SASS/SCSS files
│   └── main.scss
├── posts/                    # Blog posts
│   ├── 2024-01-01-first.md
│   └── 2024-01-15-second.md
├── assets/                   # Static assets
│   ├── css/
│   ├── images/
│   └── js/
├── index.liquid              # Homepage
└── _site/                    # Generated output (git ignored)
```

## Configuration

### _cobalt.yml

```yaml
site:
  title: My Cobalt Site
  description: A fast static site built with Cobalt
  base_url: https://yourusername.github.io

posts:
  dir: posts
  drafts_dir: _drafts

pages:
  dir: .

ignore:
  - _site
  - .git

syntaxhighlight:
  theme: base16-ocean-dark
```

## Content Format

### Blog Post Example

```markdown
---
title: My First Post
layout: post
published_date: 2024-01-19 10:00:00 +0000
excerpt: A brief introduction to my blog
tags:
  - rust
  - cobalt
  - static-sites
---

# Welcome!

This is my first post using Cobalt.

## Features I Love

- Fast compilation
- Simple configuration
- Liquid templates
```

### Page Example

```markdown
---
layout: default
title: About
permalink: /about/
---

## About Me

Information about the site and author.
```

## Templates

### Layout Template (default.liquid)

```liquid
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ page.title }} - {{ site.title }}</title>
    <link rel="stylesheet" href="/assets/css/main.css">
</head>
<body>
    {% include header.liquid %}
    
    <main>
        {{ page.content }}
    </main>
    
    {% include footer.liquid %}
</body>
</html>
```

### Post Layout (post.liquid)

```liquid
---
layout: default
---

<article class="post">
    <header>
        <h1>{{ page.title }}</h1>
        <time datetime="{{ page.published_date | date: "%Y-%m-%d" }}">
            {{ page.published_date | date: "%B %d, %Y" }}
        </time>
    </header>
    
    {{ page.content }}
    
    <footer>
        {% if page.tags %}
        <div class="tags">
            {% for tag in page.tags %}
            <span class="tag">{{ tag }}</span>
            {% endfor %}
        </div>
        {% endif %}
    </footer>
</article>
```

## Liquid Filters

Cobalt supports standard Liquid filters:

```liquid
{{ "hello" | capitalize }}
{{ page.published_date | date: "%Y-%m-%d" }}
{{ page.content | size }}
{{ page.excerpt | strip_html }}
```

## Development

### Local Server

```bash
cobalt serve
```

This starts a development server with live reload at `http://localhost:3000`.

### Watch Mode

```bash
cobalt watch
```

### Build for Production

```bash
cobalt build --release
```

## Migration from Jekyll

Cobalt is largely compatible with Jekyll:

1. Rename `_config.yml` to `_cobalt.yml`
2. Update configuration syntax (minor differences)
3. Most Liquid templates work as-is
4. Frontmatter is compatible
5. Folder structure is similar

### Key Differences

| Feature | Jekyll | Cobalt |
|---------|--------|--------|
| Config | `_config.yml` | `_cobalt.yml` |
| Posts dir | `_posts` | `posts` (configurable) |
| Plugins | Ruby gems | Built-in only |
| Speed | Slower | Much faster |
| Dependencies | Ruby + gems | Single binary |

## Plugins & Extensions

Cobalt has built-in features instead of plugins:

- **Syntax Highlighting**: Built-in (Syntect)
- **Sass Compilation**: Built-in
- **RSS/Atom Feeds**: Configure in `_cobalt.yml`
- **Pagination**: Built-in support
- **Drafts**: Supported natively

## Themes

Create custom themes with layouts and includes:

```
_layouts/
├── default.liquid
├── post.liquid
└── page.liquid

_includes/
├── header.liquid
├── footer.liquid
└── sidebar.liquid

_sass/
└── main.scss
```

## Advanced Configuration

### Custom Collections

```yaml
collections:
  projects:
    title: Projects
    dir: _projects
    order: Desc
```

### Pagination

```yaml
posts:
  paginate: 10
```

### Custom Permalinks

```yaml
posts:
  permalink: /blog/:year/:month/:day/:name/
```

## Performance

- **Build Speed**: Typically 10-100x faster than Jekyll
- **Binary Size**: ~10MB standalone executable
- **Memory Usage**: Minimal (< 100MB for most sites)
- **Incremental Builds**: Fast rebuilds during development

## Resources

- [Cobalt Documentation](https://cobalt-org.github.io/)
- [Cobalt GitHub](https://github.com/cobalt-org/cobalt.rs)
- [Liquid Template Reference](https://shopify.github.io/liquid/)
- [Example Sites](https://github.com/cobalt-org/cobalt.rs/wiki/Sites-using-Cobalt)

## Limitations

- Fewer plugins than Jekyll
- Smaller community
- Less mature ecosystem
- Limited third-party themes

## Tips

1. **Use Live Reload**: `cobalt serve` for rapid development
2. **Organize Content**: Use clear directory structure
3. **Leverage Includes**: DRY principle with reusable components
4. **Sass Features**: Take advantage of built-in SASS compilation
5. **Fast Builds**: Benefit from Rust's performance
6. **Git Ignore**: Add `_site/` to `.gitignore`

## Best Practices

- Keep layouts simple and modular
- Use includes for repeated elements
- Organize posts by date in frontmatter
- Add excerpts to posts for listing pages
- Use descriptive filenames
- Test locally before deploying
- Version control your source, not `_site/`

## Comparison with Other SSGs

| Feature | Cobalt | Jekyll | Hugo | Zola |
|---------|--------|--------|------|------|
| Language | Rust | Ruby | Go | Rust |
| Speed | Very Fast | Slow | Very Fast | Very Fast |
| Templates | Liquid | Liquid | Go | Tera |
| Learning Curve | Low | Low | Medium | Low |
| Ecosystem | Small | Large | Large | Small |
