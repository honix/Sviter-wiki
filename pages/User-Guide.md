# User Guide

Complete reference for all Sviter features.

---

## Page Management

### Creating Pages

1. Right-click in the page tree (left panel)
2. Select **New Page**
3. Enter the page name
4. Start writing

Or create via chat: `Create a new page called "Meeting Notes"`

### Editing Pages

- Click a page to view it
- Press `Ctrl+E` or click **Edit** to enter edit mode
- Press `Escape` or click **Save** to exit

### Organizing Pages

- **Folders**: Right-click → New Folder
- **Move**: Drag and drop pages between folders
- **Rename**: Right-click → Rename
- **Delete**: Right-click → Delete

### Page Types

Sviter supports:
- `.md` — Markdown (default)
- `.csv` — Spreadsheet data
- `.tsx` — React components (advanced)

---

## Chat Interface

### Asking Questions

Type in the chat input and press Enter. The assistant can:

- Answer questions about wiki content
- Find specific information
- Summarize pages
- Compare content across pages

**Examples:**
- `What do we know about Project X?`
- `Find all pages mentioning "API"`
- `Summarize the Architecture page`

### Adding Context

1. Select text on any page
2. Click **Add to Chat** (appears on selection)
3. The selected text is sent as context
4. Your next message can reference it

This helps the assistant understand exactly what you're asking about.

---

## Working with Threads

### Spawning a Thread

Ask the assistant to make changes:

- `Fix the typos on this page`
- `Add a section about deployment`
- `Reorganize this content into bullet points`

The assistant spawns a worker thread automatically.

### Viewing Threads

Switch to the **Threads** tab in the right panel.

Each thread shows:
- **Name**: What it's working on
- **Status**: WORKING, NEED_HELP, or REVIEW
- **Branch**: The git branch name

### Reviewing Changes

1. Click a thread with status **REVIEW**
2. Center panel shows the diff view
3. Red lines = removed, Green lines = added
4. Scroll through all changes

### Accepting or Rejecting

At the bottom of the review:

- **Accept**: Merge changes to main branch
- **Reject**: Delete the branch, discard changes

After accepting, the page updates automatically.

### Helping a Stuck Thread

If a thread shows **NEED_HELP**:

1. Click the thread
2. Read what it's asking
3. Reply in the thread chat
4. Thread continues working

---

## Branch Management

For advanced users who want direct branch control.

### Viewing Branches

Click the branch selector (top of center panel).

Shows:
- Current branch (bold)
- All available branches
- Thread branches (prefixed with `thread/`)

### Switching Branches

Click any branch to switch. The page tree updates to show content on that branch.

### Creating Branches

Click **+ New Branch** in the branch selector.

Useful for:
- Manual experiments
- Grouping related changes
- Working without AI

### Deleting Branches

Right-click a branch → Delete.

Cannot delete:
- The `main` branch
- The currently checked-out branch

---

## Collaborative Editing

Multiple users can edit the same page simultaneously.

### How It Works

- Changes sync in real-time via WebSocket
- See other users' cursors (when available)
- No conflicts — changes merge automatically

### Merge Blocking

When users are actively editing a page:
- Thread merges are blocked
- Prevents conflicts with live edits
- Merges resume when editing stops

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+E` | Toggle edit mode |
| `Escape` | Exit edit mode |
| `Ctrl+S` | Save (in edit mode) |
| `Ctrl+/` | Focus chat input |

---

## Next

- [Architecture](Architecture) — How it's built
- [Development](Development) — Contributing
