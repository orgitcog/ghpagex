# ghpagex

GitHub Pages workflow examples and templates for various static site generators and frameworks.

## Available Templates

This repository contains ready-to-use GitHub Actions workflow templates for deploying static sites to GitHub Pages. Each template is in its own folder with documentation and a workflow file.

### 🧠 Knowledge + Cognition Systems

Ideal for knowledge graphs, documentation, and persistent memory systems.

#### 🧠 [Docusaurus](templates/docusaurus/)
Great for knowledge graphs, interactive documentation, and persistent memory systems. Perfect for presenting dynamic nodes and cognitive schemas as evolving documentation.

#### 🔮 [Quartz](templates/quartz/)
Publishing Zettelkasten-style notes and dynamic thought graphs. Ideal for projecting evolving thought-chains with backlink support.

#### 📘 [TiddlyWiki](templates/tiddlywiki/)
A personal, self-contained knowledge system. Each "tiddler" can represent a node or reservoir for persistent internal state modeling.

#### 📚 [mdBook](templates/mdbook/)
Package and deploy a site using mdBook, a utility to create modern online books from Markdown files.

### 🌐 Graph & Hypergraph-Friendly

Perfect for rendering complex relationships, temporal chains, and graph-based content.

#### 🪞 [SvelteKit](templates/sveltekit/)
Reactive, lightweight deployments with easy integration for graph visualization libraries (cytoscape.js, d3.js, hypergraph.js).

#### 🌌 [Eleventy (11ty)](templates/eleventy/)
Extremely flexible static site generator supporting multiple input formats. Perfect for hypergraph-friendly rendering and distributed membrane logic.

#### ⚙️ [Gridsome](templates/gridsome/)
Vue-based JAMstack with powerful graph-based content sourcing. Ideal for deploying thematic node systems and knowledge trail visualization.

### 🚀 Modern Frameworks


### 🚀 Modern Frameworks

Popular modern static site generators and frameworks.

#### 🚀 [Astro](templates/astro/)
Deploy an Astro site with automatic package manager detection.

#### 💚 [NuxtJS](templates/nuxtjs/)
Package and deploy a NuxtJS site with static site generation.

#### ⚫ [Next.js](templates/nextjs/)
Package and deploy a Next.js site with static export configuration.

#### 🟣 [Gatsby](templates/gatsby/)
Package and deploy a Gatsby site with build caching and optimization.

#### 🧱 [Remix](templates/remix/)
Full-stack framework with SSR and API integration. Designed for dynamic data fetching with seamless API integration.

#### ⚙️ [Vite App](templates/vite/)
Modern build tool for custom apps with direct API integration. Perfect for small to mid-sized apps using Vite.

### 🌱 Minimal & Flexible
### 🌱 Minimal & Flexible

Lightweight, modular generators for evolving systems.


Lightweight, modular generators for evolving systems.

#### 🌐 [Lume](templates/lume/)
Deno-based static site generator with native TypeScript support and modular architecture.

#### ⚡ [Hugo](templates/hugo/)
Package and deploy a Hugo site with extended features and Dart Sass support.


Lightweight, modular generators for evolving systems.


Lightweight, modular generators for evolving systems.

#### 🌐 [Lume](templates/lume/)
Deno-based static site generator with native TypeScript support and modular architecture.

#### ⚡ [Hugo](templates/hugo/)
Package and deploy a Hugo site with extended features and Dart Sass support.

#### 🌸 [Jekyll](templates/jekyll/)
Build and deploy a Jekyll site with custom Ruby setup and dependencies.

#### 🌸 [Jekyll with GitHub Pages](templates/jekyll-gh-pages/)
Deploy a Jekyll site with GitHub Pages dependencies preinstalled.

#### 🦀 [Cobalt](templates/cobalt/)
Rust-based static site generator that's fast and simple, similar to Jekyll but with better performance.

#### 🔷 [Bridgetown](templates/bridgetown/)
Modern Ruby-based static site generator, a progressive evolution of Jekyll with modern JavaScript support.

### 📄 Simple Deployment

No build process required - just deploy your files.

#### 📄 [Static HTML](templates/static-html/)
Deploy static HTML files without any build process - the simplest option.

### 🔮 WebAssembly & Unconventional Systems

Advanced deployments pushing the boundaries of what's possible with GitHub Pages.

#### 🖥️ [daedalOS Desktop](templates/daedalos/)
Deploy a complete desktop environment in the browser. Features window management, file system, terminal, code editor, games, and more. Built with React and Next.js.

#### 💻 [WebVM / CheerpX](templates/webvm/)
Deploy full Linux environments in the browser using WebAssembly. Based on the WebVM project, enables running complete operating systems with networking and persistent storage.

