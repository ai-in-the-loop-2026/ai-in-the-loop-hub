---
title: "Publishing a Portfolio Site with Quarto"
description: "How to create a simple project portfolio site using Quarto and publish it to GitHub Pages."
date: 2026-02-16
categories: [Quarto, GitHub]
tags: [quarto, github-pages, portfolio]
---

# Publishing a Portfolio Site with Quarto

Quarto turns markdown files into a polished website — no HTML or CSS required. This guide walks you through creating a simple portfolio site for your final project and publishing it to GitHub Pages.

---

## 1. Install Quarto

1. Download and run the installer for your platform from [quarto.org/docs/download](https://quarto.org/docs/download/).
2. In VS Code, install the **Quarto extension** (`quarto.quarto`). This gives you a Preview button, syntax highlighting, and autocomplete for `.qmd` files.

---

## 2. Set up your public repo

Follow the steps in [Setting up your portfolio repo](#setting-up-your-portfolio-repo) below to create a clean copy of your project code without development history. Then open the folder in VS Code.

---

## 3. Add a Quarto config file

Create a file called `_quarto.yml` in the root of your repo:

```yaml
project:
  type: website
  render:
    - "*.qmd"

website:
  title: "Your Project Name"

format:
  html:
    theme: cosmo
```

The `render: ["*.qmd"]` line tells Quarto to only render `.qmd` files, so your project's `README.md` and other `.md` files won't get pulled into the site.

Change the title to your project name. If you want a different look, you can swap `cosmo` for another theme like `flatly`, `lumen`, or `minty` ([full list](https://quarto.org/docs/output-formats/html-themes.html)).

---

## 4. Write your content

Create an `index.qmd` file in the root of your repo (next to `_quarto.yml`). This is your home page. Write it in markdown:

Here's a minimal starting point — adapt the structure and sections to fit your project:

```markdown
---
title: "Your Project Name"
---

## What it does

Describe your project for a general audience. What problem does it solve? Who is it for?

![The main interface](images/main-interface.png)

## How it works

Summarize the technical approach — tools, LangGraph workflow, etc. Keep it accessible.

![Example of the workflow in action](images/workflow-example.png)

## Team

- Name 1
- Name 2
- Name 3
```

Place screenshots in an `images/` folder and embed them where they're relevant — alongside the text they illustrate, not in a separate pile.

You can add more pages — just create more `.qmd` files in the root of your repo. Link to them from `index.qmd` using standard markdown links:

```markdown
Learn more about our [technical architecture](architecture.qmd) or see the [demo walkthrough](demo.qmd).
```

---

## 5. Preview your site

Click the **Preview** button in the top right of the VS Code editor when you have a `.qmd` file open. Your site opens in a panel and auto-refreshes as you edit.

You can also preview from the terminal:

```bash
quarto preview
```

---

## 6. Publish to GitHub Pages

When you're happy with the site, open a terminal in VS Code and run:

```bash
quarto publish gh-pages
```

Quarto will render your site, push it to a `gh-pages` branch, and give you the URL. Your site will be live at `https://USERNAME.github.io/REPO-NAME/`.

---

## Tips

- **Keep it concise.** This is a portfolio piece, not a technical report. A recruiter or admissions reviewer should be able to understand your project in a few minutes.
- **Include visuals.** Screenshots or screen recordings make the project tangible.
- **Include your project code.** Someone should be able to clone this repo and run your app. Don't include your AI development log or full commit history — see [Setting up your portfolio repo](#setting-up-your-portfolio-repo) below.
- **Consider a demo video.** A short screen recording uploaded to YouTube (unlisted, so only people with the link can view it) can be more compelling than screenshots alone. Link to it from your site.

---

## Setting up your portfolio repo

Your public portfolio repo should contain your project code but **not** the development history or AI development log from your private working repo. Instead, include a brief summary in your README of how AI tools were used in developing the project. You'll build the site together as a team, then each member copies it to their own GitHub so it shows up on everyone's profile.

### Step A: Build it together (one member creates the shared repo)

One team member does steps 1–5. The others join as collaborators.

1. Copy your entire working repo folder to a new location with a clean name (e.g., `your-project-name`).

2. Open the copied folder in VS Code, then open a terminal and delete the `.git/` folder and any files you don't want public:

::: {.panel-tabset}

#### macOS

```bash
rm -rf .git
rm -f ai_dev_log.md .env
```

#### Windows (PowerShell)

```powershell
Remove-Item -Recurse -Force .git
Remove-Item -Force ai_dev_log.md, .env
```

:::

3. Initialize a fresh repo and make your first commit:

```bash
git init
git add .
git commit -m "Initial commit"
```

4. Create a new repo on GitHub:
    - Go to [github.com/new](https://github.com/new)
    - Name it the **same thing** as your local folder
    - Set it to **Public**
    - **Do not** check "Add a README file" or any other options — the repo must be empty
    - Click **Create repository**

5. GitHub will show a page with setup instructions. Under **"…or push an existing repository from the command line"**, copy the commands and run them. They will look like:

```bash
git remote add origin https://github.com/USERNAME/your-project-name.git
git push -u origin main
```

6. Add your teammates and the instructor as collaborators: go to the repo on GitHub → **Settings** → **Collaborators** → **Add people**.

Now your team can collaborate on the portfolio site — add the `_quarto.yml`, `index.qmd`, screenshots, etc. Use the same [branch and pull request workflow](github_collaboration.md) as your working repo.

### Step B: Each member copies it to their own GitHub

Once the portfolio site is finished, **each other team member** copies it to their own GitHub account so it appears on their profile (not as a fork).

1. Clone the shared repo to a new folder:

```bash
git clone https://github.com/TEAMMATE/your-project-name.git your-project-name-copy
cd your-project-name-copy
```

2. Remove the git history and reinitialize:

::: {.panel-tabset}

#### macOS

```bash
rm -rf .git
git init
git add .
git commit -m "Initial commit"
```

#### Windows (PowerShell)

```powershell
Remove-Item -Recurse -Force .git
git init
git add .
git commit -m "Initial commit"
```

:::

3. Create your own repo on GitHub (same as step 4 above — [github.com/new](https://github.com/new), same name, public, empty).

4. Push to your repo:

```bash
git remote add origin https://github.com/YOUR-USERNAME/your-project-name.git
git push -u origin main
```

5. Publish your own GitHub Pages site:

```bash
quarto publish gh-pages
```

Each team member ends up with their own copy of the portfolio site on their own GitHub profile.
