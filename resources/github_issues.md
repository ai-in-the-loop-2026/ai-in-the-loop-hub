---
title: "GitHub Issues Quickstart"
description: "How to use GitHub Issues to track bugs, remaining features, and to-dos in your repo."
date: 2026-02-16
categories: [GitHub]
tags: [github, issues, project-management]
---

# GitHub Issues Quickstart

GitHub Issues are lightweight to-do items attached to your repository. Each issue has a title and a description — think of them as sticky notes for your project that your whole team (and the instructor) can see.

You'll use issues in your final project to track remaining features and known bugs, especially around the [prototype checkpoint](final_project.md#working-prototype).

---

## Creating an issue

1. Go to your repo on GitHub.
2. Click the **Issues** tab (near the top of the page, next to **Code**).
3. Click **New issue**.
4. Give it a short, descriptive **title** (e.g., "Add error handling for invalid API responses").
5. In the description, add any helpful details — what the feature should do, steps to reproduce a bug, etc.
6. Click **Submit new issue**.

That's it. GitHub assigns it a number (e.g., `#1`, `#2`) that you can reference elsewhere.

---

## Closing an issue

When the work is done, you have two options:

### Option 1: Close it manually

Open the issue on GitHub and click **Close issue** at the bottom.

### Option 2: Close it from a commit message

Include a keyword and the issue number in your commit message:

```bash
git commit -m "Add input validation — fixes #3"
```

When you push that commit, GitHub automatically closes issue `#3`. Any of these keywords work: `fixes`, `closes`, `resolves` (case-insensitive).

---

## What makes a good issue?

Keep it simple. A good issue has:

- **A clear title** — someone should understand the task from the title alone
- **Enough context** — a sentence or two about what needs to happen or what's broken

Examples:

| Title | Description |
|---|---|
| Add retry logic for API timeouts | Right now a timeout crashes the app. Should retry up to 3 times before showing an error. |
| Fix crash when user enters empty query | Entering an empty string in the Streamlit input causes a KeyError in `process_query()`. |
| Build "export to PDF" feature | Users should be able to export the summary as a PDF from the Streamlit interface. |

---

## Tips

- **One issue per task.** Don't lump multiple features into a single issue.
- **Create issues as you go.** When you notice a bug or think of a feature, open an issue right away so you don't forget.
- **Reference issues in commits.** Even if you don't auto-close them, mentioning `#5` in a commit message creates a link between the commit and the issue, making it easy to trace what changed and why.
