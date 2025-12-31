---
title: "GitHub Classroom Workflow"
description: "Accept an assignment, clone the repo, set up a virtual environment, and submit your work."
date: 2025-12-30
categories: [GitHub]
tags: [github-classroom, git, python, venv, pip, workflow]
---

# GitHub Classroom Workflow
## Creating with AI in the Loop — Assignment workflow (repeat for each assignment)

This guide covers the steps you'll follow for each GitHub Classroom assignment:

1. Accept the assignment and clone the repo
2. Create a virtual environment and install dependencies
3. Do the work
4. Commit and push (submit)

> **Prerequisite:** Complete the one-time setup first:
> [Initial Setup (Windows)](initial_setup_windows.md) | [Initial Setup (macOS)](initial_setup_macos.md)

---

## 1) Accept the GitHub Classroom assignment

1. Click the Classroom invite link (from the [Assignments page](../assignments.qmd)).
2. Click **Accept assignment**.
3. GitHub creates a repo for you and takes you to it.

---

## 2) Clone the repo

Copy the repo **HTTPS** URL from GitHub (click **Code** → **HTTPS**).

::: {.panel-tabset}

### Windows (VS Code)
1. In VS Code: `Ctrl+Shift+P` → `Git: Clone`
2. Paste the URL
3. Pick a folder
4. Open the repo when prompted

### Windows (Terminal)
```powershell
cd C:\Users\YourName\Documents
git clone <PASTE-REPO-URL-HERE>
cd <REPO-FOLDER>
code .
```

### macOS (Terminal)
```bash
cd ~/Documents
git clone <PASTE-REPO-URL-HERE>
cd <REPO-FOLDER>
code .
```

:::

---

## 3) Create a virtual environment and install dependencies

Open a terminal in VS Code: **Terminal → New Terminal**

::: {.panel-tabset}

### Windows (PowerShell)
```powershell
py -3.13 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### Windows (Command Prompt)
If PowerShell blocks the activation script:
```bat
py -3.13 -m venv .venv
.\.venv\Scripts\activate.bat
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### macOS
```bash
python3.13 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

:::

### Verify the venv is active

::: {.panel-tabset}

### Windows
```powershell
python --version
where python
```
The `where python` output should show a path inside `.venv`.

### macOS
```bash
python --version
which python
```
The `which python` output should show a path inside `.venv`.

:::

---

## 4) Sanity checks

If the repo has tests:
```bash
pytest -q
```

Or run a quick Python check:
```bash
python -c "print('Hello from Python!')"
```

---

## 5) Do the work

Complete the assignment according to the instructions in the repo's README.

---

## 6) Commit and push (submit)

Typical "submission" is **commit + push**. Autograding (if enabled) runs after you push.

::: {.panel-tabset}

### VS Code UI
1. Open the **Source Control** panel (left sidebar)
2. Stage changes (click `+` next to files)
3. Enter a commit message
4. Click **Commit**
5. Click **Sync Changes** (pushes to GitHub)

### Terminal
```bash
git status
git add .
git commit -m "Complete submission"
git push
```

:::

After pushing, check your repo on GitHub. If autograding is enabled, you'll see a ✅ or ❌ next to your commit.

---

# Troubleshooting

## `git push` permission/auth errors

- Make sure you accepted the assignment with the correct GitHub account
- Retry push and complete the browser sign-in flow if prompted
- Check that the repo URL matches your GitHub username

If issues persist, run these commands and include the output in your help request:

```bash
git remote -v
git config --global credential.helper
git config --show-origin --get-all credential.helper
```

## PowerShell won't activate `.venv` (execution policy)
Use **Command Prompt** instead:
```bat
.\.venv\Scripts\activate.bat
```
Or (advanced) allow local scripts in PowerShell:
```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

## `requirements.txt` not found
Not all assignments have a `requirements.txt`. Skip the `pip install -r requirements.txt` step if the file doesn't exist.

## Tests failing after push

- Read the error message in the GitHub Actions log
- Fix the issue locally
- Commit and push again

---

## Quick reference: common commands

| Task | Windows (PowerShell) | macOS |
|------|---------------------|-------|
| Create venv | `py -3.13 -m venv .venv` | `python3.13 -m venv .venv` |
| Activate venv | `.\.venv\Scripts\Activate.ps1` | `source .venv/bin/activate` |
| Deactivate venv | `deactivate` | `deactivate` |
| Install deps | `pip install -r requirements.txt` | `pip install -r requirements.txt` |
| Run tests | `pytest -q` | `pytest -q` |
| Commit all | `git add . && git commit -m "msg"` | `git add . && git commit -m "msg"` |
| Push | `git push` | `git push` |