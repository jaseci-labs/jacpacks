# Multi-User Todo App with AI Meal Planner

A full-stack Jac application combining an authenticated todo list with an AI-powered meal planner that generates shopping lists with ingredient costs and nutritional indicators.

## Prerequisites

- **Jaclang**: Version 0.9.8 or higher
- **Node.js**: 18+ with npm for frontend dependencies
- **Anthropic API Key**: Required for the AI meal planner feature

## Installation

### 1. View template info (optional)
```bash
jac jacpack info multi-user-todo-meals-app.jacpack
```

### 2. Create a new project from this jacpack
```bash
jac create my-meals-app --use multi-user-todo-meals-app.jacpack
cd my-meals-app
```

### 3. Install dependencies
```bash
jac add
```
This will install both Python and npm dependencies defined in `jac.toml`.

### 4. Set environment variables
```bash
export ANTHROPIC_API_KEY=your_anthropic_api_key
```

### 5. Start the application
```bash
jac start main.jac
```
The application will be available at `http://localhost:8000`.

## Features

### Authentication
- User registration and login
- Token-based session management
- Per-user isolated data

### Todo Management
- Create, toggle, and delete todos
- Three priority levels (high, medium, low)
- Hierarchical sub-todos with nested display
- Real-time UI updates

### AI Meal Planner
- Describe any meal and generate a full shopping list using Claude
- Ingredient quantities with units (piece, lb, oz, cup, tbsp, tsp, clove, bunch)
- Estimated costs in JMD (Jamaican Dollars)
- Carbohydrate/glucose spike indicators for health-conscious planning
- Total cost calculation with clear button

### Modern UI
- Two-column responsive layout (todos on left, meal planner on right)
- Dark theme with orange and green accent palette
- CSS-driven styling with no inline styles
- Loading spinner and disabled state during AI generation
- Responsive: stacks to single column on screens under 900px

## Technical Architecture

- **Backend**: Jac walkers operating on a graph of Todo nodes, plus LLM-powered ingredient generation via `byllm`
- **Frontend**: React-style Jac-Client components with CSS classes
- **AI**: Claude Sonnet via `byllm` with structured output (typed `Ingredient` objects with semantic annotations)
- **Persistence**: Jac's built-in TieredMemory (SQLite-backed)
- **Auth**: Built-in jac-client authentication (signup/login/logout)

## Dependencies

### Python
- `jaclang` - Jac language runtime
- `jac-client` - Fullstack web framework
- `byllm` - LLM integration plugin (provides `Model` and `by llm()` syntax)

### NPM
- `jac-client-node` - Client-side runtime
- `tailwindcss` - CSS framework (configured in jac.toml)

## Project Structure

After creation, your project will have:
```
my-meals-app/
├── jac.toml                          # Project configuration
├── main.jac                          # Entry point with Todo nodes, walkers, and AI functions
├── frontend.cl.jac                   # Client-side UI component (declarations)
├── frontend.impl.jac                 # Client-side logic (implementations)
├── styles.css                        # All application styles
├── components/                       # Reusable UI components
│   ├── TodoItem.cl.jac               # Todo item with priority badge
│   ├── AuthForm.cl.jac               # Login/signup form
│   ├── IngredientItem.cl.jac         # Ingredient row with cost and carb badge
│   └── Button.cl.jac                 # Generic button component
└── .jac/                             # Managed directory (venv, client builds)
```

## API Endpoints

| Endpoint | Description |
|----------|-------------|
| `/walker/AddTodo` | Create a new todo (supports sub-todos via parent_id) |
| `/walker/ListTodos` | Retrieve all todos for the authenticated user |
| `/walker/ToggleTodo` | Toggle a todo's completed state |
| `/walker/DeleteTodo` | Delete a todo and its sub-todos |
| `/walker/GenerateShoppingList` | Generate AI ingredient list from a meal description |

## Configuration

The `jac.toml` file contains all project configuration. Key sections:
- `[project]` - Project metadata
- `[dependencies]` - Python dependencies
- `[dependencies.npm]` - NPM packages
- `[serve]` - Server configuration (base_route_app = "app")
- `[plugins.client]` - Jac-client and Tailwind CSS settings

## Troubleshooting

### Common Issues

1. **Missing API key**: Ensure `ANTHROPIC_API_KEY` is exported in your shell before running `jac start`
2. **Port already in use**: Change the port with `jac start main.jac --port 8001`
3. **Stale data after schema changes**: Delete `.jac/data/*.db*` files and restart
4. **npm install failures**: Ensure Node.js 18+ is installed and run `jac add` again
5. **Slow ingredient generation**: The AI call takes a few seconds; the UI shows a loading spinner while waiting

## Learn More

- [Jac Language Documentation](https://www.docs.jaseci.org/)
- [Jac Full-Stack Guide](https://www.docs.jaseci.org/reference/language/full-stack/)
