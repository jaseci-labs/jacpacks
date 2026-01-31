# Jacpacks - Project Templates for Jac

Jacpacks are self-contained project templates that bundle everything you need to scaffold a full Jac application. Each `.jacpack` file is a portable archive containing source code, configuration, and setup hooks -- use them with `jac create` to spin up a working project in seconds.

This directory contains a collection of ready-to-use jacpacks showcasing different capabilities of the Jac ecosystem.

## Prerequisites

Before using any jacpack, make sure you have the following installed:

- **Python 3.12+**
- **Node.js 18+** with npm (for jacpacks that include a frontend)
- **Jac** -- install the full ecosystem bundle:

```bash
pip install jaseci
```

This installs `jaclang` along with all official plugins (`byllm`, `jac-client`, `jac-scale`, `jac-super`).

If you only need the language runtime:

```bash
pip install jaclang
```

Verify your installation:

```bash
jac version
```

### IDE Setup

Install the [Jac extension for VS Code](https://marketplace.visualstudio.com/items?itemName=jaseci-labs.jaclang-extension) (also works in Cursor) for syntax highlighting, diagnostics, and language server support.

---

## Quick Start

Every jacpack follows the same workflow:

```bash
# 1. Create a new project from a jacpack
jac create my-app --use <template>

# 2. Move into the project directory
cd my-app

# 3. Install dependencies
jac add

# 4. Set any required environment variables (see each jacpack's section below)

# 5. Start the application
jac start main.jac
```

The server runs at **http://localhost:8000** by default.

---

## Available Jacpacks

### AI Study Helper

An intelligent study companion that transforms text into structured educational material using specialized AI agents.

```bash
jac create my-study-app --use AI_Study_Helper.jacpack
cd my-study-app && jac add
```

**Required environment variables:**

```bash
export GEMINI_API_KEY=your_gemini_api_key
export TAVILY_API_KEY=your_tavily_api_key
```

**Features:**
- Agent-based architecture with dedicated Quiz, Summarizer, Explanation, and Flashcard agents
- Interactive assessment with multiple-choice question generation and progress tracking
- Web search integration via Tavily for real-time information retrieval
- Four-panel study workspace (quiz, summarize, explain, flashcards)

---

### TasteTalk

A restaurant feedback management system that collects, analyzes, and responds to customer feedback with AI-powered insights.

```bash
jac create my-tastetalk --use TasteTalk.jacpack
cd my-tastetalk && jac add
```

**Required environment variables:**

```bash
export GEMINI_API_KEY=your_gemini_api_key
```

**Features:**
- Customer portal for submitting feedback with AI-generated responses
- Admin dashboard with sentiment distribution charts, category tracking, and AI summaries
- Multi-language support (Sinhala/Tamil)
- Persistent storage with SQLite-backed TieredMemory
- Graph database backend via Jac-Scale

---

### Algo

A voice-enabled personal AI assistant with calendar, email, and GitHub integration.

```bash
jac create my-algo --use Algo.jacpack
cd my-algo && jac add
```

**Required environment variables:**

```bash
export OPENAI_API_KEY=your_openai_api_key
```

**Features:**
- Voice interface powered by OpenAI Realtime API
- Calendar and email management
- GitHub issue tracking integration
- Real-time task graph visualization
- Complete authentication system (register, login, protected routes)

---

### Multi-User Todo App

A full-stack authenticated todo list with hierarchical sub-todos and priority levels. A good starting point for learning Jac's fullstack capabilities.

```bash
jac create my-todo-app --use multi-user-todo-app.jacpack
cd my-todo-app && jac add
```

**Features:**
- User authentication (register, login, token-based sessions)
- Todo CRUD with three priority levels (high, medium, low)
- Hierarchical sub-todos with nested display
- CSS-driven dark theme UI with no inline styles
- Declaration/implementation separation pattern (`frontend.cl.jac` + `frontend.impl.jac`)

---

### Jac Playground

An interactive browser-based code editor and runner for Jac. Runs entirely client-side using WebAssembly and Pyodide -- no backend required.

```bash
jac create my-playground --use jacplayground.jacpack
cd my-playground && jac add --npm
jac start
```

**Features:**
- Monaco editor with Jac syntax highlighting
- Real-time in-browser code execution via Pyodide
- Interactive graph visualizer for Jac data structures
- Bidirectional Jac/Python code conversion
- Debugging tools with breakpoint support
- Built-in example library
- Dark/light mode and mobile-responsive layout

---

### Jac GPT

A documentation assistant for the Jac language, built as a fullstack Jac application.

```bash
jac create my-jac-gpt --use jac-gpt.jacpack
cd my-jac-gpt && jac add
```

**Required environment variables:**

```bash
export OPENAI_API_KEY=your_openai_api_key
```

**Features:**
- Conversational interface for querying Jac documentation
- MongoDB-backed data persistence

---

## Jacpack CLI Reference

### Listing available templates

```bash
# List all registered templates (from installed plugins and local files)
jac create --list-jacpacks

# Or use the jacpack subcommand
jac jacpack list
```

### Inspecting a jacpack

```bash
jac jacpack info AI_Study_Helper.jacpack
```

### Creating a project

Templates can be referenced by registered name, local file path, or URL:

```bash
# From a registered template name
jac create my-app --use client

# From a local .jacpack file
jac create my-app --use ./path/to/template.jacpack

# From a template directory (must contain a jac.toml with a [jacpack] section)
jac create my-app --use ./my-template-dir/

# From a remote URL
jac create my-app --use https://example.com/template.jacpack
```

### Managing dependencies

```bash
# Install all dependencies defined in jac.toml
jac add

# Add a Python package
jac add requests

# Add an npm package (requires jac-client plugin)
jac add react --npm

# Install dependencies without adding new ones
jac install
```

### Running a project

```bash
# Run a Jac file directly
jac run main.jac

# Start a server (for fullstack apps)
jac start main.jac
```

---

## Creating Your Own Jacpack

You can bundle any Jac project into a distributable jacpack.

### 1. Add a `[jacpack]` section to your `jac.toml`

```toml
[project]
name = "{{name}}"
version = "0.1.0"
entry-point = "main.jac"

[dependencies]
requests = ">=2.28.0"

[jacpack]
name = "my-template"
description = "A brief description of what this template provides"
jaclang = "0.9.0"
```

Use `{{name}}` as a placeholder in your `jac.toml` and source files -- it gets replaced with the project name during `jac create`.

### 2. Bundle it

```bash
jac jacpack pack ./my-template-dir
```

This produces a `my-template.jacpack` file.

### 3. Share it

Others can use your jacpack directly:

```bash
jac create cool-project --use ./my-template.jacpack
```

Or host it at a URL for remote access:

```bash
jac create cool-project --use https://example.com/my-template.jacpack
```

---

## Project Structure

A typical Jac project created from a jacpack looks like this:

```
my-app/
├── jac.toml          # Project config and dependencies
├── main.jac          # Application entry point
├── *.jac             # Additional Jac source files
├── .jac/             # Managed directory (venv, client builds, etc.)
│   └── venv/         # Isolated Python virtual environment
└── .gitignore
```

The `.jac/` directory is auto-managed -- it holds the project's virtual environment and any plugin-generated artifacts (like client-side builds). It should be gitignored.

---

## Useful Links

- [Jac Documentation](https://docs.jaseci.org)
- [CLI Reference](https://docs.jaseci.org/reference/cli/)
- [GitHub Repository](https://github.com/Jaseci-Labs/jaseci)
- [VS Code Extension](https://marketplace.visualstudio.com/items?itemName=jaseci-labs.jaclang-extension)
