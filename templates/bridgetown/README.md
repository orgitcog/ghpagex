# Bridgetown - Modern Ruby Static Site Generator

Deploy static sites built with Bridgetown, a modern evolution of Jekyll with first-class support for modern JavaScript.

## Overview

Bridgetown is a Ruby-based static site generator that builds on Jekyll's foundation while embracing modern web development practices. It features Webpack integration, component-based architecture, and better developer experience.

## Features

- **Modern JavaScript**: First-class Webpack/esbuild support
- **Component Architecture**: Reusable components and partials
- **Ruby Plugins**: Extend with Ruby gems
- **Liquid & ERB Templates**: Multiple templating options
- **Resource-based Content**: Modern content modeling
- **Live Reload**: Fast development with hot module replacement
- **Internationalization**: Built-in i18n support

## Use Cases

- **Modern Documentation**: Technical docs with interactive components
- **Developer Portfolios**: Showcase projects with rich interactivity
- **SaaS Marketing Sites**: Product pages with modern UX
- **Content Platforms**: Blogs and publications with advanced features
- **Jekyll Migration**: Upgrade from Jekyll with modern tooling

## Prerequisites

- Ruby 3.0+ and Bundler
- Node.js 16+ (for frontend assets)
- Basic understanding of Ruby and JavaScript

## Quick Start

### 1. Install Bridgetown

```bash
gem install bridgetown -N
```

### 2. Create New Site

```bash
bridgetown new mysite
cd mysite
```

### 3. Start Development Server

```bash
bin/bridgetown start
```

### 4. Build for Production

```bash
bin/bridgetown build
```

## Deployment Workflow

```yaml
name: Deploy Bridgetown Site

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
      
      - name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: '3.2'
          bundler-cache: true
      
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      
      - name: Install Node dependencies
        run: npm ci
      
      - name: Build site
        run: bin/bridgetown build
        env:
          BRIDGETOWN_ENV: production
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: 'output'
  
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
├── src/
│   ├── _components/          # Reusable components
│   │   ├── navbar.liquid
│   │   └── footer.erb
│   ├── _layouts/             # Layout templates
│   │   ├── default.erb
│   │   └── post.liquid
│   ├── _data/                # Data files (YAML, JSON)
│   │   └── site.yml
│   ├── _posts/               # Blog posts
│   │   └── 2024-01-19-welcome.md
│   ├── _resources/           # Collections
│   ├── images/               # Images
│   └── index.md              # Homepage
├── frontend/
│   ├── javascript/           # JavaScript files
│   │   └── index.js
│   └── styles/               # CSS/SCSS
│       └── index.scss
├── plugins/                  # Custom Ruby plugins
├── bridgetown.config.yml     # Configuration
├── Gemfile
├── package.json
└── output/                   # Built site (git ignored)
```

## Configuration

### bridgetown.config.yml

```yaml
url: "https://yourusername.github.io"
title: "My Bridgetown Site"
description: "A modern static site"

permalink: pretty

collections:
  projects:
    output: true
    permalink: /projects/:title/

pagination:
  enabled: true
  per_page: 10

esbuild:
  format: esm
  minify: true
```

## Content Types

### Blog Post

```markdown
---
layout: post
title: "Welcome to Bridgetown"
date: 2024-01-19
categories: [web, ruby]
---

# Hello World

This is my first Bridgetown post!
```

### Resource Model

```ruby
# src/_projects/cool-project.md
---
layout: project
title: Cool Project
tech_stack: [Ruby, JavaScript, React]
---

Project description here.
```

## Templates

### Liquid Template

```liquid
<!-- src/_layouts/default.liquid -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>{{ page.title }} | {{ site.title }}</title>
  {% webpack_path css %}
</head>
<body>
  {% render "navbar" %}
  
  <main>
    {{ content }}
  </main>
  
  {% render "footer" %}
  
  {% webpack_path js %}
</body>
</html>
```

### ERB Template

```erb
<%# src/_layouts/post.erb %>
<article class="post">
  <header>
    <h1><%= resource.data.title %></h1>
    <time datetime="<%= resource.data.date %>">
      <%= resource.data.date.strftime("%B %d, %Y") %>
    </time>
  </header>
  
  <%= yield %>
  
  <footer>
    <%= render "social_share", title: resource.data.title %>
  </footer>
</article>
```

## Components

### Reusable Component

```liquid
<!-- src/_components/card.liquid -->
<div class="card">
  <h3>{{ title }}</h3>
  <p>{{ description }}</p>
  {% if link %}
    <a href="{{ link }}">Learn more</a>
  {% endif %}
</div>
```

