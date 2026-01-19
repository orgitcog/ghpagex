# WebVM / CheerpX Deployment

Deploy full Linux environments running in the browser using WebAssembly and CheerpX technology.

## Overview

WebVM is a groundbreaking project that runs a complete Linux virtual machine in the browser using WebAssembly. This template helps you deploy similar WebAssembly-based system emulators to GitHub Pages.

## What is WebVM?

[WebVM](https://github.com/leaningtech/webvm) by Leaning Technologies demonstrates:
- Full x86 virtualization in the browser via CheerpX
- Networking through Tailscale
- Persistent storage options
- Complete Linux environment (based on Debian)

## Use Cases

- **Interactive Demos**: Showcase Linux applications without requiring installation
- **Educational Environments**: Provide sandboxed learning environments for system administration
- **Development Environments**: Offer browser-based development setups
- **Legacy Software**: Run older Linux applications in modern browsers

## Prerequisites

- A CheerpX license (free for open source projects)
- Pre-built Linux disk images or CheerpX filesystem
- Network configuration files (if needed)

## Setup

1. Build or obtain your WebAssembly system image
2. Configure networking (optional - Tailscale, WebSockets)
3. Set up the HTML/JavaScript interface
4. Deploy using the provided workflow

## Deployment Workflow

```yaml
name: Deploy WebVM to GitHub Pages

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
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Pages
        uses: actions/configure-pages@v5
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## Project Structure

```
your-repo/
├── index.html              # Main page with CheerpX loader
├── cx/                     # CheerpX runtime files
├── images/                 # Disk images
│   └── debian_large.ext2   # Linux filesystem
├── networking/             # Network configuration (optional)
└── .github/
    └── workflows/
        └── deploy.yml
```

## Example Implementation

### Basic index.html
```html
<!DOCTYPE html>
<html>
<head>
    <title>WebVM - Linux in Your Browser</title>
    <script src="cx/cheerpx-loader.js"></script>
</head>
<body>
    <div id="console"></div>
    <script>
        CheerpXLoader.load({
            container: document.getElementById("console"),
            diskImage: "images/debian_large.ext2",
            networkInterface: "tailscale" // optional
        });
    </script>
</body>
</html>
```

## Advanced Features

### Networking
- **Tailscale**: Secure VPN networking
- **WebSockets**: Connect to external services
- **WebRTC**: Peer-to-peer communication

### Persistence
- **IndexedDB**: Store filesystem changes locally
- **Cloud Storage**: Sync state to remote storage

### Performance Optimization
- **Lazy Loading**: Load filesystem blocks on demand
- **Compression**: Use compressed disk images
- **Service Workers**: Cache assets for offline use

## Alternatives & Related Projects

- **JSLinux**: Another full OS in browser implementation
- **v86**: x86 emulator in JavaScript
- **Emscripten**: General C/C++ to WebAssembly compiler
- **box86/box64**: ARM to x86 translation (can be combined with WebAssembly)

## Resources

- [WebVM Official Site](https://webvm.io/)
- [CheerpX Documentation](https://leaningtech.com/cheerpx/)
- [WebAssembly System Interface (WASI)](https://wasi.dev/)
- [Browser-based Linux Terminal](https://github.com/leaningtech/webvm)

## Limitations

- Performance depends on browser and device
- Some system calls may not be fully supported
- File size constraints (GitHub Pages has a 1GB soft limit per repository)
- No GPU acceleration in most browsers yet

## Tips

1. **Optimize Images**: Use minimal Linux distributions (Alpine, BusyBox)
2. **CDN Hosting**: Consider hosting large disk images on external CDN
3. **Progressive Loading**: Implement loading indicators for better UX
4. **Mobile Support**: Test on mobile browsers (performance varies significantly)

## License Considerations

- CheerpX requires a commercial license for closed-source projects
- Linux images must comply with GPL and distribution licenses
- WebVM itself is Apache 2.0 licensed
