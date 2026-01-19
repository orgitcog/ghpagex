# Plan 9 Web Explorer

Deploy a web-based interface for exploring Plan 9 operating system concepts, file systems, and remote servers.

## Overview

Plan 9 from Bell Labs introduced revolutionary concepts in distributed computing. This template helps you create web interfaces to explore Plan 9 systems, connect to remote Plan 9 servers, or demonstrate Plan 9 concepts interactively.

## What is Plan 9?

Plan 9 is a distributed operating system from Bell Labs that extends Unix philosophy:
- Everything is a file (including processes, networks, windows)
- 9P protocol for unified resource access
- Distributed namespace composition
- UTF-8 native support

## Deployment Approaches

### 1. Static Documentation & Visualization

Deploy comprehensive Plan 9 documentation with interactive visualizations of:
- 9P protocol flows
- Namespace hierarchies
- Process file systems
- Network topologies

### 2. 9P File System Browser

Create a web-based 9P client that connects to remote Plan 9 servers:
- Browse remote file systems
- Visualize namespace structure
- Demonstrate distributed resources

### 3. WebAssembly Plan 9 Components

Compile Plan 9 utilities to WebAssembly:
- rc shell (Plan 9 shell)
- Text processing tools
- File system utilities

## Use Cases

- **Education**: Interactive tutorials on Plan 9 concepts
- **Research**: Demonstrate distributed systems research
- **Documentation**: Comprehensive Plan 9 reference with live examples
- **Development**: Browser-based tools for Plan 9 developers
- **History**: Preserve and showcase Plan 9 innovations

## Prerequisites

- Node.js (for building JavaScript/TypeScript projects)
- Understanding of 9P protocol
- Access to a Plan 9 server (optional, for remote connections)
- WebSocket proxy for 9P connections (if connecting to real servers)

## Deployment Workflow

```yaml
name: Deploy Plan 9 Web Explorer

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
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Build site
        run: npm run build
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: 'dist'
  
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
your-repo/
├── src/
│   ├── 9p-client.js          # 9P protocol implementation
│   ├── namespace-viz.js       # Namespace visualization
│   ├── terminal.js            # Web-based terminal
│   └── examples/              # Plan 9 concept demos
├── docs/                      # Plan 9 documentation
├── assets/
│   ├── diagrams/              # System diagrams
│   └── examples/              # Code examples
├── index.html
├── package.json
└── .github/
    └── workflows/
        └── deploy.yml
```

## Implementation Examples

### 9P Client in JavaScript

```javascript
// Basic 9P message structure
class NinePClient {
    async connect(url) {
        this.ws = new WebSocket(url);
        await this.version();
    }
    
    async version() {
        const msg = {
            type: 'Tversion',
            msize: 8192,
            version: '9P2000'
        };
        return this.sendMessage(msg);
    }
    
    async walk(fid, newfid, path) {
        const msg = {
            type: 'Twalk',
            fid: fid,
            newfid: newfid,
            wname: path.split('/')
        };
        return this.sendMessage(msg);
    }
    
    // ... more 9P operations
}
```

### Namespace Visualization

```javascript
// Visualize Plan 9 namespace using D3.js or similar
function visualizeNamespace(root) {
    const tree = d3.tree()
        .size([height, width]);
    
    const nodes = tree(root);
    
    // Draw namespace hierarchy
    svg.selectAll('.link')
        .data(nodes.links())
        .enter().append('path')
        .attr('class', 'link')
        .attr('d', d3.linkHorizontal());
    
    // Label mount points, binds, etc.
}
```

## Key Features to Implement

### 1. Interactive 9P Protocol Demo

Show real-time 9P message exchanges:
- Tversion/Rversion handshake
- Walk, Open, Read, Write operations
- Error handling

### 2. Virtual File System

Implement a client-side file system following Plan 9 principles:
- Everything as a file
- Hierarchical namespace
- Union directories

### 3. Process File System (/proc)

Demonstrate how Plan 9 exposes process information:
- /proc/n/ctl (control)
- /proc/n/status (status)
- /proc/n/text (executable)

### 4. Network Resources

Show how Plan 9 makes network resources appear as files:
- /net/tcp
- /net/udp
- /net/ether

## Remote Server Connectivity

### WebSocket Proxy Setup

To connect to real Plan 9 servers, you need a WebSocket-to-9P proxy:

```javascript
// Client-side connection
const client = new NinePClient();
await client.connect('wss://your-9p-proxy.example.com');

// Server-side proxy (Node.js example)
const WebSocket = require('ws');
const net = require('net');

wss.on('connection', (ws) => {
    const plan9 = net.connect(564, 'plan9.server.com');
    ws.on('message', (data) => plan9.write(data));
    plan9.on('data', (data) => ws.send(data));
});
```

## Educational Content Ideas

1. **Unix vs Plan 9**: Interactive comparison of design philosophies
2. **9P Protocol Tutorial**: Step-by-step protocol walkthrough
3. **Distributed Computing**: Demonstrate resource sharing across machines
4. **Rio Window System**: Visualize Plan 9's unique window system
5. **Acme Editor**: Showcase mouse-based editing paradigm

## Related Projects

- **9front**: Modern continuation of Plan 9
- **harvey-os**: Modern, open-source Plan 9 derivative
- **inferno**: Related distributed OS (see inferno-disvm template)
- **plan9port**: Plan 9 tools ported to Unix

## Resources

- [Plan 9 Papers](https://9p.io/sys/doc/)
- [9P Protocol Specification](https://9p.io/sys/man/5/INDEX.html)
- [9front.org](http://9front.org/)
- [Plan 9 Desktop Guide](http://9p.io/wiki/plan9/desktop_guide/)
- [Russ Cox's Plan 9 Articles](https://research.swtch.com/plan9)

## Challenges & Solutions

### Challenge: Binary Protocol Over HTTP
**Solution**: Use WebSockets or convert to text-based representation

### Challenge: Authentication
**Solution**: Implement Plan 9's authentication protocol or use proxy authentication

### Challenge: Performance
**Solution**: Cache frequently accessed files, implement read-ahead

### Challenge: Cross-Origin Restrictions
**Solution**: Deploy proxy on same domain or use CORS-enabled proxy

## Alternatives

- **v9fs**: Linux 9P client (for actual file system mounting)
- **Drawterm**: Native Plan 9 client for multiple platforms
- **VNC/Remote Desktop**: Access Plan 9 GUI remotely

## Tips

1. **Start Simple**: Begin with static documentation and add interactivity
2. **Use SVG**: Visualize file system hierarchies and protocols
3. **Provide Examples**: Include working code snippets
4. **Historical Context**: Explain why Plan 9 design choices matter
5. **Modern Relevance**: Connect to current distributed systems (Kubernetes, etc.)

## Performance

- **Static Content**: Instant loading
- **9P Client**: Depends on remote server latency
- **Visualizations**: Optimize D3.js/Canvas rendering for large namespaces
- **WebAssembly**: Near-native speed for compiled Plan 9 tools
