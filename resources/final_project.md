---
title: "Final Project Spec"
description: "Requirements, deliverables, and timeline for the final group project."
date: 2026-03-16
categories: [Course Logistics, Projects]
---

# Final Group Project

Your team will design and build a substantial AI application (or suite of related applications) using LangChain and LangGraph. The project should be related to your interests and do something genuinely useful — not just a toy demo.

## Teams

There are four project teams: three teams of three and one team of two. Your final project team is also your group-led discussion team.

## Technical Requirements

Your project must incorporate the following LangChain/LangGraph features:

- **Tools** — whether invoked by the LLM via `bind_tools` or called deterministically in a graph node
- **Conditional routing** — at least one use of `add_conditional_edges`
- **Custom state** — a `TypedDict` state that goes beyond `MessagesState` (additional fields that your workflow reads and writes)

Your application must have a **user interface** well-suited to the problem. Multiple interfaces are encouraged (e.g., a CLI built with Typer and a Streamlit web app), but at least one polished interface is required.

## Deliverables and Timeline

| Deliverable | Due | Weight |
|---|---|---|
| Proposal | Week 10 (Tue, before class) | — |
| Working prototype | Week 14 (Tue, before class) | — |
| Final repository | Week 15 | 5% |
| Presentation | Week 15 (Tue, April 30) | 5% |
| Portfolio piece (public site) | Week 15 | 5% |
| Group code review | Mon, May 4 (12:30–2:30pm) | 15% |

### Proposal

A 1–2 page markdown document in your team repo covering:

- **Problem / domain:** What problem are you solving, and for whom?
- **Planned features:** What will the application do? Be specific.
- **Technical approach:** What tools, RAG strategy, routing logic, and state fields do you plan to use?
- **Team member roles:** Who is responsible for what?
- **Rough timeline:** What do you plan to have done by when?

The instructor will review your proposal and provide feedback. You may be asked to adjust scope.

### Working Prototype

By Week 14, your core functionality should be working. Remaining features and polish are fine, but they should be clearly tracked as issues in your repo.

### Final Repository

A clean, well-organized private repo with:

- **README** — project description, setup instructions, how to run the application
- **Working code** — the application runs as described
- **`requirements.txt`** — all dependencies pinned
- **AI development log** — see [AI Development Log](#ai-development-log) below

### Presentation

Each team gives a presentation on Tuesday of Week 15 (April 30). Your presentation should include a live demo and slides covering what you built, your technical approach, challenges you encountered, and what you learned.

### Portfolio Piece

A **public** GitHub repository with a GitHub Pages site that summarizes your project for a general audience. This is a portfolio artifact — something you can show to future employers or graduate programs. It should include a clear project description, screenshots or screen recordings, and a summary of the technical approach. This public repo does not need to contain your working code or development history.

### Group Code Review

The group code review takes place during the scheduled final exam time: **Monday, May 4, 12:30–2:30pm** (~30 minutes per team). Format:

1. **Demo (~5 min):** Quick walkthrough of your application
2. **Q&A (~25 min):** The instructor asks questions about your project and code — architecture decisions, how specific features work, why you made certain choices, etc.

Questions may cover any part of the project, not just one feature. **Every team member must be able to explain every part of the code.** This is an individual assessment — you are evaluated on your understanding, not just the team's output.

## Two-Repo Model

Your project will use two repositories:

1. **Private working repo** (GitHub Classroom) — where you develop your code, track issues, maintain your AI development log, and collaborate with your team. This is the repo the instructor evaluates.
2. **Public portfolio repo** — a clean, public-facing repository with your GitHub Pages site. Create this toward the end of the project. It does not need to include your full development history or AI development log.

## AI Development Log

Maintain an AI development log (`ai_dev_log.md`) in your **private** working repo. This is an ongoing document — add entries as you work, not after the fact. Each entry should describe:

- What you were trying to accomplish
- How you used AI tools (prompts, suggestions, generated code)
- What worked, what didn't, and what you learned

The log helps you reflect on your AI-assisted development process and gives the instructor insight into how your project evolved.

## API Keys and Repo Hygiene

- **Never commit API keys, secrets, or credentials to your repo.** Store them in a `.env` file and make sure `.env` is in your `.gitignore`. If you accidentally commit a key, rotate it immediately.
- **Each team member should use their own API key.** Do not share API keys with your group members, even in private messages or shared documents.
- **Check `git status` before every commit.** Make sure you are not staging files that contain secrets, large data files, or other artifacts that don't belong in the repo.
- **Use `.gitignore` liberally.** At a minimum, ignore `.env`, `__pycache__/`, `.venv/`, and any local data files.

## Tips

- **Start early.** The proposal is due Week 10, and the semester moves fast from there.
- **Scope wisely.** A focused, polished application is better than an ambitious one that half-works. You can always list stretch goals in your proposal.
- **Commit often.** Small, frequent commits with clear messages make collaboration easier and give you a safety net.
- **Divide work, but understand all of it.** The code review evaluates individual understanding. Don't let any part of the codebase become a black box to you.
- **Test your application thoroughly** before the presentation and code review. Nothing undermines a demo like a crash.
