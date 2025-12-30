# Welcome to Sviter

**Sviter** is an AI-powered wiki where autonomous agents help you build and maintain knowledge — while you stay in control.

## Motivation

I work as a developer in a team. Our analytics folks kept documentation in OneNote — messy styles, hard to search, hard to navigate. As devs, we avoided those docs. The knowledge was there, but getting to it felt like a chore.

Writers and developers speak different languages. Writers don't know git. Devs don't want to dig through unstructured docs. Everyone loses.

Then I tried Claude Code for a personal design-repo — markdown, AI, git history. Loved it. But I couldn't share it with my team. Git is scary for non-devs. The terminal is scary. It stayed local on my machine.

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