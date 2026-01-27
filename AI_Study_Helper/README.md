# AI Study Helper

An intelligent study companion built entirely in Jac. This jacpack transforms text into structured educational material using specialized AI agents that classify and route queries to appropriate handlers.

## Prerequisites

- **Jaclang**: Version 0.9.0 or higher
- **Node.js**: 18+ with npm for frontend dependencies
- **Google Gemini API Key**: Required for AI-powered content generation
- **Tavily API Key**: Required for web search capabilities

## Installation

### 1. View template info (optional)

```bash
jac jacpack info AI_Study_Helper.jacpack
```

### 2. Create a new project from this jacpack

```bash
jac create my-study-helper --use AI_Study_Helper.jacpack
cd my-study-helper
```

### 3. Install dependencies

```bash
jac add
```

This will install both Python and npm dependencies defined in `jac.toml`.

### 4. Set environment variables

Create a `.env` file or export the following:

```bash
export GEMINI_API_KEY=your_gemini_api_key
export TAVILY_API_KEY=your_tavily_api_key
```

### 5. Start the application

```bash
jac start main.jac
```

The application will be available at `http://localhost:8000`.

## Features

### Agent-Based Architecture
- **Quiz Agent** - Generates multiple-choice questions and evaluates answers
- **Summarizer Agent** - Produces concise summaries of text content
- **Explanation Agent** - Provides step-by-step or simplified breakdowns
- **Flashcard Agent** - Creates question-answer study cards
- **Task Manager** - Identifies user intent and dispatches to appropriate agent

### Study Workspace
Four separate panels for focused, distraction-free studying:
- Quiz panel for MCQ generation and testing
- Summarize panel for content condensation
- Explain panel for detailed breakdowns
- Flashcards panel for memorization aids

### Interactive Assessment
- Generate MCQs from any text
- Submit answers and receive immediate feedback
- Track your learning progress

## Technical Architecture

- **Backend**: Jac walkers with specialized AI agents
- **LLM**: Google Gemini for content generation
- **Search**: Tavily API for web search integration
- **Frontend**: React-style Jac-Client components
- **Persistence**: Jac's built-in TieredMemory (SQLite-backed)

## Dependencies

### Python
- `jaclang` - Jac language runtime
- `jac-client` - Fullstack web framework
- `byllm` - LLM integration plugin

### NPM
- React-style UI components
- Styling and layout utilities

## Project Structure

After creation, your project will have:

```
my-study-helper/
├── jac.toml              # Project configuration
├── main.jac              # Main application entry
├── endpoints.sv.jac      # Server-side models and walkers
├── frontend.cl.jac       # React-style UI components
├── components/           # Reusable UI components
└── assets/               # Static assets (images, CSS)
```

## API Endpoints

| Endpoint | Description |
|----------|-------------|
| `/walker/quiz` | Generate quiz questions from text |
| `/walker/quiz_answer` | Submit and evaluate quiz answers |
| `/walker/summarize` | Generate text summaries |
| `/walker/explain` | Get detailed explanations |
| `/walker/flashcards` | Create study flashcards |

## Configuration

The `jac.toml` file contains all project configuration. Key sections:

- `[project]` - Project metadata
- `[dependencies]` - Python dependencies
- `[dependencies.npm]` - NPM packages
- `[serve]` - Server configuration
- `[plugins.client]` - Jac-client plugin settings

## Troubleshooting

### Common Issues

1. **Missing GEMINI_API_KEY**: Ensure the environment variable is set
2. **Missing TAVILY_API_KEY**: Required for web search features
3. **Port already in use**: Change the port with `jac start main.jac --port 8001`
4. **Stale data after schema changes**: Delete `.jac/data/*.db*` files and restart

## Learn More

- [Jac Language Documentation](https://www.docs.jaseci.org/)
- [AI Study Helper Source Repository](https://github.com/Hushan-10/AI_Study_Helper)

## License

MIT
