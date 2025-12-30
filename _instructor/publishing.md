# Publishing the Course Hub (Quarto + GitHub Pages)
Creating with AI in the Loop — `_instructor/publishing.md`

This document explains how to publish the **public course hub** as a Quarto website hosted on **GitHub Pages**.

Assumptions:
- Your hub repo is public (e.g., `ai-in-the-loop`).
- The repo is a Quarto website project (has `_quarto.yml`).
- You publish HTML output to a `gh-pages` branch.

---

## 1) One-time setup (GitHub Pages)
### A) Confirm Pages is enabled
In the GitHub repo:
- **Settings → Pages**

Recommended configuration:
- **Source:** `Deploy from a branch`
- **Branch:** `gh-pages` (root)

If `gh-pages` does not exist yet, it will appear after your first publish.

GitHub Pages docs: https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages

### B) Choose your site URL / base path
Your site URL will typically be:
- `https://<org>.github.io/<repo>/`

Quarto handles the correct base path automatically when using `quarto publish gh-pages`, but if you ever see broken links, check:
- `_quarto.yml` and site root links
- relative links inside `.qmd`/`.md` files

---

## 2) Local prerequisites (your machine)
Install Quarto:
- https://quarto.org/docs/get-started/

Verify:
```bash
quarto --version
```

---

## 3) Day-to-day publishing workflow (manual publish)
### Step 1: Pull latest changes
```bash
git checkout main
git pull
```

### Step 2: Render the site locally
```bash
quarto render
```

Output goes to `_site/` (or whatever you set as `output-dir`).

### Step 3: Publish to GitHub Pages
```bash
quarto publish gh-pages
```

What this does (high level):
- renders (if needed)
- creates/updates a `gh-pages` branch containing the rendered site
- pushes that branch to GitHub

Quarto GitHub Pages publishing: https://quarto.org/docs/publishing/github-pages.html

---

## 4) Publishing slides (RevealJS) from this repo
Recommended approach:
- Store slide sources in `slides/` as `.qmd`
- Render them as HTML (RevealJS)
- Link to the rendered slide HTML from `schedule.qmd`

If you keep slides in the same Quarto website project, `quarto render` will build them alongside the site.

---

## 5) Exporting the syllabus to PDF (expanded policies)

The syllabus embeds some policies using shared includes from `policies/_includes/`.
In HTML they appear in collapsible sections; in PDF they should be **fully expanded**.

Render just the syllabus PDF:
```bash
quarto render syllabus.qmd --to pdf
```

After rendering, open the PDF and verify:
- embedded policy sections are present and fully expanded
- headings and page breaks look reasonable

---

## 6) What to publish vs keep private
**Safe for public hub**
- syllabus, schedule, assignment prompts (not solutions)
- policies
- setup guides, FAQs
- slide decks

**Keep private**
- solutions/answer keys/exams you will reuse
- anything with student identifiers or grades
- API keys or secrets

---

## 7) Troubleshooting common publishing issues

### A) “Site updated but I don’t see changes”
- Hard refresh in browser (`Ctrl+F5`)
- Try incognito/private window
- Confirm you published (`quarto publish gh-pages`) after committing changes

### B) Broken links (404) after publishing
Common causes:
- A file was renamed/moved, but links weren’t updated.
- Using absolute links incorrectly.

Fixes:
- Prefer **relative links** in Quarto (`resources/day1_setup_windows.md`, `policies/ai-use.qmd`, etc.)
- Re-run `quarto render` and click the link locally in the preview.

### C) YAML front matter errors stop the build
Symptoms:
- `quarto render` fails with a YAML parse error.

Fix:
- Check the file mentioned in the error.
- Ensure YAML uses correct indentation and colon spacing.
- Quotes help if you have special characters in titles.

### D) `gh-pages` branch exists but Pages isn’t serving it
- Repo **Settings → Pages**: confirm branch is `gh-pages` and folder is `/ (root)`.
- Wait a minute and refresh (Pages can take a short moment to update).

---

## 7) Optional: adopt a PR-based workflow later
Once the term ramps up, you might prefer:
- changes via PRs
- branch ruleset protecting `main`
- (optional) a GitHub Action that runs `quarto render` on PRs

This is optional; manual publish is perfectly fine and usually simpler for the first run.
