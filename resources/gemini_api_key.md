---
title: "Getting a Gemini API Key"
description: "How to obtain a free Gemini API key from Google AI Studio for course assignments."
date: 2026-01-01
categories: [Setup]
tags: [gemini, api-key, google-ai-studio, authentication]
---

# Getting a Gemini API Key
## Creating with AI in the Loop — Google AI Studio setup

This guide shows you how to get a free Gemini API key using Google AI Studio. You'll need this for assignments that interact with Gemini models.

---

## What you need

- A personal Google account (Gmail or Google Workspace)

---

## Step-by-step: Get your API key

1. Sign in to your **personal Google account** (not your .edu account), then go to <https://aistudio.google.com>.

2. If prompted, accept the Terms of Service.

3. Click **Get API key** in the left sidebar.

4. Click the **Create API key** button (upper right).

5. Enter a name for your key (e.g., `myFirstGeminiKey`).

6. Under **Choose an imported project**, click **+ Create a new project** and name it (e.g., `AI in the Loop`). You may need to re-enter the key name after creating the project.

7. Click **Create**. You do not need to set up billing—the free tier is sufficient for this course.

8. Click the **copy icon** to copy your API key. Store it immediately (see next section).

---

## Storing your API key securely

**If you don't have an assignment yet:** Save your API key somewhere safe (e.g., a password manager or private notes app). You'll add it to a `.env` file when you start your first assignment that needs it.

**When working on an assignment:** Store your key in a `.env` file in your repo:

1. Create a file named `.env` in your assignment repo (note the leading dot)
2. Add your key:
   ```
   GEMINI_API_KEY=your-api-key-here
   ```
3. Verify `.env` is in your `.gitignore` (it should be by default)

Your code will load the key from this file using a library like `python-dotenv`.

**Never commit your API key to Git.**

---

## If your API key is compromised

If you suspect your API key has been compromised (e.g., accidentally pushed to GitHub or shared publicly):

1. Go to <https://aistudio.google.com/app/apikey>
2. Click the **Create API key** button to generate a new key
3. Follow steps 5-8 above to create and copy your new key
4. Update your `.env` file with the new key
5. Test that your code works with the new key
6. Return to the API keys page and click the **delete** icon (trash can) next to your old, compromised key

**Always delete the old key** to ensure the compromised key can't be used.

---

## Retrieving your API key later

If you need to copy your key again, go to <https://aistudio.google.com/app/apikey> and click the **copy icon** next to your key.

---

## Free tier limits

Google AI Studio provides a free tier with rate limits:

- Sufficient for course assignments
- If you exceed limits, you'll get a rate limit error (not a charge)
- See current limits: <https://ai.google.dev/pricing>

---

# Troubleshooting

## "API key not valid" errors

- Make sure you copied the entire key (no extra spaces)
- Verify your `.env` file has the correct variable name (check the assignment README)
- Ensure `.env` is in the same directory as your Python script (or follow the assignment's instructions)

## Can't access Google AI Studio

- Use a personal Google account, not your .edu account
- Try a different browser or incognito mode
- Clear your browser cache and cookies

## Rate limit exceeded

- Wait a few minutes and try again
- If persistent, check that you're not making requests in a loop by accident

---

## Resources

- Official docs: <https://ai.google.dev/gemini-api/docs/api-key>
- Google AI Studio: <https://aistudio.google.com>
- Pricing and limits: <https://ai.google.dev/pricing>

---

## If you're stuck, include these in your help request

- The exact error message you're seeing
- Confirmation that your `.env` file exists and is in the correct location
- The contents of your `.env` file (with the actual key replaced by `xxx`)