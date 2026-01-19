# Emscripten Projects - C/C++ to WebAssembly

Deploy C/C++ applications compiled to WebAssembly using Emscripten for browser-based execution.

## Overview

Emscripten is a complete compiler toolchain that compiles C and C++ code to WebAssembly, enabling you to run native applications in the browser. This template helps you deploy Emscripten projects to GitHub Pages.

## What is Emscripten?

Emscripten provides:
- **C/C++ to WASM Compiler**: Complete LLVM-based toolchain
- **Standard Library Support**: libc, libc++, SDL, OpenGL ES
- **File System Emulation**: Virtual file systems in browser
- **Async Support**: Handle browser's event-driven nature

## Use Cases

- **Games**: Port classic games or game engines (Doom, Quake, Unity)
- **Scientific Computing**: Run simulation and analysis tools
- **Image/Video Processing**: FFmpeg, ImageMagick in browser
- **Legacy Software**: Revive old applications without rewriting
- **Educational Tools**: Interactive C/C++ demonstrations
- **Developer Tools**: Compilers, interpreters, utilities

## Prerequisites

- Emscripten SDK installed locally for development
- C/C++ source code
- Understanding of WebAssembly and browser APIs

## Quick Start

### 1. Install Emscripten

```bash
git clone https://github.com/emscripten-core/emsdk.git
cd emsdk
./emsdk install latest
./emsdk activate latest
source ./emsdk_env.sh
```

### 2. Compile Your Code

```bash
emcc hello.c -o hello.html
```

### 3. Deploy

Use the provided GitHub Actions workflow.

## Deployment Workflow

```yaml
name: Deploy Emscripten Project

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
      
      - name: Build with Emscripten
        run: |
          # Basic compilation
          emcc src/main.c -o dist/index.html \
            -s WASM=1 \
            -s USE_SDL=2 \
            --preload-file assets
      
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
│   ├── main.c                 # Main application
│   ├── game.cpp               # Game logic (if game)
│   └── utils.c                # Utilities
├── assets/                    # Resources to embed
│   ├── images/
│   ├── sounds/
│   └── data/
├── include/                   # Header files
├── Makefile                   # Build configuration
└── .github/
    └── workflows/
        └── deploy.yml
```

## Compilation Examples

### Basic Console Application

```bash
emcc hello.c -o hello.html
```

### With Optimization

```bash
emcc main.c -O3 -o output.html
```

### SDL2 Application (Games/Graphics)

```bash
emcc game.c -o game.html \
  -s USE_SDL=2 \
  -s USE_SDL_IMAGE=2 \
  -s SDL2_IMAGE_FORMATS='["png","jpg"]'
```

### With File System

```bash
emcc app.c -o app.html \
  --preload-file data/
```

### Custom HTML Template

```bash
emcc main.c -o main.js \
  --shell-file custom_template.html
```

### Advanced Options

```bash
emcc main.cpp -o app.html \
  -O3 \
  -s WASM=1 \
  -s ALLOW_MEMORY_GROWTH=1 \
  -s USE_SDL=2 \
  -s USE_SDL_IMAGE=2 \
  -s USE_SDL_TTF=2 \
  -s ASYNCIFY \
  --preload-file assets/ \
  --shell-file shell.html
```

## Common Compiler Flags

| Flag | Purpose |
|------|---------|
| `-O3` | Maximum optimization |
| `-s WASM=1` | Output WebAssembly (default) |
| `-s ALLOW_MEMORY_GROWTH=1` | Dynamic memory allocation |
| `-s ASYNCIFY` | Enable async/await in C/C++ |
| `--preload-file` | Embed files in virtual FS |
| `-s USE_SDL=2` | Include SDL2 library |
| `-s MODULARIZE=1` | Create module instead of global |
| `-s EXPORT_NAME='MyApp'` | Custom module name |

## Example Projects

### 1. Simple Graphics Demo

```c
#include <SDL2/SDL.h>
#include <emscripten.h>

SDL_Window *window;
SDL_Renderer *renderer;

void main_loop() {
    SDL_Event event;
    while (SDL_PollEvent(&event)) {
        if (event.type == SDL_QUIT) {
            emscripten_cancel_main_loop();
        }
    }
    
    SDL_SetRenderDrawColor(renderer, 0, 0, 0, 255);
    SDL_RenderClear(renderer);
    
    // Draw something
    SDL_SetRenderDrawColor(renderer, 255, 0, 0, 255);
    SDL_Rect rect = {100, 100, 200, 200};
    SDL_RenderFillRect(renderer, &rect);
    
    SDL_RenderPresent(renderer);
}

int main() {
    SDL_Init(SDL_INIT_VIDEO);
    window = SDL_CreateWindow("Demo", 0, 0, 800, 600, 0);
    renderer = SDL_CreateRenderer(window, -1, SDL_RENDERER_ACCELERATED);
    
    emscripten_set_main_loop(main_loop, 0, 1);
    
    return 0;
}
```

