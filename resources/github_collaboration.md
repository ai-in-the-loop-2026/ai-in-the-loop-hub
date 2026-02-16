---
title: "GitHub Collaboration Quickstart"
description: "How to use branches, pull requests, and merging to collaborate on a shared repo without stepping on each other's work."
date: 2026-02-16
categories: [GitHub]
tags: [github, git, branches, pull-requests, collaboration]
---

# GitHub Collaboration Quickstart

So far you've worked in your own repo: edit, commit, push to `main`. That works great solo, but when multiple people push directly to `main`, you'll quickly overwrite each other's work. This guide covers the workflow teams use to avoid that.

The short version: **work on a branch, open a pull request, then merge.**

---

## What is a branch?

A branch is a parallel copy of the code where you can make changes without affecting `main`. When your changes are ready, you merge them back into `main`.

```
main:        A --- B --- C --------- D (merge)
                          \         /
your-branch:               E --- F
```

Your teammates keep working on `main` (or their own branches) while you work on yours. Nobody steps on anyone else's work.

---

## The collaboration workflow

The key rules:

- **Always create a branch before making changes.** If you're on `main`, your only job is to pull. Never edit files while on `main`.
- **Each person works on their own branch.** Don't share branches — if two people need to work on related features, use two separate branches.

::: {.callout-note}
Your final project repo has branch protection enabled — pushing directly to `main` is blocked. All changes must go through a pull request. If you try to push to `main`, Git will reject it. Create a branch first (see [Troubleshooting](#troubleshooting) if you already started working on `main`).
:::

Here's the loop you'll repeat for each feature or fix:

### 1. Pull the latest changes

Before starting new work, make sure you have your team's latest code:

```bash
git pull
```

### 2. Create a branch

Make sure you're on `main` first (check the bottom-left of VS Code), then pick a short, descriptive name for what you're working on. Use hyphens instead of spaces:

```bash
git checkout -b add-export-feature
```

Here `add-export-feature` is the branch name — replace it with whatever you're working on (e.g., `fix-crash-on-empty-input`, `build-streamlit-ui`).

This creates a new branch and switches you to it. You're no longer on `main`.

To check which branch you're on at any time:

```bash
git branch
```

The active branch has a `*` next to it. You can also see your current branch in the **bottom-left corner of VS Code** at all times — get in the habit of glancing at it before you start editing.

### 3. Do your work and commit

Edit files, then commit as usual:

```bash
git add .
git commit -m "Add PDF export button to Streamlit app"
```

You can make multiple commits on your branch — that's normal.

### 4. Push your branch

The first time you push a new branch, use:

```bash
git push -u origin add-export-feature
```

After that first push, `git push` is enough for additional commits on the same branch.

### 5. Open a pull request

A pull request (PR) is how you propose merging your branch into `main`. It gives your teammates a chance to see what you changed before it goes in.

1. Go to your repo on GitHub. You'll often see a banner saying your branch was recently pushed — click **Compare & pull request**.
2. If you don't see the banner: click the **Pull requests** tab → **New pull request** → set "compare" to your branch.
3. Give the PR a title that summarizes the change.
4. Add a brief description of what you did and why.
5. Click **Create pull request**.

### 6. Review and merge

**Don't merge your own PRs.** Have a teammate look it over and merge it. They can see exactly what changed in the "Files changed" tab. This keeps everyone aware of what's happening in the codebase — which matters, since you'll all need to explain every part of the code at the group code review.

When it looks good, the teammate merges:

1. Click **Merge pull request**.
2. Click **Confirm merge**.
3. Click **Delete branch** — the work is safely in `main` now, so you don't need the branch anymore.

### 7. Pull `main` and clean up

Before starting your next piece of work, switch back to `main`, pull the latest changes, and delete your local copy of the merged branch:

```bash
git checkout main
git pull
git branch -d branch-name
```

The last command is optional — stale local branches are harmless — but it keeps things tidy.

You don't need to do this while you're in the middle of working on a branch — your branch is unaffected by changes to `main`. Just make sure to pull `main` before creating your next branch.

---

## Handling merge conflicts

A merge conflict happens when two people edit the same lines in the same file. Git doesn't know which version to keep, so it asks you to decide.

You'll usually encounter this on GitHub when merging a pull request. If there's a conflict, GitHub will block the merge and show a **Resolve conflicts** button.

Click it to open GitHub's conflict editor. You'll see markers like this:

```
<<<<<<< main
def process_query(query):
    return query.strip().lower()
=======
def process_query(query):
    return query.strip()
>>>>>>> add-export-feature
```

- The top section (`main`) is what's currently in `main`.
- The bottom section is what's on your branch.

**To resolve it:**

1. Edit the file in GitHub's editor to keep the version you want (or combine both). Delete all the marker lines — that's the `<<<<<<< main`, `=======`, and `>>>>>>> branch-name` lines.
2. Click **Mark as resolved**.
3. Once all conflicts are resolved, click **Commit merge**.

**Tips for avoiding conflicts:**

- **Pull often.** The longer you go without pulling, the more your branch drifts from `main`.
- **Work in different files when possible.** If one person is building the Streamlit UI and another is writing the LangGraph workflow, conflicts are rare.
- **Keep branches short-lived.** Merge a branch once its feature works — don't let branches live for weeks.

---

## Troubleshooting

### "I made changes on `main` by accident"

If you edited files on `main` but haven't committed yet, you can move your changes to a new branch:

```bash
git stash
git checkout -b my-new-branch
git stash pop
```

This saves your changes, creates a branch, and puts the changes back. Now commit as usual.

### "I committed to `main` by accident"

If you already committed to `main`, don't panic. You can move those commits to a branch. Replace `N` with the number of commits to move (e.g., `HEAD~1` for one commit, `HEAD~2` for two):

```bash
git branch my-new-branch
git reset HEAD~N
git checkout my-new-branch
```

This creates a branch with your commit, removes it from `main`, and switches you to the branch.

### "I created a branch from another branch instead of `main`"

Always create new branches from `main`. If you accidentally branched from a feature branch, you can start over:

```bash
git stash
git checkout main
git pull
git checkout -b my-new-branch
git stash pop
```

### "I pushed but my teammate doesn't see my changes"

Commits are local until you push. If you committed but forgot to push:

```bash
git push
```

If it's a new branch you haven't pushed before:

```bash
git push -u origin branch-name
```

---

## Quick reference

| Task | Command |
|---|---|
| Pull latest changes | `git pull` |
| Create and switch to a branch | `git checkout -b branch-name` |
| Switch to an existing branch | `git checkout branch-name` |
| See which branch you're on | `git branch` |
| Push a new branch | `git push -u origin branch-name` |
| Switch back to main | `git checkout main` |
