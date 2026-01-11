# Threads: Collaborative Projects

Threads are **little projects** — spaces where people and AI work together to change the wiki.

## Two Modes of Interaction

| | Assistant | Thread |
|--|-----------|--------|
| Purpose | Explore, ask, understand | Collaborate, change |
| Participants | You + AI | You + others + AI |
| Edits wiki | No | Yes |
| Shared | No (personal) | Yes |

**Assistant** is for questions. Read-only. Personal exploration.

**Thread** is for changes. Collaborative. Shared workspace.

---

## Creating a Thread

User creates threads directly:

```
/thread auth-refactor @georg @lisa
```

This creates a shared space where participants discuss and work toward a change. The assistant might suggest creating a thread, but doesn't create it automatically — the decision stays with you.

---

## How Threads Work

A thread is a conversation that can produce changes:

1. **Discuss** — Participants talk through the problem
2. **AI participates** — But doesn't respond to every message
3. **Clarify** — AI asks questions when something is unclear
4. **Edit** — When the goal is clear, AI proposes changes
5. **Review** — Participants see the diff
6. **Apply** — When everyone agrees, changes go to main

No rigid state machine. The conversation flows naturally.

---

## AI as Participant

The AI doesn't dominate the conversation. A simple prompt guides this:

```
You are a participant in a collaborative thread.
Don't respond to every message.
Speak when:
- Directly addressed (@ai)
- You can clarify ambiguity
- Task is clear and you're ready to propose changes
- Asked a direct question

Otherwise, observe. Humans are discussing.
```

It:

- **Speaks when addressed** — "@ai what do you think?"
- **Speaks when useful** — To clarify ambiguity or propose action
- **Stays silent** — When humans are discussing among themselves
- **Asks questions** — When the goal isn't clear enough to act

```
georg: thinking we need to restructure the auth module
lisa: yeah the current flow is confusing
georg: what if we split login and registration?
lisa: makes sense

ai: I can split auth.md into separate login.md and registration.md pages.
    Should I preserve the current examples or simplify them?

georg: simplify
lisa: agreed

ai: [proposes changes]
```

The AI observes, waits for the right moment, then acts.

---

## Organic Approval

No buttons required. The AI reads consensus:

```
georg: looks good
lisa: 👍

ai: Both approved. Applying changes.
```

Or explicit:

```
lisa: @ai go ahead
ai: Applied. ✓
```

Reject is just... not approving. The thread stays open, discussion continues.

---

## Branches Under the Hood

Each thread works on an isolated git branch:

```
thread/<name>-<hash>
```

This means:
- Main content is never at risk
- Multiple threads can exist simultaneously
- Changes merge only when approved

But you don't need to think about git. The branch is just isolation — a safety net, not a workflow to manage.

---

## Notifications and Inbox

Your **inbox** is simply: threads that need your attention.

**You get notified when:**
- Added to a thread — `/thread feature @you`
- Mentioned — `@you what do you think?`
- AI asks you directly — `@you can you clarify X?`
- Thread is waiting on your input

No separate notification system. Your inbox is a filtered view of threads where you're a participant and something needs you.

```
┌─ Inbox ──────────────────────────┐
│                                  │
│ 🔴 auth-refactor                 │
│    @ai asked: "JWT or sessions?" │
│                                  │
│ 🔴 docs-update                   │
│    @lisa mentioned you           │
│                                  │
│ ○  dark-mode                     │
│    waiting for others            │
└──────────────────────────────────┘
```

---

## Thread History

Threads accumulate knowledge:
- Why decisions were made
- What was considered and rejected
- Who contributed what

This history can be preserved, searched, referenced. Future AI can learn from past threads.

---

## Summary

```
Questions  →  Assistant (explore)
Changes    →  Thread (collaborate)
```

Threads are where work happens. People discuss, AI helps, changes emerge from consensus. Simple.
