# jac-playground

An interactive code playground for Jac, built entirely in Jac. This jacpack provides a fully browser-based environment for writing, testing, debugging, and visualizing Jac code in real-time. Powered by WebAssembly and Pyodide, the playground runs entirely in your browser with no backend required.

## Prerequisites

- **Jaclang**: Version 0.9.0 or higher
- **Node.js**: For frontend dependencies
- **Python**: 3.12 or higher (for Pyodide runtime)

## Installation

### 1. View template info (optional)

```bash
jac jacpack info jacplayground.jacpack
```

### 2. Create a new project from this jacpack

```bash
jac create my-jac-playground --use jacplayground.jacpack
cd my-jac-playground
```

### 3. Install dependencies

```bash
jac add --npm
```

This will install both Python and npm dependencies defined in `jac.toml`.

### 4. Start the application

```bash
jac start
```

The application will be available at `http://localhost:8000`.

## Features

- **Monaco Editor** - Full-featured code editor with syntax highlighting
- **Real-time Execution** - Run Jac code directly in the browser using Pyodide
- **Graph Visualizer** - Interactive visualization of Jac graph structures
- **Code Conversion** - Convert between Jac and Python
- **Debugging Tools** - Set breakpoints and step through code execution
- **Example Library** - Pre-built examples to learn Jac
- **Mobile Responsive** - Works seamlessly on desktop, tablet, and mobile devices
- **Dark/Light Mode** - Theme support for comfortable coding
- **Split View** - Multiple panels for code, output, and graph visualization

## Dependencies

### NPM
- `jac-client-node` - Jac client library
- `@monaco-editor/react` - Code editor component
- `monaco-editor` - Monaco editor core
- `tailwindcss` - Utility-first CSS framework
- `@tailwindcss/vite` - Tailwind CSS Vite plugin
- `lucide-react` - Icon library
- `react-graph-vis` - Graph visualization
- `vis-network` - Network visualization library
- `vis-data` - Data handling for visualizations
- `clsx` & `tailwind-merge` - CSS utilities

### Dev Dependencies
- `watchdog` - File system monitoring for hot reload

## Project Structure

After creation, your project will have:

```
my-jac-playground/
├── jac.toml              # Project configuration
├── main.jac              # Main application entry
├── components/           # UI components
│   ├── Index.cl.jac
│   ├── PlayGroundLayout.cl.jac
│   ├── TopBar.cl.jac
│   ├── Visualizer.cl.jac
│   ├── ConversionEditor.cl.jac
│   ├── JacWorkspace.cl.jac
│   ├── Layout/           # Desktop layout components
│   ├── Mobile/           # Mobile-specific components
│   ├── Controllers/      # Debug controllers
│   └── ui/               # Reusable UI components
├── hooks/                # React hooks
│   ├── usePlayground.cl.jac
│   ├── useMobile.cl.jac
│   └── useEditor.cl.jac
├── lib/                  # Utility libraries
│   ├── python_thread.cl.jac
│   ├── syntax_highlighting.cl.jac
│   └── utils.cl.jac
├── services/             # Backend services
│   └── fetch_examples.jac
├── styles/               # Global styles
│   └── global.css
└── assets/               # Static assets
```

## Configuration

The `jac.toml` file contains all project configuration. Key sections:

- `[project]` - Project metadata and entry point
- `[dependencies.npm]` - NPM packages for the client
- `[dev-dependencies]` - Development dependencies
- `[serve]` - Server configuration
- `[plugins.client.vite]` - Vite bundler configuration
- `[environments.response]` - HTTP headers for CORS and security

## Usage

### Running Code

1. Write your Jac code in the editor
2. Click the **Run** button or use keyboard shortcuts
3. View output in the console panel
4. See graph visualizations in the graph panel

### Debugging

1. Click in the gutter (left margin) to set breakpoints
2. Enable debug mode with the debug toggle
3. Run your code
4. Use step controls to navigate through execution

### Code Conversion

1. Switch to **Jac to Python** or **Python to Jac** mode
2. Enter your code
3. Click **Convert**
4. View the converted output

### Examples

Browse pre-built examples from the examples panel to learn Jac syntax and patterns.