#### 🎮 [Emscripten Projects](templates/emscripten/)
Compile C/C++ applications to WebAssembly for browser deployment. Perfect for porting games, simulations, or system utilities.

#### 🐍 [Pyodide/JupyterLite](templates/jupyterlite/)
Run Python and Jupyter notebooks entirely in the browser without a backend server. Full scientific Python stack (NumPy, Pandas, Matplotlib) in a static site.

#### 🌐 [Plan 9 / 9front Explorer](templates/plan9-web/)
Web-based interface for exploring Plan 9 file systems and concepts. Connect to remote Plan 9 servers via 9P protocol over WebSockets.

#### 🔷 [Inferno Dis VM](templates/inferno-disvm/)
Deploy the Inferno Dis virtual machine compiled to WebAssembly. Run Limbo programs in the browser with Styx protocol support.

### 📖 Documentation Generators

Specialized tools for technical documentation and API references.

#### 📗 [MkDocs Material](templates/mkdocs-material/)
Python-based docs generator that renders Markdown "as-is", supports Python notebooks via `mkdocs-jupyter`, perfect for Python-heavy workflows.

#### 🕸 [MkDocs](templates/mkdocs/)
Fast documentation generator with Material theme for beautiful hierarchical documentation. Ideal for control plane UIs and system maps.

#### 🧠 [Sphinx](templates/sphinx/)
Documentation generator with optional Doxygen integration for C++ API docs. Ideal for generating API documentation from headers and keeping low-level primitives discoverable.

#### 🔮 [Quarto](templates/quarto/)
Literate notebook generator that converts Jupyter or RMarkdown notebooks into static sites. Perfect for step-by-step walkthroughs, plots, and reproducible experiments.

#### 🧭 [Redocly](templates/redocly/)
Interactive API documentation generator from OpenAPI specifications. Perfect for documenting service interfaces and API contracts.

#### 👁 [Starlight](templates/starlight/)
Package and deploy a Starlight site—Astro's documentation-focused framework for modular knowledge graphs.

#### 📘 [VitePress](templates/vitepress/)
Vite-powered static site generator designed for building fast, content-focused documentation sites with Vue ecosystem support.

### 🗂 Content Management Systems

Static site generators optimized for content-heavy sites and blogs.

#### 🧠 [Zola](templates/zola/)
Lightning-fast Rust-based static site generator with zero runtime dependencies and instantaneous builds.

#### 🧼 [Pelican](templates/pelican/)
Python-based static site generator with extensive plugin support for content pipelines and blog workflows.

## 🚀 Advanced & Impressive Deployments

While GitHub Pages is traditionally used for documentation and simple websites, the community has pushed the boundaries with remarkable implementations:

### 🖥️ System Emulators & Virtual Machines

