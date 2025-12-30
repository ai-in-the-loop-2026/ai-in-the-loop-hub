# Creating with AI in the Loop — Course Hub (`ai-in-the-loop-hub`)

This repository is the **public course hub** for *Creating with AI in the Loop*.

It contains:
- syllabus, schedule, policies
- setup guides + FAQs
- Quarto slide sources and published HTML
- the assignment index (with GitHub Classroom invite links)

> **Student submissions do not go here.**  
> Graded work happens in **GitHub Classroom assignment repositories** (usually private).

---

## Quick links (when the site is published)
- Course site (GitHub Pages): `https://ai-in-the-loop-2026.github.io/ai-in-the-loop-hub/`
- Syllabus: `syllabus.qmd`
- Schedule: `schedule.qmd`
- Assignments index: `assignments.qmd`
- Resources: `resources/index.qmd`
- Policies: `policies/index.qmd`

---

## Repository structure

```
.
├─ _quarto.yml               # Quarto website config
├─ index.qmd                 # site home page
├─ schedule.qmd              # weekly schedule + links
├─ assignments.qmd           # canonical assignment index + invite links
├─ syllabus.qmd              # syllabus content (or link/embed PDF)
├─ policies/                 # student-facing policies
├─ resources/                # setup guides, FAQs, how-tos (auto-listed)
├─ slides/                   # Quarto RevealJS slide sources
└─ _instructor/              # staff-only docs (not published by Quarto)
```

### Important note about `_instructor/`
Quarto does not publish folders/files that start with `_`, so `_instructor/` stays out of the public website.

### Shared policy content (used by syllabus + policies)
Policy bodies are stored once in `policies/_includes/` and included into:
- `policies/*.qmd` (policy pages)
- `syllabus.qmd` (embedded policies, collapsible on the website and expanded in PDF)

---

## Editing workflow (recommended)

### Student-facing content
- Edit `.qmd` / `.md` files on `main`
- Keep `assignments.qmd` as the **single canonical place** for Classroom invite links and due dates
- Keep `schedule.qmd` as the **single canonical place** for week-by-week links to slides + assignments

### Staff-only notes
- Put internal process docs in `_instructor/`:
  - `authoring.md`
  - `publishing.md`
  - `release-checklist.md`

---

## Publishing the site (Quarto → GitHub Pages)

### One-time setup
1. Install Quarto: `https://quarto.org/docs/get-started/`
2. Ensure GitHub Pages is configured to serve from the `gh-pages` branch.

### Day-to-day publishing (manual)
From the repo root:

```bash
quarto render
quarto publish gh-pages
```

Publishing guidance and troubleshooting:
- `_instructor/publishing.md`

Release checklist:
- `_instructor/release-checklist.md`

---

## Guardrails for a public hub
✅ OK to include:
- assignment prompts (not solutions), rubrics without answers
- policies, setup guides, FAQs
- slide decks and demos
- links to GitHub Classroom assignments

❌ Do NOT include:
- solutions/answer keys/exams you plan to reuse
- student grades, feedback, or identifying info
- API keys or secrets (never commit `.env`)

---

## Contributing / permissions
This is a public repository, but only instructors/TAs with write access can merge changes.

If you are staff and need access, contact the repository owner (org: `ai-in-the-loop-2026`).

---

## License (optional)
If you want to explicitly allow reuse of *your* course materials, add a license (e.g., CC BY 4.0 for text/slides, MIT for code).
If you don’t add a license, default copyright applies.
