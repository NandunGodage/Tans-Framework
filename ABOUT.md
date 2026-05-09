# Tan's Framework

## What Is This?

Tan's Framework is a project management and development workflow framework designed to work with AI coding assistants (like Claude). It gives any project a structured, professional workflow out of the box — no matter the tech stack or deployment platform.

## Why Use It?

Building software with AI assistants is powerful, but without structure, things get messy fast — no version tracking, no work logs, no consistent git workflow, and no accountability for who did what.

Tan's Framework solves this by providing:

- **Guided Setup** — When you start a new project, the AI asks you setup questions (project name, deployment platform, tech stack, team members) and configures everything automatically.
- **Strict Git Workflow** — A step-by-step git procedure that prevents mistakes. Changes go through `development` first, get reviewed, then merge to `main`. No accidental pushes to production.
- **Automatic Changelog** — Every change is logged in `CHANGELOG.md` with the version, date, what changed, and who did it. You always know the full history of your project.
- **Daily Work Tracking** — `PROJECT-TRACKER.md` is updated before every commit with a date-stamped summary of work done. You can see exactly what happened on any given day.
- **Team-Friendly Git Guide** — A simple guide (`GIT-GUIDE.md`) that any team member can follow, even if they're new to Git.
- **AI-Ready Instructions** — `AI-INSTRUCTIONS.md` tells AI assistants exactly how to behave in your project — what rules to follow, what files to update, and what questions to ask.
- **User Commands** — Type `/deploy`, `/status`, or `/release <version>` to quickly trigger common actions without explaining what you need.

## How to Use It

1. **Copy this framework** into the root of any new project.
2. **Open the project with an AI assistant** (e.g., Claude Code).
3. **The AI will ask you setup questions** — project name, deployment platform, tech stack, team members, and repository URL.
4. **Start building.** The framework handles the rest — tracking changes, logging work, and enforcing a clean git workflow.

### Files in This Framework

| File | What It Does |
|------|-------------|
| `AI-INSTRUCTIONS.md` | Instructions for AI assistants — setup questions, workflow rules, and user commands |
| `PROJECT-CONFIG.md` | Your project's settings (auto-generated during setup) |
| `GIT_PROCEDURE.md` | Step-by-step git workflow — the rules everyone follows |
| `GIT-GUIDE.md` | Simple git guide for team members |
| `CHANGELOG.md` | Version history — what changed, when, and who did it |
| `PROJECT-TRACKER.md` | Daily work log — date-stamped record of all work |
| `ABOUT.md` | This file — about the framework |

## Who Made This?

**Tan** — [@1simply_tan](https://instagram.com/1simply_tan) on Instagram.

Built from real experience shipping projects with AI-assisted development. This framework exists because every project deserves clean version control, clear accountability, and a workflow that doesn't fall apart when things move fast.
