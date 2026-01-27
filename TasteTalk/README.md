# TasteTalk

A restaurant feedback management system built entirely in Jac. This jacpack provides an AI-powered platform for collecting, analyzing, and responding to customer feedback with actionable insights for restaurant management.

## Prerequisites

- **Jaclang**: Version 0.9.0 or higher
- **Node.js**: 18+ with npm for frontend dependencies
- **Google Gemini API Key**: Required for AI-powered analysis and responses

## Installation

### 1. View template info (optional)

```bash
jac jacpack info TasteTalk.jacpack
```

### 2. Create a new project from this jacpack

```bash
jac create my-tastetalk-app --use TasteTalk.jacpack
cd my-tastetalk-app
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
```

### 5. Start the application

```bash
jac start main.jac
```

The application will be available at `http://localhost:8000`.

## Features

### Customer Portal
- Submit dining or delivery feedback
- Receive instant, personalized AI-generated responses
- Multi-language support (Sinhala/Tamil)

### Admin Dashboard
- Filter data by timeframe (3, 7, or 30 days)
- View sentiment distribution charts (positive/negative/neutral)
- Track feedback across categories: Food Quality, Delivery, Pricing, Other
- Generate AI summaries of customer feedback
- Receive AI-powered improvement recommendations

## Technical Architecture

- **Backend**: Jac-Scale graph database for storing feedback with relationship mapping
- **LLM**: Google Gemini 2.5 Flash for analysis and response generation
- **Frontend**: React-based Jac-Client with Recharts visualization
- **Persistence**: Jac's built-in TieredMemory (SQLite-backed)

## Dependencies

### Python
- `jaclang` - Jac language runtime
- `jac-client` - Fullstack web framework
- `byllm` - LLM integration plugin

### NPM
- `recharts` - Data visualization
- UI components for the admin dashboard

## Project Structure

After creation, your project will have:

```
my-tastetalk-app/
├── jac.toml              # Project configuration
├── main.jac              # Main application entry
├── endpoints.sv.jac      # Backend API endpoints
├── frontend.cl.jac       # Client-side UI logic
├── utils.jac             # Utility functions
├── components/           # Reusable UI components
└── assets/               # Static assets (images, CSS)
```

## API Endpoints

| Endpoint | Description |
|----------|-------------|
| `/walker/submit_feedback` | Submit customer feedback |
| `/walker/get_feedback` | Retrieve feedback entries |
| `/walker/get_sentiment_stats` | Get sentiment distribution |
| `/walker/get_category_stats` | Get category breakdown |
| `/walker/generate_summary` | AI-generated feedback summary |
| `/walker/get_recommendations` | AI-powered improvement suggestions |

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
2. **Port already in use**: Change the port with `jac start main.jac --port 8001`
3. **Stale data after schema changes**: Delete `.jac/data/*.db*` files and restart

## Learn More

- [Jac Language Documentation](https://www.docs.jaseci.org/)
- [TasteTalk Source Repository](https://github.com/SahanUday/TasteTalk)