### 2. File I/O Example

```c
#include <stdio.h>
#include <emscripten.h>

int main() {
    FILE *f = fopen("data/file.txt", "r");
    if (f) {
        char buffer[256];
        while (fgets(buffer, sizeof(buffer), f)) {
            printf("%s", buffer);
        }
        fclose(f);
    }
    return 0;
}
```

### 3. JavaScript Interop

```c
#include <emscripten.h>

EM_JS(void, call_js_function, (), {
    console.log("Called from C!");
    alert("Hello from WebAssembly!");
});

int main() {
    call_js_function();
    return 0;
}
```

## Performance Optimization

### 1. Optimization Levels

- `-O0`: No optimization (fast compile, slow runtime)
- `-O1`: Basic optimization
- `-O2`: Good balance
- `-O3`: Maximum optimization
- `-Os`: Optimize for size

### 2. Memory Management

```bash
# Allow dynamic memory growth
emcc app.c -s ALLOW_MEMORY_GROWTH=1

# Set initial memory
emcc app.c -s INITIAL_MEMORY=64MB

# Set maximum memory
emcc app.c -s MAXIMUM_MEMORY=2GB
```

### 3. Code Splitting

```bash
# Create separate data file
emcc app.c -o app.html --preload-file assets/ --separate-asm
```

## Advanced Features

### Multithreading

```bash
emcc parallel.c -o parallel.html \
  -s USE_PTHREADS=1 \
  -s PTHREAD_POOL_SIZE=4
```

### SIMD Support

```bash
emcc simd.c -o simd.html \
  -msimd128
```

### WebGL

```c
#include <GLES2/gl2.h>
#include <emscripten/html5.h>

// OpenGL ES 2.0 code works as-is
glClearColor(0.0, 0.0, 0.0, 1.0);
glClear(GL_COLOR_BUFFER_BIT);
```

## Popular Ports

### Games
- **Doom**: Classic FPS game
- **Quake**: 3D shooter engine
- **ScummVM**: Adventure game interpreter
- **DOSBox**: DOS emulator

### Tools
- **FFmpeg**: Video/audio processing
- **ImageMagick**: Image manipulation
- **SQLite**: Database engine
- **Python**: Python interpreter (Pyodide)

### Libraries
- **Box2D**: Physics engine
- **Bullet**: 3D physics
- **FreeType**: Font rendering
- **Lua**: Scripting language

## Debugging

### Enable Debug Info

```bash
emcc -g app.c -o app.html
```

### Source Maps

```bash
emcc app.c -o app.html -g4 --source-map-base ./
```

### Assertions

```bash
emcc app.c -o app.html -s ASSERTIONS=1
```

## Resources

- [Emscripten Documentation](https://emscripten.org/docs/)
- [WebAssembly.org](https://webassembly.org/)
- [Awesome Emscripten](https://github.com/emscripten-core/emscripten/wiki/Porting-Examples-and-Demos)
- [Emscripten Tutorial](https://emscripten.org/docs/getting_started/)

## Limitations

- Synchronous file I/O requires special handling
- Some POSIX features unavailable
- Threading requires SharedArrayBuffer (not all browsers)
- Limited system call support
- No direct hardware access

## Tips

1. **Start Simple**: Begin with console applications before graphics
2. **Use Ports**: Leverage pre-built ports of common libraries
3. **Async Patterns**: Embrace browser's async nature with ASYNCIFY
4. **File System**: Use virtual FS for file I/O
5. **Testing**: Test in multiple browsers (Chrome, Firefox, Safari)
6. **Size Optimization**: Use `-Os` and code splitting for large apps
7. **Memory**: Monitor memory usage, browser limits vary
8. **JavaScript Integration**: Use EM_JS for calling browser APIs

## Best Practices

- Keep initial memory reasonable (start small, grow if needed)
- Preload only essential assets
- Use Web Workers for heavy computation
- Implement progressive loading for large applications
- Cache WASM modules with Service Workers
- Provide loading indicators for better UX
- Test across different devices and browsers
