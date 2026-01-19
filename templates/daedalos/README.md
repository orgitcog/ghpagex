# daedalOS - Desktop Environment in the Browser

Deploy a complete desktop environment running entirely in the browser, featuring window management, file systems, applications, and a familiar desktop experience.

## Overview

[daedalOS](https://github.com/DustinBrett/daedalOS) is an impressive project by Dustin Brett that recreates a full desktop operating system experience in the browser. Built with modern web technologies, it demonstrates the incredible capabilities of static site hosting on GitHub Pages.

**Live Demo**: [dustinbrett.com](https://dustinbrett.com)

## Features

### 🪟 Desktop Environment

- **Window Management**: Resizable, draggable, maximizable windows with minimize/maximize/close controls
- **Taskbar**: Windows-style taskbar with start menu, pinned apps, and window previews
- **Start Menu**: Application launcher with search functionality
- **Desktop Icons**: Customizable desktop with file and folder icons
- **Context Menus**: Right-click menus for files, folders, and desktop
- **Multi-tasking**: Run multiple applications simultaneously

### 📁 File System

- **Virtual File System**: Complete file and folder hierarchy stored in browser
- **File Operations**: Create, rename, delete, copy, move files and folders
- **Archive Support**: Open and extract ZIP and ISO files
- **Drag & Drop**: Drag files between windows and desktop
- **File Search**: Search across the file system
- **Persistence**: File system state saved in IndexedDB

### 🎨 Customization

- **Wallpapers**: Static and animated wallpapers
- **Themes**: Multiple color schemes and visual themes
- **Desktop Layout**: Customizable icon positions and arrangements
- **Window Positions**: Remember and restore window states
- **Settings**: Comprehensive settings panel for personalization

### 🔨 Built-in Applications

#### Development Tools
- **Monaco Editor**: Full-featured code editor (powers VS Code)
  - Syntax highlighting for multiple languages
  - IntelliSense and code completion
  - File editing with save functionality
- **Terminal**: Command-line interface with various commands
  - File system navigation
  - System information
  - Custom commands

#### Productivity
- **File Explorer**: Windows Explorer-like file manager
  - Tree view and icon view
  - File preview
  - Search and filtering
- **Notepad**: Simple text editor
- **Markdown Viewer**: Render Markdown files
- **PDF Viewer**: View PDF documents

#### Media & Entertainment
- **Video Player**: Play video files (MP4, WebM, etc.)
- **Music Player**: Audio playback with playlist support
- **Photos**: Image viewer and slideshow
- **Paint**: Basic drawing application
- **Games**: Classic games via js-dos (Doom, Quake, etc.)

#### Utilities
- **Browser**: Web browser within the desktop
- **Calendar**: Date and calendar views
- **Clock**: System clock and timer
- **Calculator**: Basic calculator app

## Technology Stack

- **Framework**: React 18+ with Next.js
- **Language**: TypeScript
- **Styling**: Styled Components
- **State Management**: React Context + Hooks
- **File System**: Browser File System API + IndexedDB
- **Build Tool**: Next.js with static export
- **Deployment**: GitHub Pages

## Use Cases

- **Portfolio Projects**: Showcase your skills with an interactive desktop experience
- **Educational Platforms**: Teach operating system concepts interactively
- **Retro Gaming**: Host classic games in a nostalgic desktop environment
- **Development Environments**: Provide browser-based coding environments
- **Digital Museums**: Create interactive exhibits of computing history
- **Creative Demos**: Push the boundaries of web development

## Prerequisites

- Node.js 18+ and npm/yarn
- Understanding of React and Next.js
- Basic TypeScript knowledge (for customization)

## Quick Start

### 1. Fork or Clone daedalOS

```bash
git clone https://github.com/DustinBrett/daedalOS.git
cd daedalOS
```

### 2. Install Dependencies

```bash
yarn install
# or
npm install
```

### 3. Development Server

```bash
yarn dev
# or
npm run dev
```

Visit `http://localhost:3000` to see your desktop environment.

### 4. Build for Production

```bash
yarn build
# or
npm run build
```

This creates a static export in the `out/` directory.

## Deployment Workflow

```yaml
name: Deploy daedalOS

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
          cache: 'yarn'
      
      - name: Install dependencies
        run: yarn install --frozen-lockfile
      
      - name: Build daedalOS
        run: yarn build
        env:
          NEXT_PUBLIC_BASE_PATH: ""
      
      - name: Export static site
        run: yarn export
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: 'out'
  
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
daedalos/
├── components/           # React components
│   ├── system/          # System-level components
│   │   ├── Desktop/     # Desktop environment
│   │   ├── Taskbar/     # Taskbar component
│   │   └── Window/      # Window management
│   └── apps/            # Application components
│       ├── FileExplorer/
│       ├── Monaco/      # Code editor
│       ├── Terminal/
│       └── VideoPlayer/
├── contexts/            # React contexts
│   ├── fileSystem.tsx   # File system state
│   ├── process.tsx      # Process management
│   └── session.tsx      # Session state
├── public/              # Static assets
│   ├── System/          # System files
│   ├── Users/           # User files
│   └── wallpapers/      # Wallpaper images
├── styles/              # Global styles
├── utils/               # Utility functions
├── next.config.js       # Next.js configuration
├── package.json
└── tsconfig.json
```

## Customization

### Adding Custom Applications

1. Create a new component in `components/apps/`:

```typescript
// components/apps/MyApp/index.tsx
import { FC } from 'react';

const MyApp: FC = () => {
  return (
    <div>
      <h1>My Custom Application</h1>
      <p>Content goes here</p>
    </div>
  );
};

export default MyApp;
```

2. Register the app in the process context.

3. Add an icon to `public/System/Icons/`.

### Custom Wallpapers

Add images to `public/wallpapers/` and they'll appear in the wallpaper selector.

### Custom Themes

Modify styled-components theme in `styles/theme.ts`:

```typescript
export const myTheme = {
  colors: {
    primary: '#0078d4',
    background: '#1e1e1e',
    text: '#ffffff',
    // ... more colors
  },
};
```

### File System Content

Populate default files in `public/Users/Public/`:
- Documents/
- Pictures/
- Videos/
- Downloads/

## Advanced Features

### File System API

```typescript
import { useFileSystem } from 'contexts/fileSystem';

const MyComponent = () => {
  const { readFile, writeFile, deleteFile } = useFileSystem();
  
  // Read a file
  const content = await readFile('/path/to/file.txt');
  
  // Write a file
  await writeFile('/path/to/newfile.txt', 'content');
  
  // Delete a file
  await deleteFile('/path/to/file.txt');
};
```

### Process Management

```typescript
import { useProcesses } from 'contexts/process';

const MyComponent = () => {
  const { open, close, minimize } = useProcesses();
  
  // Open an application
  open('Monaco', { url: '/file.txt' });
  
  // Close an application
  close('Monaco');
};
```

### Window Positioning

Windows automatically save and restore their positions using browser storage.

## Performance Optimization

### Lazy Loading

Applications are lazy-loaded to reduce initial bundle size:

```typescript
const Monaco = dynamic(() => import('components/apps/Monaco'));
```

### Service Workers

daedalOS includes service worker support for:
- Offline functionality
- Asset caching
- Faster subsequent loads

### Code Splitting

Next.js automatically splits code by route and component.

## Browser Compatibility

- **Chrome/Edge**: Full support
- **Firefox**: Full support
- **Safari**: Full support (iOS 15+)
- **Mobile**: Responsive design with touch support

## Impressive Technical Achievements

1. **File System in Browser**: Complete file system implementation using IndexedDB
2. **Window Management**: Sophisticated window manager with stacking, focus, minimize/maximize
3. **Process Model**: Multi-process architecture similar to real operating systems
4. **Emulation**: Runs DOS games via js-dos emulator
5. **Rich Applications**: Monaco Editor, video player, PDF viewer all client-side
6. **State Persistence**: Entire desktop state saved and restored
7. **No Backend**: Everything runs client-side on GitHub Pages

## Similar Projects

- **WebVM**: Full Linux VM in browser
- **OS.js**: Another browser-based desktop environment
- **Windows 98**: Recreation of Windows 98
- **CloudOS**: Cloud-based desktop environment

## Resources

- [daedalOS Live Demo](https://dustinbrett.com)
- [GitHub Repository](https://github.com/DustinBrett/daedalOS)
- [Show HN Discussion](https://news.ycombinator.com/item?id=44088777)
- [Next.js Documentation](https://nextjs.org/docs)
- [React Documentation](https://react.dev)

## Limitations

- **Storage**: Limited to browser storage (typically 50MB-100MB IndexedDB)
- **Performance**: Slower than native desktop applications
- **File Operations**: Some OS-level operations not available
- **Network**: Limited by browser security (CORS, etc.)
- **Offline**: Requires initial online load (then works offline with service worker)

## Tips for Deployment

1. **Optimize Assets**: Compress images and videos
2. **Use CDN**: Host large files (ISOs, game files) externally
3. **Configure Base Path**: Set proper base path for subdirectory deployments
4. **Enable Service Worker**: Improve offline experience
5. **Test Mobile**: Ensure touch interactions work well
6. **Add Analytics**: Track usage patterns
7. **Custom Domain**: Use custom domain for professional look

## Best Practices

- **Keep Default Files Small**: Don't bloat initial file system
- **Progressive Loading**: Load heavy apps on demand
- **Mobile Experience**: Test on various screen sizes
- **Accessibility**: Ensure keyboard navigation works
- **Error Handling**: Gracefully handle file system errors
- **Documentation**: Provide in-app help for users
- **Updates**: Regular updates to dependencies for security

## Development Tips

1. **Hot Reload**: Use `yarn dev` for fast iteration
2. **Type Safety**: Leverage TypeScript for fewer bugs
3. **Component Reuse**: Build reusable UI components
4. **Context API**: Use contexts for global state
5. **Performance Profiling**: Use React DevTools to identify bottlenecks
6. **Git LFS**: Use Git LFS for large binary assets
7. **Testing**: Add tests for critical functionality

## Contributing

If forking for your own project:
1. Credit the original author (Dustin Brett)
2. Maintain the open-source license
3. Consider contributing improvements upstream
4. Share your customizations with the community

## Security Considerations

- **User Data**: All data stored locally in browser
- **XSS**: React provides XSS protection
- **HTTPS**: Deploy only over HTTPS
- **Content Security Policy**: Configure CSP headers appropriately
- **Third-party Content**: Be cautious loading external content

## Future Possibilities

- WebRTC for peer-to-peer file sharing
- WebGL for 3D desktop effects
- WebAssembly for better performance
- Cloud storage integration
- Multi-user collaboration
- Plugin system for third-party apps

## Conclusion

daedalOS represents one of the most impressive examples of what's possible with modern web technologies and GitHub Pages. It demonstrates that complex, stateful applications traditionally requiring backend infrastructure can run entirely client-side, opening new possibilities for web development.