#### WebVM - Full Linux in the Browser
[WebVM](https://github.com/leaningtech/webvm) demonstrates one of the most impressive GitHub Pages deployments: a full Linux virtual machine running entirely in the browser using WebAssembly. It includes:
- Complete x86 virtualization via CheerpX
- Networking capabilities through Tailscale
- Persistent storage options
- A fully functional Linux environment accessible via HTTPS

This proves that GitHub Pages can host complex, stateful applications that were previously unimaginable for static hosting.

#### JSLinux
Another impressive example running full operating systems (Linux, Windows 2000) in the browser using JavaScript and WebAssembly.

### 🎮 Game Engines & Interactive Experiences

- **Doom, Quake, and Classic Games**: Full game engines compiled to WebAssembly and deployed to GitHub Pages
- **Unity/Godot WebGL Exports**: Complete 3D games with physics engines and complex interactions
- **Emulator Collections**: RetroArch, MAME, and other emulators running classic console games

### 🔬 Scientific Computing & Visualization

- **Jupyter Notebooks**: Interactive computational notebooks (via JupyterLite) running Python entirely in-browser
- **TensorFlow.js Models**: ML model demos with real-time inference
- **3D Scientific Visualizations**: WebGL-based molecular viewers, astronomy simulations

### 📱 Full-Stack Applications (Frontend Only)

- **VS Code Web**: Browser-based code editors with syntax highlighting and extensions
- **Figma-like Design Tools**: Vector graphics editors running entirely client-side
- **Database GUIs**: SQLite running in WebAssembly with full query capabilities

### 🖥️ Desktop Environments in the Browser

#### daedalOS - Complete Desktop Experience
[daedalOS](https://github.com/DustinBrett/daedalOS) by Dustin Brett is a stunning achievement: a complete desktop environment running entirely in the browser. Features include:
- **Windows-like Interface**: Start menu, taskbar, window management
- **File System**: Virtual file system with ZIP/ISO support, drag-and-drop
- **Built-in Applications**: 
  - Monaco Editor (VS Code-like code editor)
  - Terminal emulator
  - Media player (video/audio)
  - Web browser within browser
  - PDF viewer, Markdown viewer
  - Classic games (Doom, Quake via js-dos)
  - Paint, notepad, and more
- **Customization**: Animated wallpapers, themes, persistent desktop state
- **Modern Web Tech**: Built with React, Next.js, and TypeScript

This demonstrates that GitHub Pages can host fully-featured desktop operating systems with file management, multi-tasking, and rich applications - all without backend infrastructure.

**Live Demo**: [dustinbrett.com](https://dustinbrett.com)

## 🌐 Distributed Systems on GitHub Pages

### Theoretical Approaches for Plan 9 & Inferno

GitHub Pages' static nature presents interesting challenges for distributed systems like Plan 9 or Inferno, but creative solutions exist:

#### Plan 9 Deployment Strategies

**1. WebAssembly Port**
- Compile Plan 9 components to WASM
- Use browser as the execution environment
- Implement 9P protocol over WebSockets (connecting to external servers)
- Deploy the compiled system as static assets

**2. Hybrid Architecture**
- Host Plan 9 documentation and command references as static content
- Provide web-based terminals that connect to remote Plan 9 CPU servers
- Use GitHub Pages as the UI layer for distributed Plan 9 infrastructure

**3. Read-Only File System Explorer**
- Deploy a JavaScript-based 9P file system browser
- Connect to public Plan 9 file servers
- Render the namespace hierarchy as an interactive web interface

#### Inferno Dis VM Deployment

**Dis VM in Browser**
- Port the Dis virtual machine to WebAssembly
- Load Dis bytecode modules as static assets
- Implement Limbo standard library in JavaScript/WASM
- Enable Styx protocol (9P equivalent) over WebSockets for remote resources

**Example Implementation Pattern:**
```yaml
# .github/workflows/deploy-inferno.yml
- Compile Dis VM to WebAssembly
- Package Limbo modules as static .dis files
- Deploy with a web-based shell/REPL
- Connect to external Inferno resources via WebRTC or WebSockets
```

**Real-World Applications:**
- Educational Inferno environments
- Distributed computing demonstrations
- Interactive Limbo programming tutorials

### Other Distributed System Patterns

#### IPFS-Backed GitHub Pages
- Use GitHub Pages as the entry point
- Load content from IPFS using js-ipfs
- Create truly distributed, censorship-resistant sites

#### WebRTC P2P Networks
- Deploy P2P chat applications
- Browser-based distributed file sharing
- Decentralized collaboration tools

#### Service Worker Architectures
- Implement offline-first distributed apps
- Background sync and caching strategies
- Progressive Web Apps (PWAs) with distributed data stores

## Emacs Lisp & AGI Research Templates

These templates are particularly useful for Emacs Lisp implementations, OpenCog, AGI research, and technical documentation in Emacs environments.

### 📝 [Org Mode (ox-publish)](templates/org-mode/)
Deploy technical documentation using Org Mode's built-in publishing system. Native to Emacs, lightweight, supports inline Emacs Lisp execution. Perfect for literate programming and documenting OpenCog/AGI projects with embedded code, results, and theory.

### 🧠 [Org-Roam](templates/org-roam/)
Deploy Zettelkasten-style knowledge bases from org-roam or Denote notes as searchable static sites. Knowledge graphs are integral to AGI development, and org-roam mirrors Hyperon's link structures.

### 📖 [Texinfo HTML](templates/texinfo/)
Generate HTML manuals from Texinfo `.texi` files using GNU's standard documentation format. Ideal for publishing Emacs Lisp system documentation such as AtomSpace or PLN modules.

### 🔬 [Literate Org (org-babel)](templates/literate-org/)
Create reproducible documents with executable code blocks using Org Babel (similar to Jupyter notebooks). Perfect for OpenCog-based reasoning experiments and PLN rule exploration.

### 🌐 [AtomSpace Visualizations](templates/atomspace-viz/)
Generate and deploy AtomSpace graph visualizations, attention values, and PLN inference traces. Converts `.dot` files to SVG via Graphviz and embeds them in HTML. Makes AGI system internals visible and explorable through the web.

## Usage

1. Browse to the template folder for your framework
2. Read the README in that folder for specific instructions
3. Copy the `deploy.yml` file to `.github/workflows/` in your repository
4. Update the branch name in the workflow file to match your default branch
5. Push to your repository to trigger the deployment

## Prerequisites

- A GitHub repository with your site's source code
- GitHub Pages enabled in your repository settings
- Appropriate configuration files for your chosen framework (e.g., `package.json`, `config.yml`, etc.)

## Contributing

Feel free to submit pull requests to improve these templates or add new ones!

## License

See [LICENSE](LICENSE) file for details.
