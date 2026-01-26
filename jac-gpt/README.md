# jac-gpt

A documentation assistant for Jac, built entirely in Jac. This jacpack provides a fullstack GPT-powered chat interface.

## Prerequisites

- **Jaclang**: Version 0.9.0 or higher
- **Node.js**: For frontend dependencies
- **OpenAI API Key**: Required for GPT functionality
- **MongoDB**: For data persistence

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
export MONGODB_URI=your_mongodb_connection_string
```

### 5. Start the application

```bash
jac start main.jac
```

The application will be available at `http://localhost:8000`.

## Features

- GPT-powered chat interface
- RAG (Retrieval-Augmented Generation) support
- MongoDB integration for conversation persistence
- Mantine UI components
- Markdown rendering with syntax highlighting

## Dependencies

### Python
- `langchain-openai` - OpenAI integration
- `langchain-community` - Community LangChain tools
- `langchain-chroma` - Vector store
- `pymongo` - MongoDB driver
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
├── components/           # Reusable UI components
├── services/             # Backend services
└── assets/               # Static assets
```

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
2. **MongoDB connection failed**: Verify your `MONGODB_URI` is correct
3. **Port already in use**: Change the port with `jac start main.jac --port 8001`
