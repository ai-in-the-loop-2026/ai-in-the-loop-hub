---
title: "Initial Setup (Windows)"
description: "One-time installation of VS Code, Git, and Python 3.13 on Windows."
date: 2025-12-30
categories: [Setup]
tags: [windows, vscode, git, python, one-time]
---

# Initial Setup Guide (Windows)
## Creating with AI in the Loop — One-time Windows setup

This guide installs the core tools you need for the course. You only need to do this once.

> **Course standard:** Python **3.13.x** (we'll support/debug primarily on 3.13).
> Download: <https://www.python.org/downloads/>

---

## What you need

- Windows 10/11
- A GitHub account (the same one you'll use to accept GitHub Classroom assignments)

---

## 1) Install Visual Studio Code (VS Code)

### Download (official)

<https://code.visualstudio.com/download>

### Install
1. Run the installer.
2. Accept defaults unless you know you want something else.
3. **Recommended:** enable **"Add to PATH"**.

(Official Windows setup doc: <https://code.visualstudio.com/docs/setup/windows>)

### Verify
Open VS Code from the Start menu.

---

## 2) Install Git (Git for Windows)

### Download (official)

Use either official source:

- <https://git-scm.com/download/win>
- <https://gitforwindows.org/>

### Install
Accept defaults unless you know you need different settings.

### Verify
Open **PowerShell** and run:
```powershell
git --version
```

### One-time Git identity setup
```powershell
git config --global user.name "First Last"
git config --global user.email "you@school.edu"
git config --global --list
```

---

## 3) Install Python (course standard: 3.13.x)

### Download (official)

<https://www.python.org/downloads/>

### Install (important checkboxes)
When running the installer:
1. Check **"Add python.exe to PATH"**
2. Keep **pip** included (default)
3. Keep the **Python launcher** (`py`) enabled if offered (default)

### Verify
Close and reopen PowerShell, then run:
```powershell
python --version
py --version
pip --version
```

---

## 4) Install VS Code extensions

In VS Code, go to Extensions:

- **Python** (Microsoft)

Optional:

- **GitHub Pull Requests and Issues** (GitHub)

---

## You're done with one-time setup!

For each assignment, follow the [GitHub Classroom Workflow Guide](github_classroom_workflow.md).

---

# Troubleshooting

## Git not found in VS Code

- Install [Git for Windows](https://git-scm.com/download/win)
- Quit and restart VS Code
- Verify:
  ```powershell
  git --version
  ```

## `python` not recognized or opens Microsoft Store

- Install [Python 3.13.x](https://www.python.org/downloads/)
- Make sure **Add to PATH** is checked
- Restart PowerShell and verify:
  ```powershell
  python --version
  py --version
  ```

## PowerShell won't run scripts (execution policy)
Use **Command Prompt** terminal in VS Code instead, or (advanced) allow local scripts:
```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

---

## If you're stuck, include these in your help request
```powershell
git --version
python --version
py --version
```