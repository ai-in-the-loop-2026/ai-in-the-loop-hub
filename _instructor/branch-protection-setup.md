# Branch Protection for Final Project Repos

## Overview

An organization-level branch ruleset is configured to enforce the branch-and-PR workflow on final project repos. This prevents students from pushing directly to `main` — all changes must go through a pull request.

## Ruleset details

- **Ruleset name:** Final project — require PRs
- **Enforcement:** Active
- **Bypass list:** Organization admins (always allow)
- **Target repositories:** Repositories matching name `final-project-working-*`
- **Target branches:** Default branch (`main`)
- **Rules enabled:**
  - Require a pull request before merging (0 required approvals)
  - Block force pushes
  - Restrict deletions

## GitHub Classroom assignment

When creating the final project group assignment in GitHub Classroom:

- **Assignment name:** `final-project-working`
- GitHub Classroom will create repos named `final-project-working-TEAM-NAME`, which matches the ruleset's `final-project-working-*` pattern.

## Where to find the ruleset

Organization Settings → Code, planning, and automation → Repository → Rulesets

## Notes

- The ruleset applies automatically to new repos matching the naming pattern — no per-repo setup needed.
- The org admin bypass means you can push directly to `main` if needed (e.g., seeding starter files).
- This ruleset does **not** apply to individual assignment repos (e.g., `a0-*`, `a1-*`), which still use the direct commit-and-push workflow.
