---
title: "Initial Setup (macOS)"
description: "One-time installation of VS Code, Git, Python 3.13, and Homebrew on macOS."
date: 2025-12-30
categories: [Setup]
tags: [macos, vscode, git, python, homebrew, one-time]
---

# Initial Setup Guide (macOS)
## Creating with AI in the Loop — One-time macOS setup

This guide installs the core tools you need for the course. You only need to do this once.

> **Course standard:** Python **3.13.x** (we'll support/debug primarily on 3.13).

---

## What you need

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

### One-time Git identity setup
```bash
git config --global user.name "First Last"
git config --global user.email "you@school.edu"
git config --global --list
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
> and follow the "caveats" it prints (Homebrew will tell you what to add to your PATH).

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

In VS Code, go to Extensions:

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

## You're done with one-time setup!

For each assignment, follow the [GitHub Classroom Workflow Guide](github_classroom_workflow.md).

---

# Troubleshooting

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
and follow the "caveats" (it tells you exactly what to add to your PATH). Then open a new Terminal and retry:
```bash
python3.13 --version
```

## VS Code: `code: command not found`

In VS Code:

- `Cmd+Shift+P` → **Shell Command: Install 'code' command in PATH**
Restart Terminal.

---

## If you're stuck, include these in your help request
```bash
git --version
python3.13 --version
brew --version
```
