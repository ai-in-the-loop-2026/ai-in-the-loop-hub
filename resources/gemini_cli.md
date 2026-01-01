---
title: "Installing Gemini CLI"
description: "Set up Google's Gemini CLI for AI assistance in your terminal."
date: 2026-01-01
categories: [Setup]
tags: [gemini, cli, terminal, ai-assistant]
---

# Installing Gemini CLI
## Creating with AI in the Loop — Terminal AI assistant

Gemini CLI brings Gemini AI directly to your terminal. You can ask questions, generate code, and work with your codebase from the command line.

---

## macOS

```bash
brew install gemini-cli
```

Verify: `gemini --version`

---

## Windows

### 1) Install Node.js (version 20 or higher)

Download the LTS installer from <https://nodejs.org> and run it. Reboot if prompted.

Verify:

```powershell
node -v
npm -v
```

### 2) Install Gemini CLI

```powershell
npm install -g @google/gemini-cli
```

Verify: `gemini --version`

---

## First run: Sign in

1. Open a terminal in your project directory.
2. Run `gemini`.
3. Select **Login with Google**.
4. Sign in with your **personal Google account** (not your .edu account).

After signing in, you can start chatting with Gemini about your code.

---

## Free tier

Gemini CLI is free. The daily limits are sufficient for course assignments.

---

# Troubleshooting

## macOS: `brew: command not found`

Install Homebrew first. See [Initial Setup (macOS)](initial_setup_macos.md).

## Windows: `node` or `npm` not recognized

Restart your terminal after installing Node.js. If still not working, reinstall Node.js and make sure "Add to PATH" is checked.

## Authentication issues

- Use a personal Google account, not your .edu account
- Try signing out and back in: `gemini --logout` then `gemini`

---

## Resources

- Official docs: <https://geminicli.com/docs/>
- GitHub: <https://github.com/google-gemini/gemini-cli>
