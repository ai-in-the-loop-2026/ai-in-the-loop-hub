# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the public course hub for "Creating with AI in the Loop" — a Quarto website hosted on GitHub Pages. It contains the syllabus, schedule, policies, setup guides, slide decks, and assignment links (but not student submissions or solutions).

## Common Commands

```bash
# Preview the site locally
quarto preview

# Render the full site
quarto render

# Publish to GitHub Pages (renders first if needed)
quarto publish gh-pages

# Render syllabus as PDF (policies expand fully in PDF)
quarto render syllabus.qmd --to pdf
```

## Architecture

### Content Structure
- `_quarto.yml` — website configuration (navbar, theme, render list)
- `index.qmd`, `schedule.qmd`, `assignments.qmd`, `syllabus.qmd` — main pages
- `policies/` — student-facing policy pages (use auto-listing via `policies/index.qmd`)
- `resources/` — setup guides and FAQs (use auto-listing via `resources/index.qmd`)
- `slides/` — Quarto RevealJS slide decks, named as `NN-topic-name.qmd`
- `_instructor/` — staff-only docs (Quarto ignores `_` prefixed directories)
- `_site/` — rendered output (gitignored)

### Shared Policy Content (DRY Pattern)
Policy text lives in `policies/_includes/*.md` (no YAML front matter). These files are included into:
- `policies/*.qmd` — for standalone policy pages
- `syllabus.qmd` — for embedded policies (collapsible in HTML, expanded in PDF)

Use `{{< include /policies/_includes/filename.md >}}` syntax. Keep include statements on their own line with blank lines around them.

### Canonical Link Philosophy
- `assignments.qmd` — single source for GitHub Classroom invite links and due dates
- `schedule.qmd` — single source for week-by-week links to slides and assignments
- Other pages should link to these rather than duplicating information

### Auto-Listing Requirements
Resources and policy pages need YAML front matter with `title`, `description`, and `categories` for the auto-listing to work properly. Recommended categories:
- Resources: `Setup`, `GitHub`, `Python`, `Quarto`, `Course Logistics`, `Reference`
- Policies: `Course Logistics`, `Academic Integrity`, `Projects`, `Accessibility`, `Classroom Norms`

Use `draft: true` in front matter to hide work-in-progress pages.

### Slide Naming Convention
Slides use topic-driven names (not "Week 1 Tue"): `01-course-overview-setup.qmd`, `02-model-apis-and-keys.qmd`, etc. The schedule provides the "when."

## Quarto Formatting Notes

- **Blank line before lists:** Quarto requires a blank line before bulleted/numbered lists to render them correctly.