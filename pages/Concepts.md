# Concepts

Understanding how Sviter works under the hood.

---

## Pages

A **page** is a file in the wiki. Pages can be organized in folders.

Sviter supports three page types:

- **Markdown** (`.md`) — Text, docs, notes
- **Data** (`.csv`) — Tables and structured data
- **View** (`.tsx`) — Custom React components (e.g., [kanban boards](agents/examples/kanban.tsx) example)
- and more to support in future

Every page is stored in git. No database, no metadata files — just files tracked by git.

When you edit a page, Sviter commits the change automatically.

---

## Users

Currently Sviter supports **guest users** — no login required to start.

**Planned:**

- User accounts and profiles
- @mentions so agents can notify specific users
- Agents asking users directly for domain knowledge

---

## Agents Folder

The `agents/` folder is the **command center** for AI behavior. Users can edit these files to customize how agents work.

**Planned:**

- Scheduler — run agents on a schedule
- Agent roles — different agents for different tasks (librarian, reviewer, etc.)

---

## The AI Assistant

The assistant lives in the right panel. It's **read-only** — it can search and read pages but cannot edit them directly.

**What it can do:**

- Search pages by name (`glob`)
- Search content (`grep`)
- Read full page content
- Answer questions about the wiki
- Spawn worker threads

**What it cannot do:**

- Edit pages directly
- Delete pages
- Make changes without your approval

---

## Worker Threads

When you ask the assistant to make changes, it spawns a **worker thread**.

A thread is an autonomous AI agent that:

1. Gets a **goal** (e.g., "Fix typos on this page")
2. Works on its own **git branch**
3. Has **write access** to pages
4. Reports back when done

### Thread Lifecycle

```
WORKING → NEED_HELP → REVIEW → ACCEPTED / REJECTED
```

- **WORKING**: Thread is actively making changes
- **NEED_HELP**: Thread is stuck and needs your input
- **REVIEW**: Thread is done, waiting for your approval
- **ACCEPTED**: Changes merged to main
- **REJECTED**: Branch deleted, no changes made

---

## Branches

Every thread works on an isolated **git branch**:

```
thread/<name>/<timestamp>
```

For example: `thread/fix-typos/1704067200`

This means:

- Your main content is **never at risk**
- Multiple threads can work simultaneously
- You review changes before they merge

When you **Accept**, the branch merges to main. When you **Reject**, the branch is deleted.

All this branch management is hidden — you just click Accept or Reject.

---

## The Review Workflow

1. You ask the assistant to make a change
2. Assistant spawns a thread with your request
3. Thread works on its own branch
4. When done, thread status becomes **REVIEW**
5. You see a diff of all changes
6. Click **Accept** or **Reject**
7. Done — changes merged or discarded

This workflow keeps humans in control while letting AI do the heavy lifting.

---

## Git Under the Hood

You never have to use git directly, but here's what happens:

| Action | Git Operation | |--------|--------------| | Edit a page | `git commit` on current branch | | Spawn thread | `git checkout -b thread/...` | | Thread edits | `git commit` on thread branch | | Accept | `git merge` to main | | Reject | `git branch -D` |

All history is preserved. You can always go back.

---

## Next

- [User Guide](User-Guide) — Detailed feature reference
- [Architecture](Architecture) — Technical implementation