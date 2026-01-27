# Algo

A Voice RAG (Retrieval-Augmented Generation) application built entirely in Jac. This jacpack provides a voice-enabled AI assistant using OpenAI's Realtime API for natural conversational interactions.

## Prerequisites

- **Jaclang**: Version 0.9.11 or higher
- **Node.js**: 18+ with npm for frontend dependencies
- **OpenAI API Key**: Required for the Realtime API and voice features

## Installation

### 1. View template info (optional)

```bash
jac jacpack info Algo.jacpack
```

### 2. Create a new project from this jacpack

```bash
jac create my-voice-app --use Algo.jacpack
cd my-voice-app
```

### 3. Install dependencies

```bash
jac add
```

This will install both Python and npm dependencies defined in `jac.toml`.

### 4. Set environment variables

Create a `.env` file or export the following:

```bash
export OPENAI_API_KEY=your_openai_api_key
```

### 5. Start the application

```bash
jac start
```

The application will be available at `http://localhost:8000`.

## Features

- Voice-enabled AI assistant with real-time speech interaction
- RAG (Retrieval-Augmented Generation) for context-aware responses
- OpenAI Realtime API integration for low-latency voice conversations
- Modern React-based UI with Tailwind CSS styling
- Graph visualization capabilities

## Technical Architecture

- **Backend**: Jac walkers with RAG capabilities
- **Voice**: OpenAI Realtime API for speech-to-speech interaction
- **Frontend**: React with Tailwind CSS and Vite
- **Visualization**: @hpcc-js/wasm for graph rendering
- **Persistence**: Jac's built-in TieredMemory (SQLite-backed)

## Dependencies

### Python
- `jaclang` - Jac language runtime
- `jac-client` - Fullstack web framework

### NPM
- `react` / `react-dom` - UI framework
- `react-router-dom` - Client-side routing
- `@openai/agents` - OpenAI agent integration
- `tailwindcss` - Utility-first CSS framework
- `@hpcc-js/wasm` - Graph visualization
- `zod` - Schema validation

## Project Structure

After creation, your project will have:

```
my-voice-app/
├── jac.toml              # Project configuration
├── src/
│   └── app.jac           # Main application entry
├── components/           # Reusable UI components
└── assets/               # Static assets
```

## Configuration

The `jac.toml` file contains all project configuration. Key sections:

- `[project]` - Project metadata
- `[dependencies.npm]` - NPM packages
- `[serve]` - Server configuration
- `[plugins.client]` - Jac-client plugin settings
- `[plugins.client.vite]` - Vite configuration with Tailwind

## Troubleshooting

### Common Issues

1. **Missing OPENAI_API_KEY**: Ensure the environment variable is set
2. **Port already in use**: Change the port with `jac start --port 8001`
3. **Microphone access denied**: Grant browser microphone permissions for voice features
4. **Stale data after schema changes**: Delete `.jac/data/*.db*` files and restart

## Learn More

- [Jac Language Documentation](https://www.docs.jaseci.org/)
- [OpenAI Realtime API](https://platform.openai.com/docs/guides/realtime)