Usage:
```liquid
{% render "card", 
   title: "My Card",
   description: "Card description",
   link: "/page" %}
```

## Frontend Integration

### JavaScript (ESM)

```javascript
// frontend/javascript/index.js
import Alpine from 'alpinejs'

// Initialize Alpine.js
window.Alpine = Alpine
Alpine.start()

// Custom JavaScript
console.log('Bridgetown is ready!')
```

### CSS/SCSS

```scss
// frontend/styles/index.scss
@import "variables";
@import "components/navbar";
@import "components/footer";

body {
  font-family: $font-stack;
  line-height: 1.6;
}
```

## Ruby Plugins

### Custom Builder

```ruby
# plugins/builders/custom_builder.rb
class CustomBuilder < SiteBuilder
  def build
    hook :site, :post_read do
      site.posts.docs.each do |post|
        post.data.reading_time = calculate_reading_time(post.content)
      end
    end
  end
  
  def calculate_reading_time(content)
    words = content.split.size
    (words / 200.0).ceil # Assuming 200 words per minute
  end
end
```

### Custom Tag

```ruby
# plugins/tags/custom_tag.rb
class CustomTag < Liquid::Tag
  def render(context)
    "<div class='custom'>Custom content</div>"
  end
end

Liquid::Template.register_tag "custom", CustomTag
```

## Advanced Features

### Internationalization

```yaml
# bridgetown.config.yml
available_locales: [:en, :es, :fr]
default_locale: :en
```

```liquid
<!-- Use translations -->
<h1>{% t site.welcome_message %}</h1>
```

### Pagination

```ruby
---
layout: default
title: Blog
paginate:
  collection: posts
---

<% paginator.resources.each do |post| %>
  <article>
    <h2><%= post.data.title %></h2>
  </article>
<% end %>

<%= paginator.previous_page_link %>
<%= paginator.next_page_link %>
```

### Taxonomies

```ruby
# Get all posts with a specific category
<% collections.posts.resources.select do |post|
  post.data.categories&.include?("ruby")
end.each do |post| %>
  <%= post.data.title %>
<% end %>
```

## Migration from Jekyll

Bridgetown maintains Jekyll compatibility:

1. **Most Jekyll Sites Work**: Liquid templates, frontmatter
2. **New Features**: Optionally adopt modern features
3. **Gradual Migration**: Mix Jekyll patterns with Bridgetown features
4. **Plugin Ecosystem**: Many Jekyll plugins work

### Key Changes

- Output directory: `_site` → `output`
- Configuration: `_config.yml` → `bridgetown.config.yml`
- Resources replace Documents/Pages
- Webpack/esbuild for assets
- Ruby 3.0+ required

## Performance

- **Build Speed**: Fast incremental builds
- **Hot Reload**: Sub-second updates during development
- **Asset Pipeline**: Modern bundling with esbuild/Webpack
- **Caching**: Smart caching for faster rebuilds

## Resources

- [Bridgetown Documentation](https://www.bridgetownrb.com/docs/)
- [Bridgetown GitHub](https://github.com/bridgetownrb/bridgetown)
- [Plugin Directory](https://www.bridgetownrb.com/plugins/)
- [Community Forum](https://community.bridgetown.pub/)

## Limitations

- Requires both Ruby and Node.js
- Smaller ecosystem than Jekyll
- More complex than simple SSGs
- Ruby knowledge beneficial

## Tips

1. **Use Components**: Build reusable component library
2. **Modern JS**: Leverage ESM and modern frameworks
3. **ERB for Logic**: Use ERB when you need Ruby power
4. **Plugins**: Create custom plugins for repeated tasks
5. **Resource Models**: Take advantage of structured content
6. **Hot Reload**: Keep dev server running for fast feedback

## Best Practices

- Organize components by feature
- Use data files for configuration
- Keep layouts simple and composable
- Leverage Ruby for complex logic
- Use esbuild for faster builds
- Test in production mode before deploying
- Version control `Gemfile.lock` and `package-lock.json`

## Comparison

| Feature | Bridgetown | Jekyll | Hugo |
|---------|-----------|--------|------|
| Language | Ruby | Ruby | Go |
| Modern JS | ✅ Built-in | ❌ Manual | ❌ Manual |
| Speed | Fast | Slower | Very Fast |
| Learning Curve | Medium | Low | Medium |
| Plugins | Ruby gems | Ruby gems | Go modules |
| Templates | Liquid/ERB | Liquid | Go templates |
