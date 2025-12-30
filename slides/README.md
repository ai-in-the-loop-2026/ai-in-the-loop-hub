# Slides (Quarto RevealJS)

This folder contains **Quarto RevealJS** slide sources (`.qmd`).

Students access slides through:
1. the course website (rendered HTML), linked from `schedule.qmd`, and/or
2. the Slides index page (`slides/index.qmd`), which auto-lists decks by metadata.

---

## Naming convention
Use **numbered filenames** so decks sort naturally:

- `01-course-overview-setup.qmd`
- `02-model-apis-and-keys.qmd`
- `03-prompting-and-evaluation.qmd`

> Slide **titles** should be **topic-driven** (avoid “Week 1 Tue” in the title).  
> The filename + schedule provides the “when”.

---

## Slide metadata (categories + tags)
We use **categories** and **tags** so students can browse slides by topic on `slides/index.qmd`.

### Recommended practice
- **categories:** 1–2 broad buckets (kept consistent across the term)
- **tags:** several specific keywords (free-form, but try to reuse terms)

### Suggested category vocabulary
Keep this small and stable:
- `Workflow`
- `Model APIs`
- `Prompting`
- `Evaluation`
- `Tool Use`
- `RAG`
- `Agents`
- `Engineering`
- `Ethics`
- `Project`

Example tags (more specific):
- `gemini`, `langchain`, `langgraph`, `pytest`, `github-classroom`, `autograding`,
  `structured-outputs`, `embeddings`, `observability`, `costs`, `safety`

---

## Starter YAML front matter (copy/paste)
At minimum, include:

```yaml
---
title: "Topic-driven title"
description: "One sentence students will see in the slides listing."
date: 2026-01-13
categories: [Workflow]
tags: [github-classroom, setup, python]
# Optional: hide repo links on decks for a cleaner slide experience
repo-actions: false
format:
  revealjs:
    theme: simple
    slide-number: true
---
```

> Tip: Keep `date` accurate—your slides index sorts newest-first by date.

---

## Rendering / publishing
From the repo root:

```bash
quarto render
quarto publish gh-pages
```

Rendered HTML for slides will typically appear under the site as:
- `slides/<deck-name>.html`

---

## Images and assets
If a deck needs images, store them under `slides/assets/` (or per-deck subfolders) and use relative paths.

---

## Keep sensitive content out
Avoid including solutions or private notes in a public repo. If you need instructor-only notes, keep them in a private repo or in `_instructor/` (but remember `_instructor/` is still visible in the public GitHub repo).
