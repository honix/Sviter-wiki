# Welcome to Sviter

**Sviter** is an AI-powered wiki where autonomous agents help you build and maintain knowledge — while you stay in control.

## Motivation

As a developer, I've seen this problem firsthand. Our analytics team kept their documentation in a well-known wiki system with inconsistent styles, bloated with old irrelevant information, and nearly impossible to search or navigate efficiently. The knowledge was valuable, but accessing it felt like such a chore that we developers just avoided those docs altogether.

The root issue? Writers and developers speak different languages. Writers aren't comfortable with git, and developers don't want to wade through unstructured documentation. Meanwhile, we devs also want to document our own systems, and the analytics team frequently asks us for technical details — but the friction of the existing tools means it rarely happens. The result is that everyone loses.

I discovered a partial solution when I started using Claude Code for a personal design repo. The combination of markdown, AI assistance, and git history was perfect — I loved it. But I hit a wall when I tried to share it with my team. Git intimidated the non-developers. The command line scared them off. It stayed local on my machine.

So I built Sviter.

## The Solution

Sviter bridges this gap:

- **AI-powered search** — Chat finds what you need, no digging
- **Human in the loop** — Review all AI changes before they go live, accept or reject
- **Real-time collaboration** — Work together like Notion or Google Docs
- **Version control** — Full history, branch, revert — git under the hood
- **Git hidden** — All the power, none of the complexity
- **Open source** — FSL-1.1 license (free for production use, no competing products for 2 years, then Apache 2.0)
- **Pluggable LLM** — Claude Agent SDK or OpenRouter out of the box, easy to add more
- **On-demand data views** — AI generates custom React components from simple prompts to visualize CSV data with interactive views

## Agents

1. **Ask** — Chat with the AI assistant about any topic in the wiki
2. **Request** — Ask it to make changes — it spawns an autonomous agent
3. **Review** — Agent works on its own branch, you see the diff when it's done
4. **Accept or Reject** — One click to merge or discard

Agents do the work. You stay in control. Git handles history under the hood.

---

## Use Cases

A few examples of how Sviter can help:

- **Spec-Driven Development** — Write specs in wiki, AI keeps docs and code in sync
- **Dev Teams** — Devs ask questions, writers update docs, git stays hidden
- **Book Authors** — Chapters as pages, AI checks consistency, full draft history
- **Research** — Connect ideas across notes, AI helps cross-reference
- **Second Brain** — Dump notes now, ask AI to organize later

---

## Quick Links

- [Getting Started](Getting-Started.md) — Set up and run Sviter
- [Tutorial](Tutorial.md) — Interactive walkthrough (learn by doing)
- [Concepts](Concepts.md) — Understand threads, branches, and the review workflow
- [User Guide](User-Guide.md) — Feature reference
- [Architecture](Architecture.md) — Technical deep dive
- [Development](Development.md) — Contributing & future vision