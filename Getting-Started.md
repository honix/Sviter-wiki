# Getting Started

Get Sviter running in minutes.

## Prerequisites

- **Python 3.11+**
- **Node.js 18+**
- **Git**

## Installation

1. Clone the repository:
```bash
git clone https://github.com/honix/sviter.git
cd sviter
```

2. Initialize the wiki submodule:
```bash
git submodule update --init
```

3. Set up dependencies:
```bash
make setup
```

4. Configure your LLM provider. Copy the example config:
```bash
cp backend/.env.example backend/.env
```

Edit `backend/.env` and set your API key:
```
# For Claude Agent SDK (recommended)
# Works if Claude Code is already authorized on this machine
LLM_PROVIDER=claude
LLM_MODEL=claude-sonnet-4-5

# Or for OpenRouter
# LLM_PROVIDER=openrouter
# LLM_MODEL=x-ai/grok-4.1-fast
# OPENROUTER_API_KEY=your-key-here
```

## Running

Start both backend and frontend:
```bash
make run
```

- **Backend**: http://localhost:8000
- **Frontend**: http://localhost:5173

Open http://localhost:5173 in your browser.

## The Interface

Sviter has a 3-panel layout:

```
┌──────────────┬────────────────────────┬──────────────────┐
│              │                        │                  │
│  Page Tree   │    Page Content        │   Chat / Threads │
│              │                        │                  │
│  (Left)      │    (Center)            │   (Right)        │
│              │                        │                  │
└──────────────┴────────────────────────┴──────────────────┘
```

- **Left Panel**: Browse and organize wiki pages
- **Center Panel**: View and edit page content
- **Right Panel**: Chat with AI or manage threads

## Next Steps

- [Tutorial](Tutorial.md) — Learn by doing (interactive walkthrough)
- [Concepts](Concepts.md) — Understand how Sviter works
