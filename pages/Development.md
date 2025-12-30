# Development

Contributing to Sviter and future plans.

---

## Contributing

### Setup for Development

1. Fork the repository
2. Clone your fork
3. Install dependencies: `make setup`
4. Run in dev mode: `make run`

### Project Structure

```
sviter/
├── backend/
│   ├── main.py              # FastAPI entry point
│   ├── ai/
│   │   ├── adapters/        # LLM providers
│   │   ├── tools.py         # Wiki tools
│   │   └── prompts.py       # System prompts
│   ├── storage/             # GitWiki class
│   ├── threads/             # Thread system
│   └── api/                 # REST + WebSocket
│
├── frontend/
│   ├── src/
│   │   ├── components/      # React components
│   │   ├── contexts/        # State management
│   │   ├── services/        # API + WebSocket
│   │   └── hooks/           # Custom hooks
│   └── package.json
│
└── Sviter-wiki/             # Wiki content (submodule)
```

### Code Style

**Backend (Python):**
- Type hints required
- Black formatting
- Async/await for I/O

**Frontend (TypeScript):**
- Strict TypeScript
- Functional components
- TailwindCSS for styling

### Submitting Changes

1. Create a feature branch
2. Make your changes
3. Test locally
4. Submit a pull request

---

## Running Tests

```bash
# Backend tests
make test-backend

# Frontend tests
make test-frontend
```

---

## API Reference

### Adding New Tools

Tools are defined in `backend/ai/tools.py`:

```python
@tool
def my_new_tool(param: str) -> str:
    """Description for the LLM."""
    # Implementation
    return result
```

Register in `ToolBuilder`:

```python
builder.add_tool(my_new_tool)
```

### Adding LLM Providers

Create adapter in `backend/ai/adapters/`:

```python
class MyAdapter:
    async def chat(self, messages, tools):
        # Call your LLM
        return response
```

---

## Future Vision

Ideas we're exploring for future development.

### Librarian Agent

An autonomous agent that:
- Scans the wiki periodically
- Identifies structural issues
- Spawns worker threads to fix them
- Suggests reorganization
- Maintains consistency

Example: The librarian notices orphaned pages, duplicate content, or outdated information — and spawns threads to address each issue.

### Enhanced Collaboration

- User presence indicators
- Comment threads on pages
- Suggested edits (like Google Docs)
- Notification system

### Plugin System

- Custom tools for specific domains
- Integrations with external services
- Custom page types

### Multi-Wiki Support

- Multiple wiki instances
- Cross-wiki search
- Shared agent pool

---

## Roadmap

See the [GitHub Project](https://github.com/honix/sviter/projects) for current roadmap and planned features.

---

## Links

- **Repository**: https://github.com/honix/sviter
- **Issues**: https://github.com/honix/sviter/issues
- **Discussions**: https://github.com/honix/sviter/discussions
