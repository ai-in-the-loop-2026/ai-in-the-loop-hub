# Release Checklist (Course Hub)
Creating with AI in the Loop — `_instructor/release-checklist.md`

Use this checklist any time you “release” a batch of updates to the public course hub (new week, new assignments, big policy change, etc.).

---

## 1) Content sanity (student-facing)
- [ ] **Schedule page updated** (`schedule.qmd`)
  - [ ] Week/date labels correct
  - [ ] Links to slides are correct
  - [ ] Assignment links (invite/spec) correct
- [ ] **Assignments index updated** (`assignments.qmd`)
  - [ ] Due dates and times correct (include timezone if helpful)
  - [ ] Submission rules correct (commit/push + cutoff behavior if used)
  - [ ] Autograding expectations stated (what students should run locally)
- [ ] **Syllabus + policies** (shared includes)
  - [ ] Policy bodies in `policies/_includes/` are up to date (no duplication in syllabus/policy pages).
  - [ ] Syllabus HTML shows embedded policies as **collapsible** sections.
  - [ ] Syllabus PDF export shows embedded policies **expanded** (no collapsed/hidden content).
  - [ ] Policy pages render correctly and match the syllabus-embedded versions.
  - [ ] **Resources updated**
  - [ ] Day 1 setup guides current (Windows/macOS)
  - [ ] Any new how-to docs added (autograding, asking for help)
  - [ ] Each resource has YAML front matter (`title`, `description`, `categories`, optional `date`, `tags`)
  - [ ] Draft-only resources marked `draft: true`

---

## 2) Link check (fast, pragmatic)
- [ ] Click all links you just added/changed:
  - [ ] Slide links
  - [ ] GitHub Classroom invite links
  - [ ] Any external docs/tools
- [ ] Confirm there are no “sandbox:” links or local-machine paths.

---

## 3) Secrets / privacy / licensing
- [ ] No secrets committed
  - [ ] `.env` not committed
  - [ ] no API keys in code blocks or screenshots
- [ ] No student-identifying info (names, grades, feedback)
- [ ] No copyrighted content you cannot redistribute
- [ ] If using images/figures: verify you have reuse rights or cite properly

---

## 4) Git hygiene (recommended)
- [ ] Pull latest `main` before changes
- [ ] Commit message is clear (e.g., `Week 03 updates`, `Post A2 prompt`, `Fix broken links`)
- [ ] If using PR workflow for the hub:
  - [ ] PR opened
  - [ ] Review complete (if required)
  - [ ] PR merged cleanly

---

## 5) Build and publish (Quarto)
- [ ] Local render succeeds:
  - `quarto render`
- [ ] Preview locally (optional but recommended):
  - `quarto preview`
- [ ] Publish to GitHub Pages:
  - `quarto publish gh-pages`
- [ ] Verify published site loads:
  - Home page
  - Schedule page
  - Resources listing
  - The newest slides

---

## 6) Post-release verification (2–3 minutes)
- [ ] Open the site from a private/incognito window (no cached assets)
- [ ] Confirm the newest changes appear
- [ ] Confirm the Resources auto-listing still works and filters correctly
- [ ] Confirm the “featured” Day 1 links still point to the right files

---

## 7) Optional: tag a release
If you want a permanent marker for “what students saw when Week X started,” tag it:
```bash
git tag -a week03-release -m "Week 03 hub release"
git push origin week03-release
```

---

## If something breaks
1. Reproduce locally with `quarto render`
2. Check for:
   - YAML front matter syntax errors
   - broken relative links (paths changed)
   - missing files referenced in `schedule.qmd`
3. If urgent, revert the last commit on `main` and re-publish.
