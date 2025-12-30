---
title: "Day 1 Setup (Windows)"
description: "Install VS Code, Git, and Python 3.13; accept the GitHub Classroom assignment; create a venv; commit and push."
date: 2025-12-30
categories: [Setup]
tags: [Windows, VS Code, Git, Python, venv]
---

# Day 1 Setup Guide (Windows)
## Creating with AI in the Loop — Windows local setup (no WSL)

This guide gets you to the “ready for class” baseline:
- VS Code + Git + Python installed
- Clone a GitHub Classroom repo
- Create a `.venv` and install dependencies with `pip`
- Run a quick sanity check and **commit + push** (what “submission” usually looks like)

> **Course standard:** Python **3.13.x** (we’ll support/debug primarily on 3.13).  
> Download: `https://www.python.org/downloads/latest/python3.13/`

---

## 0) What you need
- Windows 10/11
- A GitHub account (the same one you’ll use to accept GitHub Classroom assignments)

---

## 1) Install Visual Studio Code (VS Code)

### Download (official)
`https://code.visualstudio.com/download`

### Install
1. Run the installer.
2. Accept defaults unless you know you want something else.
3. **Recommended:** enable **“Add to PATH”**.

(Official Windows setup doc: `https://code.visualstudio.com/docs/setup/windows`)

### Verify
Open VS Code from the Start menu.

---

## 2) Install Git (Git for Windows)

### Download (official)
Use either official source:
- `https://git-scm.com/download/win`
- `https://gitforwindows.org/`

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
`https://www.python.org/downloads/latest/python3.13/`

### Install (important checkboxes)
When running the installer:
1. ✅ Check **“Add python.exe to PATH”**
2. ✅ Keep **pip** included (default)
3. ✅ Keep the **Python launcher** (`py`) enabled if offered (default)

### Verify
Close and reopen PowerShell, then run:
```powershell
python --version
py --version
pip --version
```

---

## 4) Install VS Code extensions
In VS Code → Extensions:
- **Python** (Microsoft)

Optional:
- **GitHub Pull Requests and Issues** (GitHub)

---

## 5) Accept the GitHub Classroom assignment and clone the repo

### A) Accept
1. Click the Classroom invite link.
2. Click **Accept assignment**.
3. GitHub creates a repo and takes you to it.

### B) Clone in VS Code
1. Copy the repo **HTTPS** URL from GitHub (Code → HTTPS).
2. In VS Code:
   - `Ctrl+Shift+P` → `Git: Clone`
   - paste the URL
   - pick a folder
3. Open the repo when prompted.

---

## 6) Create a virtual environment (`.venv`) and install dependencies

Open Terminal in VS Code: **Terminal → New Terminal**

### Create venv
From the repo root:
```powershell
py -3.13 -m venv .venv
```

### Activate venv
PowerShell:
```powershell
.\.venv\Scripts\Activate.ps1
```

### Upgrade pip (recommended)
```powershell
python -m pip install --upgrade pip
```

### Install requirements
If your repo has `requirements.txt`:
```powershell
pip install -r requirements.txt
```

---

## 7) Sanity checks
```powershell
python --version
where python
```

If the repo has tests:
```powershell
pytest -q
```

---

## 8) Make a change, commit, and push

Typical “submission” is **commit + push**.

### Option A: VS Code UI
1. Source Control panel
2. Stage changes (`+`)
3. Commit message
4. **Commit**
5. **Sync Changes** (push)

### Option B: terminal
```powershell
git status
git add SUBMISSION.md
git commit -m "Complete submission"
git push
```

If autograding is enabled, you’ll see ✅/❌ on GitHub after pushing.

---

# Troubleshooting (common problems only)

## Git not found in VS Code
- Install Git for Windows (`https://git-scm.com/download/win`)
- Quit and restart VS Code
- Verify:
  ```powershell
  git --version
  ```

## `python` not recognized or opens Microsoft Store
- Install Python 3.13.x from `https://www.python.org/downloads/latest/python3.13/`
- Make sure **Add to PATH** is checked
- Restart PowerShell and verify:
  ```powershell
  python --version
  py --version
  ```

## PowerShell won’t activate `.venv` (execution policy)
Use **Command Prompt** terminal in VS Code and run:
```bat
.\.venv\Scriptsctivate.bat
```
Or (advanced) allow local scripts:
```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

## `git push` permission/auth errors
- Make sure you accepted the assignment with the correct GitHub account
- Retry push and complete the browser sign-in flow if prompted

---

## If you’re stuck, include these in your help request
```powershell
git --version
python --version
py --version
```
