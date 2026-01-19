# Inferno Dis VM - WebAssembly Deployment

Deploy the Inferno Dis virtual machine to run Limbo programs entirely in the browser.

## Overview

Inferno is a distributed operating system derived from Plan 9, featuring the Dis virtual machine and Limbo programming language. This template demonstrates how to compile and deploy Inferno's Dis VM to WebAssembly for browser-based execution.

## What is Inferno?

Inferno OS features:
- **Dis VM**: Portable virtual machine with garbage collection
- **Limbo**: Type-safe systems programming language
- **Styx Protocol**: Network protocol (based on 9P) for distributed resources
- **Concurrent Programming**: Built-in channels and processes

## Key Concepts

### Dis Virtual Machine
- Register-based VM (unlike JVM's stack-based architecture)
- Garbage collected memory management
- Module system with dynamic loading
- Cross-platform bytecode

### Limbo Language
```limbo
implement Hello;

include "sys.m";
    sys: Sys;
include "draw.m";

Hello: module {
    init: fn(ctxt: ref Draw->Context, args: list of string);
};

init(ctxt: ref Draw->Context, args: list of string)
{
    sys = load Sys Sys->PATH;
    sys->print("Hello, World!\n");
}
```

## Use Cases

- **Educational Platform**: Teach concurrent programming and distributed systems
- **Research**: Experiment with VM design and bytecode systems
- **Historical Computing**: Preserve and demonstrate Inferno system
- **Language Learning**: Interactive Limbo programming tutorials
- **Protocol Demos**: Showcase Styx/9P protocol implementations

## Prerequisites

- Inferno source code
- Emscripten (for compiling to WebAssembly)
- Node.js (for build tools)
- Basic understanding of Inferno/Limbo

## Deployment Workflow

```yaml
name: Deploy Inferno Dis VM

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
      
      - name: Setup Emscripten
        uses: mymindstorm/setup-emsdk@v14
        with:
          version: 'latest'
      
      - name: Build Dis VM to WASM
        run: |
          # Clone Inferno if needed
          # git clone https://github.com/inferno-os/inferno-os inferno
          cd inferno
          # Configure for WebAssembly build
          emcc emu/port/wasm.c \
               -s WASM=1 \
               -s EXPORTED_FUNCTIONS='["_disinit","_disrun","_disload"]' \
               -s EXPORTED_RUNTIME_METHODS='["ccall","cwrap"]' \
               -o dis.js
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      
      - name: Build web interface
        run: |
          npm ci
          npm run build
      
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
├── inferno/                    # Inferno source (submodule or vendored)
│   ├── emu/                   # Dis VM emulator
│   ├── dis/                   # Bytecode files
│   └── module/                # Module definitions
├── src/
│   ├── dis-loader.js          # WASM loader for Dis VM
│   ├── limbo-editor.js        # Code editor
│   ├── styx-client.js         # Styx protocol implementation
│   └── repl.js                # Interactive shell
├── examples/
│   ├── hello.b                # Limbo source files
│   ├── concurrent.b           # Concurrency examples
│   └── network.b              # Network programming
├── modules/                    # Pre-compiled .dis files
├── index.html
├── package.json
└── .github/
    └── workflows/
        └── deploy.yml
```

## Implementation Strategy

### 1. Compile Dis VM to WebAssembly

```bash
# Minimal Dis VM compilation
emcc -O3 \
     emu/port/dis.c \
     emu/port/alloc.c \
     emu/port/gc.c \
     -s WASM=1 \
     -s ALLOW_MEMORY_GROWTH=1 \
     -s MODULARIZE=1 \
     -s EXPORT_NAME='DisVM' \
     -o dis.js
```

### 2. JavaScript Wrapper

```javascript
class InfernoDisVM {
    constructor() {
        this.vm = null;
    }
    
    async initialize() {
        this.vm = await DisVM();
        this.vm._disinit();
    }
    
    loadModule(bytecode) {
        // Load .dis bytecode into VM
        const ptr = this.vm._malloc(bytecode.length);
        this.vm.HEAPU8.set(bytecode, ptr);
        return this.vm._disload(ptr, bytecode.length);
    }
    
    execute(module, function_name) {
        // Execute Limbo function
        return this.vm._disrun(module, function_name);
    }
}
```

### 3. Limbo Compiler in Browser (Optional)

For a complete experience, compile the Limbo compiler to WASM:

```javascript
// Compile Limbo source to Dis bytecode in browser
async function compileLimbo(source) {
    const compiler = await LimboCompiler();
    const bytecode = compiler.compile(source);
    return bytecode;
}
```

## Features to Implement

### 1. Interactive REPL

```html
<div id="repl">
    <textarea id="input" placeholder="Enter Limbo code..."></textarea>
    <button onclick="execute()">Run</button>
    <pre id="output"></pre>
</div>
```

### 2. Module Browser

Display available Inferno modules:
- Sys (system calls)
- Draw (graphics)
- Tk (GUI toolkit)
- Math (mathematical functions)
- String (string operations)

### 3. Concurrency Visualizer

Show Limbo's channel communication:
```limbo
chan of int c;
c = chan of int;

# Sender
spawn sender(c);

# Receiver
v := <-c;
```

### 4. Styx/9P Client

Implement Styx protocol for distributed resources:

```javascript
class StyxClient {
    async connect(server) {
        this.ws = new WebSocket(server);
    }
    
    async attach(uname, aname) {
        // Styx Tattach message
    }
    
    async open(path, mode) {
        // Styx Topen message
    }
    
    async read(fid, offset, count) {
        // Styx Tread message
    }
}
```

## Example Applications

### Hello World

```limbo
implement Hello;

include "sys.m";
sys: Sys;

Hello: module {
    init: fn(ctxt: ref Draw->Context, args: list of string);
};

init(ctxt: ref Draw->Context, args: list of string)
{
    sys = load Sys Sys->PATH;
    sys->print("Hello from Inferno!\n");
}
```

### Concurrent Programming

```limbo
implement Concurrent;

include "sys.m";
sys: Sys;

Concurrent: module {
    init: fn(ctxt: ref Draw->Context, args: list of string);
};

init(ctxt: ref Draw->Context, args: list of string)
{
    sys = load Sys Sys->PATH;
    
    c := chan of int;
    
    spawn sender(c);
    spawn receiver(c);
    
    sys->sleep(1000);
}

sender(c: chan of int)
{
    for(i := 0; i < 10; i++) {
        c <-= i;
        sys->print("sent %d\n", i);
    }
}

receiver(c: chan of int)
{
    for(;;) {
        v := <-c;
        sys->print("received %d\n", v);
    }
}
```

## Architecture Comparison

| Feature | Inferno Dis VM | JVM | .NET CLR |
|---------|---------------|-----|----------|
| Architecture | Register-based | Stack-based | Stack-based |
| GC | Concurrent | Generational | Generational |
| Concurrency | Channels | Threads | Threads |
| Typing | Strong, static | Strong, static | Strong, static |
| Protocol | Styx (9P) | RMI | Remoting |

## Educational Content

### 1. VM Internals Tutorial
- Bytecode format
- Instruction set
- Module loading
- Garbage collection

### 2. Limbo Language Guide
- Type system
- Concurrency primitives
- Module system
- ADTs (Abstract Data Types)

### 3. Distributed Computing
- Styx protocol
- Namespace composition
- Remote resources

### 4. Comparison with Go
Show how Go inherited concepts from Limbo:
- Channels and goroutines
- Garbage collection
- Strong typing
- Simplicity

## Resources

- [Inferno OS](http://www.vitanuova.com/inferno/)
- [Inferno GitHub](https://github.com/inferno-os/inferno-os)
- [Limbo Language Reference](http://www.vitanuova.com/inferno/papers/limbo.html)
- [Dis VM Specification](http://www.vitanuova.com/inferno/papers/dis.html)
- [Styx Protocol](http://www.vitanuova.com/inferno/papers/styx.html)

## Challenges

### Challenge: File System Access
**Solution**: Implement virtual file system in browser storage or IndexedDB

### Challenge: Native Modules
**Solution**: Reimplement essential modules in JavaScript/WASM

### Challenge: Graphics (Draw module)
**Solution**: Map Draw operations to HTML5 Canvas

### Challenge: Network I/O
**Solution**: Use WebSockets for Styx connections

## Related Technologies

- **Plan 9**: Parent operating system
- **Go Language**: Inspired by Limbo (channels, simplicity)
- **Erlang**: Similar concurrency model
- **WebAssembly**: Execution target

## Performance Characteristics

- **VM Initialization**: 100-500ms
- **Module Loading**: 10-50ms per module
- **Execution Speed**: 2-10x slower than native (typical WASM overhead)
- **Memory Usage**: Depends on program, GC keeps it bounded
- **Startup Time**: Fast due to small VM size (~500KB)

## Tips

1. **Start Small**: Begin with basic examples (hello world, arithmetic)
2. **Incremental Features**: Add concurrency, then I/O, then networking
3. **Documentation**: Explain Limbo concepts for newcomers
4. **Comparisons**: Relate to modern languages (Go, Rust)
5. **Visualizations**: Show concurrent processes and channel communication
6. **Historical Context**: Explain Inferno's role in OS research

## Future Enhancements

- Full Tk GUI support (map to HTML/CSS)
- WebGL support for Draw module
- WebRTC for peer-to-peer Styx connections
- Service worker for offline operation
- WASI integration for better file system support
