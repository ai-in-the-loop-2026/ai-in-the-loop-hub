---
title: "Day 1 Setup (macOS)"
description: "Install VS Code, Git, and Python 3.13; accept the GitHub Classroom assignment; create a venv; commit and push."
date: 2025-12-30
categories: [Setup]
tags: [macos, vscode, git, github-classroom, python, venv, pip]
---

# Day 1 Setup Guide (macOS)
## Creating with AI in the Loop — macOS local setup (Homebrew required; no WSL)

This guide gets you to the same “ready for class” baseline as Windows:
- VS Code + Git + Python installed
- Clone a GitHub Classroom repo
- Create a `.venv` and install dependencies with `pip`
- Run a quick sanity check and **commit + push**

> **Course standard:** Python **3.13.x** (we’ll support/debug primarily on 3.13).

---

## 0) What you need
- macOS (recent version)
- Admin access for installs
- A GitHub account

---

## 1) Install Apple Command Line Tools (includes `git`)
Open **Terminal** and run:
```bash
xcode-select --install
```

Verify:
```bash
git --version
```

---

## 2) Install Homebrew
Run the official installer:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

If the installer prints a line that starts with `eval "$(...)"`, copy/paste it into Terminal (this adds Homebrew to your PATH).

Verify:
```bash
brew --version
```

---

## 3) Install Python 3.13.x via Homebrew

Install:
```bash
brew install python@3.13
```

Verify:
```bash
python3.13 --version
python3.13 -m pip --version
```

> If `python3.13` is not found, run:
> ```bash
> brew info python@3.13
> ```
> and follow the “caveats” it prints (Homebrew will tell you what to add to your PATH).

---

## 4) Install VS Code

### Option A (recommended): download from Microsoft
- Download: `https://code.visualstudio.com/download`
- Drag **Visual Studio Code.app** to **Applications**
- Open VS Code once

### Option B: Homebrew
```bash
brew install --cask visual-studio-code
```

---

## 5) Install VS Code extensions
In VS Code → Extensions:
- **Python** (Microsoft)

Optional:
- **GitHub Pull Requests and Issues** (GitHub)

### Enable the `code` command (recommended)
In VS Code:
- `Cmd+Shift+P` → **Shell Command: Install 'code' command in PATH**

Verify in Terminal:
```bash
code --version
```

---

## 6) Accept the GitHub Classroom assignment and clone the repo

### A) Accept
1. Click the Classroom invite link
2. Click **Accept assignment**
3. GitHub creates your repo and takes you to it

### B) Clone (Terminal)
Pick a folder (example):
```bash
cd ~/Documents
```

Clone (paste your repo URL):
```bash
git clone <PASTE-REPO-URL-HERE>
cd <REPO-FOLDER>
```

Open in VS Code:
```bash
code .
```

---

## 7) Create a virtual environment (`.venv`) and install dependencies

From the repo root:

```bash
python3.13 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

If your repo has `requirements.txt`:
```bash
pip install -r requirements.txt
```

Verify you’re using the venv Python:
```bash
which python
python --version
```

---

## 8) Sanity checks
```bash
python -c "print('Hello from Python!')"
```

If the repo has tests:
```bash
pytest -q
```

---

## 9) Make a change, commit, and push

```bash
git status
git add SUBMISSION.md
git commit -m "Complete submission"
git push
```

If autograding is enabled, you’ll see ✅/❌ on GitHub after pushing.

---

# Troubleshooting (common problems only)

## Homebrew: `brew: command not found`
Re-run the PATH line the installer printed (the `eval ...` line), then restart Terminal and try:
```bash
brew --version
```

## Python 3.13 not found (`python3.13: command not found`)
Run:
```bash
brew info python@3.13
```
and follow the “caveats” (it tells you exactly what to add to your PATH). Then open a new Terminal and retry:
```bash
python3.13 --version
```

## VS Code: `code: command not found`
In VS Code:
- `Cmd+Shift+P` → **Shell Command: Install 'code' command in PATH**
Restart Terminal.

## `git push` authentication failures
Make sure you accepted the assignment with the correct GitHub account. Retry `git push` and complete any browser/device login prompts.

---

## If you’re stuck, include these in your help request
```bash
git --version
python3.13 --version
which python
```
