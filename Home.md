# Welcome to Sviter

**Sviter** is an AI-powered wiki where autonomous agents help you build and maintain knowledge — while you stay in control.

## The Problem

Working as a developer in a team, I noticed a broken communication layer. Our analytics team maintained documentation in tools like OneNote — documents with inconsistent styles, no strict structure, and terrible search. As developers, we avoided diving into those docs. The knowledge was there, but accessing it felt painful.

This gap between writers and developers creates friction. Writers don't know git. Developers don't want to wade through unstructured docs. Everyone loses.

Then I tried using Claude Code for a design-repo — markdown files, AI assistance, git history. It was a great experience for me as a developer. But I couldn't share it with the analytics team. Git is a barrier. The terminal is a barrier. It stayed local.

## The Solution

Sviter bridges this gap:

- **AI-powered search** — Chat finds what you need, no digging
- **Review before merge** — See exactly what changed, accept or reject
- **Real-time collaboration** — Work together like Notion or Google Docs
- **Version control** — Full history, branch, revert — git under the hood
- **Git hidden** — All the power, none of the complexity
- **Open source** — FSL-1.1 license (free for production use, no competing products for 2 years, then Apache 2.0)
- **Pluggable LLM** — Claude Agent SDK or OpenRouter out of the box, easy to add more

## How It Works

1. **Ask** — Chat with the AI about any topic in the wiki
2. **Request** — Ask the AI to make changes (spawns an autonomous thread)
3. **Review** — See exactly what changed in a visual diff
4. **Accept or Reject** — One click to merge or discard

All changes are tracked in git history, but you never have to touch git.

---

## Use Cases

A few examples of how Sviter can help:

- **Dev Teams** — Devs ask questions, writers update docs, git stays hidden
- **Book Authors** — Chapters as pages, AI checks consistency, full draft history
- **Research** — Connect ideas across notes, AI helps cross-reference
- **Second Brain** — Dump notes now, ask AI to organize later

---

## Quick Links

- [Getting Started](Getting-Started) — Set up and run Sviter
- [Tutorial](Tutorial) — Interactive walkthrough (learn by doing)
- [Concepts](Concepts) — Understand threads, branches, and the review workflow
- [User Guide](User-Guide) — Feature reference
- [Architecture](Architecture) — Technical deep dive
- [Development](Development) — Contributing & future vision
