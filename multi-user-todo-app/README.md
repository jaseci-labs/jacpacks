# Multi-User Todo App

A full-stack Jac application demonstrating authenticated todo list management with hierarchical sub-todos and priority levels.

## Prerequisites

- **Jaclang**: Version 0.9.8 or higher
- **Node.js**: 18+ with npm for frontend dependencies

## Installation

### 1. View template info (optional)
```bash
jac jacpack info multi-user-todo-app.jacpack
```

### 2. Create a new project from this jacpack
```bash
jac create my-todo-app --use multi-user-todo-app.jacpack
cd my-todo-app
```

### 3. Install dependencies
```bash
jac add
```
This will install both Python and npm dependencies defined in `jac.toml`.

### 4. Start the application
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

### Modern UI
- Dark theme with orange accent palette
- CSS-driven styling with no inline styles
- Responsive card-based layout
- Priority color coding (red/yellow/green)

## Technical Architecture

- **Backend**: Jac walkers operating on a graph of Todo nodes
- **Frontend**: React-style Jac-Client components with CSS classes
- **Persistence**: Jac's built-in TieredMemory (SQLite-backed)
- **Auth**: Built-in jac-client authentication (signup/login/logout)

## Dependencies

### Python
- `jaclang` - Jac language runtime
- `jac-client` - Fullstack web framework

### NPM
- `jac-client-node` - Client-side runtime
- `tailwindcss` - CSS framework (configured in jac.toml)

## Project Structure

After creation, your project will have:
```
my-todo-app/
├── jac.toml              # Project configuration
├── main.jac              # Entry point with Todo nodes and walkers
├── frontend.cl.jac       # Client-side UI component (declarations)
├── frontend.impl.jac     # Client-side logic (implementations)
├── styles.css            # All application styles
├── components/           # Reusable UI components
│   ├── TodoItem.cl.jac   # Todo item with priority badge
│   ├── AuthForm.cl.jac   # Login/signup form
│   └── Button.cl.jac     # Generic button component
└── .jac/                 # Managed directory (venv, client builds)
```

## API Endpoints

| Endpoint | Description |
|----------|-------------|
| `/walker/AddTodo` | Create a new todo (supports sub-todos via parent_id) |
| `/walker/ListTodos` | Retrieve all todos for the authenticated user |
| `/walker/ToggleTodo` | Toggle a todo's completed state |
| `/walker/DeleteTodo` | Delete a todo and its sub-todos |

## Configuration

The `jac.toml` file contains all project configuration. Key sections:
- `[project]` - Project metadata
- `[dependencies]` - Python dependencies
- `[dependencies.npm]` - NPM packages
- `[serve]` - Server configuration (base_route_app = "app")
- `[plugins.client]` - Jac-client and Tailwind CSS settings

## Troubleshooting

### Common Issues

1. **Port already in use**: Change the port with `jac start main.jac --port 8001`
2. **Stale data after schema changes**: Delete `.jac/data/*.db*` files and restart
3. **npm install failures**: Ensure Node.js 18+ is installed and run `jac add` again

## Learn More

- [Jac Language Documentation](https://www.docs.jaseci.org/)
- [Jac Full-Stack Guide](https://www.docs.jaseci.org/reference/language/full-stack/)
