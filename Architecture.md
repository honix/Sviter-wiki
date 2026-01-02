# Architecture

Technical deep dive into how Sviter is built.

---

## Overview

```
┌─────────────────────────────────────────────────────────────┐
│                        Frontend                             │
│  React 19 + TypeScript + Vite + TailwindCSS + Shadcn UI     │
└─────────────────────────────────────────────────────────────┘
                              │
                    WebSocket + REST API
                              │
┌─────────────────────────────────────────────────────────────┐
│                        Backend                              │
│  FastAPI + WebSocket + GitPython + LLM Adapters             │
└─────────────────────────────────────────────────────────────┘
                              │
              ┌───────────────┴───────────────┐
              │                               │
       ┌──────┴──────┐                 ┌──────┴──────┐
       │  Git Repo   │                 │   SQLite    │
       │  (Wiki)     │                 │  (Threads)  │
       └─────────────┘                 └─────────────┘
```

---

## Backend

### Framework

- **FastAPI**: Modern Python web framework
- **Uvicorn**: ASGI server with hot reload
- **WebSockets**: Real-time bidirectional communication

### Storage

**Wiki Content**: Pure git repository (`Sviter-wiki/` submodule)
- No database for content
- Full history via git
- Branches for thread isolation

**Thread Metadata**: SQLite database
- Thread status, messages, ownership
- User sessions
- Faster than git for queries

### AI Integration

Pluggable LLM adapters:

```
ai/adapters/
├── claude_adapter.py    # Claude SDK (Anthropic)
└── openrouter_adapter.py # OpenRouter API
```

Configure in `.env`:
```
LLM_PROVIDER=claude
LLM_MODEL=claude-sonnet-4-5
```

### Tool System

Composable tools for AI agents:

| Tool | Description | Access |
|------|-------------|--------|
| `read_page` | Read page content | Assistant, Worker |
| `write_page` | Create/overwrite page | Worker only |
| `edit_page` | Edit specific lines | Worker only |
| `grep_pages` | Search content | Assistant, Worker |
| `glob_pages` | Find pages by pattern | Assistant, Worker |
| `list_pages` | List all pages | Assistant, Worker |
| `spawn_thread` | Create worker thread | Assistant only |

### Thread Execution

```python
# Simplified flow
async def run_thread(thread_id, goal):
    branch = f"thread/{name}/{timestamp}"
    git.checkout(branch, create=True)

    while not done:
        response = await llm.chat(messages, tools)
        execute_tools(response)

    thread.status = "REVIEW"
```

---

## Frontend

### Stack

- **React 19**: UI framework
- **TypeScript**: Type safety
- **Vite**: Fast dev server and bundler
- **TailwindCSS 3.4**: Utility-first styling
- **Shadcn UI**: Component library

### Key Libraries

| Library | Purpose |
|---------|---------|
| `@radix-ui/*` | Accessible UI primitives |
| `codemirror` | Code/markdown editor |
| `yjs` | Real-time collaboration |
| `lucide-react` | Icons |
| `use-stick-to-bottom` | Chat auto-scroll |
| `react-resizable-panels` | Panel layout |

### State Management

React Context with useReducer:

```typescript
interface AppState {
  rightPanelMode: 'chat' | 'threads';
  centerPanelMode: 'page' | 'thread-review';
  selectedThread: Thread | null;
  currentPage: string | null;
  // ...
}
```

No routing library — context-based navigation.

### WebSocket Messages

Real-time sync between frontend and backend:

| Message | Direction | Purpose |
|---------|-----------|---------|
| `assistant_message` | Server → Client | AI response chunk |
| `tool_call` | Server → Client | Tool being executed |
| `thread_created` | Server → Client | New thread spawned |
| `thread_updated` | Server → Client | Thread status change |
| `page_updated` | Server → Client | Page content changed |
| `user_message` | Client → Server | User chat input |

---

## Git Operations

### Branch Strategy

```
main                    # Production content
thread/fix-typos/123    # Worker thread branch
thread/add-docs/456     # Another thread
```

### Worktrees

Threads use git worktrees for isolation:

```bash
git worktree add /tmp/thread-123 -b thread/name/123
# Thread works in /tmp/thread-123
# Main checkout unchanged
```

### Merge Process

```python
def accept_thread(thread):
    git.checkout("main")
    git.merge(thread.branch)
    git.branch("-D", thread.branch)
    cleanup_worktree(thread)
```

---

## Real-time Collaboration

### User Interaction

Multiple users can work on the same page simultaneously:
- Edits sync instantly across all connected users
- No conflicts — changes merge automatically via CRDT
- Users see each other's changes as they type

### Yjs Integration

- **Yjs**: CRDT-based collaboration framework
- **y-websocket**: WebSocket sync provider
- **pycrdt**: Python Yjs implementation

### Merge Blocking

When users are actively editing:

```python
if active_editors_on_page(page):
    raise MergeBlockedError("Users are editing this page")
```

Prevents conflicts between live edits and thread merges.

---

## API Endpoints

### REST

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/api/pages` | GET | List all pages |
| `/api/pages/{path}` | GET | Read page |
| `/api/pages/{path}` | PUT | Update page |
| `/api/pages/{path}` | DELETE | Delete page |
| `/api/git/branches` | GET | List branches |
| `/api/git/checkout` | POST | Switch branch |
| `/api/threads` | GET | List threads |
| `/api/threads/{id}/accept` | POST | Accept thread |
| `/api/threads/{id}/reject` | POST | Reject thread |

### WebSocket

```
ws://localhost:8000/ws/{client_id}
```

Handles:
- Chat messages
- Thread updates
- Page sync
- Collaborative editing

---

## Next

- [Beyond](Beyond.md) — Vision of Sviter as an Information Operating System
- [Development](Development.md) — Contributing guide
