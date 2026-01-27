# jac-gpt

A documentation assistant for Jac, built entirely in Jac. This jacpack provides a fullstack GPT-powered chat interface.

## Prerequisites

- **Jaclang**: Version 0.9.0 or higher
- **Node.js**: For frontend dependencies
- **OpenAI API Key**: Required for GPT functionality

## Installation

### 1. View template info (optional)

```bash
jac jacpack info jac-gpt.jacpack
```

### 2. Create a new project from this jacpack

```bash
jac create my-jac-gpt-app --use jac-gpt.jacpack
cd my-jac-gpt-app
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
jac start main.jac
```

The application will be available at `http://localhost:8000`.

## Features

- GPT-powered chat interface with intelligent routing
- RAG (Retrieval-Augmented Generation) for Jac documentation
- Code generation and debugging assistance
- Native Jac persistence (no external database required)
- Session management with chat history
- Admin dashboard for session monitoring
- Mantine UI components
- Markdown rendering with syntax highlighting

## Data Persistence

This application uses **Jac's built-in TieredMemory persistence** system. All data (sessions, chat history, user locations) is automatically stored in `.jac/data/` as SQLite databases. No external database setup is required.

## Dependencies

### Python
- `langchain-openai` - OpenAI integration
- `langchain-community` - Community LangChain tools
- `langchain-chroma` - Vector store
- `sentence-transformers` - Embeddings
- `faiss-cpu` - Vector similarity search

### NPM
- `@mantine/core` - UI components
- `react-markdown` - Markdown rendering
- `rehype-highlight` - Syntax highlighting

## Project Structure

After creation, your project will have:

```
my-jac-gpt-app/
├── jac.toml              # Project configuration
├── main.jac              # Main application entry
├── frontend/             # Client-side Jac components
├── components/           # Reusable UI components
├── services/             # Backend services
│   ├── jacServer.jac     # Walker and node definitions
│   ├── jacServer.impl.jac # Walker implementations
│   └── docs/             # Documentation for RAG
└── assets/               # Static assets
```

## API Endpoints

The application exposes the following walker endpoints:

| Endpoint | Description |
|----------|-------------|
| `/walker/new_session` | Create a new chat session |
| `/walker/interact` | Send a message and get a response |
| `/walker/get_session` | Retrieve session chat history |
| `/walker/suggest_docs` | Get relevant documentation suggestions |
| `/walker/close_session` | Close an active session |
| `/walker/get_all_sessions_admin` | List all sessions (admin) |

## Configuration

The `jac.toml` file contains all project configuration. Key sections:

- `[project]` - Project metadata
- `[dependencies]` - Python dependencies
- `[dependencies.npm]` - NPM packages
- `[serve]` - Server configuration
- `[plugins.client]` - Jac-client plugin settings

## Troubleshooting

### Common Issues

1. **Missing OPENAI_API_KEY**: Ensure the environment variable is set
2. **Port already in use**: Change the port with `jac start main.jac --port 8001`
3. **Stale data after schema changes**: Delete `.jac/data/*.db*` files and restart

## Learn More

- [Jac Language Documentation](https://www.docs.jaseci.org/)
