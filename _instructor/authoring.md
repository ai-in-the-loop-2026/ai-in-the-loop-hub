# Authoring Notes (Instructors/TAs)
Creating with AI in the Loop — `_instructor/authoring.md`

This file is **for instructors/TAs only**. It’s stored in the public repo for convenience, but it should **not** be linked from the course site navigation.

---

## 1) Repository mental model (what lives where)

### Public course hub repo (this repo)
Purpose: **dissemination**
- syllabus / schedule
- policies
- setup guides + FAQs
- Quarto slides (HTML)
- links to GitHub Classroom assignments

**Do not put**:
- solutions/answer keys/exams you plan to reuse
- anything student-identifying (names, grades, individualized feedback)
- API keys or secrets (`.env` must never be committed)
- copyrighted content you don’t have redistribution rights for

### GitHub Classroom assignment repos (student work)
Purpose: **submission + autograding**
- one repo per assignment (individual)
- one repo per project team (group)

Keep assignment specs in each assignment repo README *and* keep a canonical index of links in the hub (`assignments.qmd`).

---

## 2) Quarto website structure (recommended)

Typical layout:
```
.
├─ _quarto.yml
├─ index.qmd
├─ schedule.qmd
├─ syllabus.qmd
├─ assignments.qmd
├─ policies/
│  ├─ index.qmd
│  ├─ ai-use.qmd
│  ├─ collaboration.qmd
│  └─ late-work.qmd
├─ resources/
│  ├─ index.qmd
│  ├─ day1_setup_windows.md
│  ├─ day1_setup_macos.md
│  └─ faq.md
└─ slides/
   ├─ 01-course-overview-setup.qmd
   ├─ 02-model-apis-and-keys.qmd
   └─ ...
```

**Rules of thumb**
- `assignments.qmd` is the **single canonical place** for invite links + due dates.
- `schedule.qmd` is the **single canonical place** for week-by-week links to slides + assignments.
- Keep resource docs short and task-focused. Prefer one page per task.

---

## 3) Resources and policies auto-listing (metadata conventions)

The Resources page uses Quarto auto-listing. To make it useful, each file in `resources/` should include YAML front matter like:

```yaml
---
title: "Day 1 Setup (Windows)"
description: "Install VS Code, Git, Python 3.13; accept the Classroom assignment; create a venv; commit and push."
categories: Setup
date: 2025-12-30
tags: [windows, vscode, git, github-classroom, python, venv, pip]
---
```

### Recommended resource categories
Keep categories small and consistent. Suggested set:
- `Setup`
- `GitHub`
- `Python`
- `Quarto`
- `Course Logistics`
- `Reference`


(Keep drafts out of student navigation/assignments pages.)

The Policies section uses an auto-listing (`policies/index.qmd`). To keep it consistent with Resources and Slides, **every policy page** in `policies/` should include YAML front matter with:

- `title`
- `description`
- `categories` (1 broad bucket)

Example:

```yaml
---
title: "Late Work & Extensions"
description: "Deadlines, extension requests, and how GitHub Classroom cutoffs affect submissions."
categories: Course Logistics
---
```

### Recommended policy categories
Keep categories small and consistent. Suggested set:
- `Course Logistics`
- `Academic Integrity`
- `Projects`
- `Accessibility`
- `Classroom Norms`

### Drafts
To hide a resource or policy while you work on it:
```yaml
draft: true
```

---

## 4) Linking conventions

### Prefer relative links
- Within the site, use relative links:
  - `resources/day1_setup_windows.md`
  - `policies/ai-use.qmd`
  - `slides/01-course-overview-setup.html` (if you link rendered slides)
- Avoid hardcoding full URLs unless necessary.

### “Canonical link” philosophy
- Put the one true list of invite links in **Assignments**.
- Put the one true list of weekly links in **Schedule**.
- In other pages, link back to those rather than duplicating.

---

## 5) Slides (Quarto RevealJS)

### Storage and naming
Store slide sources in `slides/` and name consistently:
- `01-course-overview-setup.qmd`
- `02-model-apis-and-keys.qmd`
- `03-prompting-and-evaluation.qmd`

Titles should be **topic-driven** (avoid “Week 1 Tue” in titles). The schedule provides the “when.”

### Metadata: categories + tags (recommended)
Add `categories` and `tags` to each deck so students can browse by topic on `slides/index.qmd`.

Example:
```yaml
---
title: "Course Overview and Workflow Setup"
description: "What this course is, how we’ll work, and how to use GitHub Classroom + autograding."
date: 2026-01-13
categories: [Workflow]
tags: [github-classroom, setup, python]
repo-actions: false
format:
  revealjs:
    theme: simple
---
```

Keep **categories** to 1–2 broad buckets (stable vocabulary), and use **tags** for specific tools/ideas (reused across decks).

### Linking to slides
Prefer linking to the rendered slide HTML from `schedule.qmd` (best student experience).

## 6) Editing and release workflow

### Small changes
- Edit directly on `main` (if you’re solo) or via PR (if multiple staff).
- Re-render and publish (see `publishing.md`).

### Weekly release cadence (recommended)
- Batch updates once per week (e.g., Friday afternoon):
  - add next week’s slides
  - update schedule links
  - post the next assignment link
- Use the checklist in `release-checklist.md` before publishing.

---

## 7) Shared policy content (no duplication)

To avoid duplicating text between the syllabus and policy pages, we keep the **canonical policy bodies** in:

- `policies/_includes/*.md`

Then we **include** those bodies from:
- `policies/*.qmd` (student-facing policy pages)
- `syllabus.qmd` (embedded policies)

Example (policy page):

```md
{{< include /policies/_includes/ai-use.md >}}
```

Example (syllabus: collapsible in HTML, expanded in PDF):

```md
::: {.callout-note collapse="true" .content-visible when-format="html"}
## AI Use Policy (click to expand)
{{< include /policies/_includes/ai-use.md >}}
:::

::: {.callout-note .content-visible when-format="pdf"}
## AI Use Policy
{{< include /policies/_includes/ai-use.md >}}
:::
```

Notes:
- Included files in `policies/_includes/` should not contain YAML front matter.
- The `{{< include ... >}}` line should be on its own line with blank lines around it.

---

## 8) Publishing (quick reference)
Manual publish from your machine:
```bash
quarto render
quarto publish gh-pages
```

See `publishing.md` for the complete workflow and troubleshooting.

---

## 8) Guardrails for a public repo (practical)

### Prevent accidental changes to main
- Use a branch ruleset to protect `main` (require PRs/approvals if multiple staff).
- If solo, at least block force pushes and restrict deletions.

### Keep secrets out
- Maintain a strong `.gitignore` that includes `.env` and `.venv/`.
- If you must show example env vars, use `.env.example` (no secrets).

### Don’t accidentally publish instructor-only docs
- Don’t link `_instructor/` docs anywhere in the Quarto site.
- If you later add an auto-listing that crawls the whole repo, exclude `_instructor/`.

---

## 9) Optional: quality-of-life improvements (later)
- Add a GitHub Action that runs `quarto render` on pull requests.
- Add link-checking or spell-checking if you have time.

These are helpful but not required for a good first run.
