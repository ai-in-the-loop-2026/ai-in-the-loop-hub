# GitHub Classroom Group Assignments

## How it works

When you create a group assignment in GitHub Classroom, you define a **team set** (a named collection of teams). Students form teams when they accept the assignment — no pre-configuration needed.

## What students see when they click the invite link

1. The first student from each team clicks the link and **creates a new team** by typing in a team name.
2. Remaining team members click the same link and **join their team** by selecting it from a list of existing teams.
3. Once a student joins a team, GitHub Classroom creates (or adds them to) a shared repo named `assignment-name-team-name` in the org.

All team members have push/pull access to the same repo.

## What you need to tell students

- **Coordinate before accepting.** One person per team creates the team, the others join it. If two people both create separate teams by accident, you'll end up with duplicate repos.
- **Team name = part of the repo name.** Keep it short, lowercase, and use hyphens (e.g., `data-wizards`). The repo will be named `final-project-working-data-wizards`.
- **The team name is permanent.** It can't be changed after creation without instructor intervention.
- **Everyone must accept the assignment.** Even if the repo already exists, each team member needs to click the invite link and join the team so they have access.

## Instructor setup notes

- **Assignment name:** `final-project-working` (matches the branch protection ruleset pattern `final-project-working-*`)
- **Invite link:** https://classroom.github.com/a/30poBfe_
- **Template repo:** `ai-in-the-loop-2026/final-project-working-template`
- **Team set name:** Something like "Final Project Teams" — this is reusable if you need teams for future assignments
- **Max team size:** Set to 3 (largest team is 3, smallest is 2)

## Suggested in-class workflow

1. Announce teams (or let students self-select if not already decided).
2. Designate one person per team to create the team on Classroom.
3. That person clicks the invite link, types the team name, and confirms.
4. Other team members click the same invite link and select their team from the list.
5. Everyone verifies they can see the shared repo on GitHub.

## If something goes wrong

- **Student joined wrong team:** Remove them from the team in the GitHub org settings (Organization → Teams), then have them re-accept the invite.
- **Duplicate teams created:** Delete the extra repo and team from the org. Have the student re-accept and join the correct team.
- **Student can't see the repo:** Make sure they actually accepted the assignment (clicked the invite link and joined the team), not just visited the repo URL.

## References

- [Create a group assignment — GitHub Docs](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/create-a-group-assignment)
- [About assignments — GitHub Docs](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/about-assignments)
