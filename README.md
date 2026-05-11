# Tan's Framework — v3.0.0

A plug-and-play project management framework for AI-assisted development. Drop it into any project and get structured git workflows, automatic changelogs, daily work tracking, and guided setup — all enforced by your AI coding assistant.

---

## What's New in v3.0.0

### Fixes & Improvements
- **Commit without deploying** — After pushing to dev (or main), the AI now asks "want to merge and deploy, or keep working?" instead of forcing you through the full pipeline every time. Use `/deploy` when you're ready.
- **GIT-GUIDE.md supports both branch strategies** — The team guide now covers both development-branch and direct-to-main workflows, matching whatever was chosen during setup.
- **Session start no longer fails without a remote** — Brand new projects after `git init` won't error on pull. The AI only pulls if a remote is configured.

---

## What's New in v2.0.0

### New Features
- **User Commands** — `/deploy`, `/status`, and `/release <version>` let you trigger common actions instantly.
- **Session Start Behavior** — AI now greets you with project context, checks your branch, and pulls latest changes at the start of every session.
- **Git Init & .gitignore Detection** — Framework detects if your project isn't a git repo yet and offers to set it up, including a .gitignore tailored to your tech stack.

### Fixes & Improvements
- **Branch strategy choice is now respected** — Saying "no" to a development branch gives you a direct-to-main workflow instead of being ignored.
- **"No" at confirmation steps is now handled** — AI asks what you'd like to change instead of being stuck or guessing.
- **`/deploy` now pulls latest main first** — Prevents merging into stale local main.
- **`/release` now updates PROJECT-TRACKER.md** — Follows the framework's own "update tracker before every commit" rule.
- **Review step now shows a diff** — AI runs `git log` and `git diff --stat` so you can actually see what's being merged.
- **Fixed ABOUT.md referencing non-existent file** — Was pointing to `CLAUDE.md` instead of `AI-INSTRUCTIONS.md`.

---

## The Problem

AI coding assistants are powerful, but without structure:

- Changes get pushed without documentation
- No one knows who changed what or when
- There's no version history or changelog
- Work done yesterday is forgotten today
- New team members have no idea how to contribute
- Deployment steps get skipped or done out of order

## The Solution

Tan's Framework gives every project a professional development workflow from day one. It works with **any AI assistant** (Claude, Cursor, Windsurf, Copilot, etc.), **any tech stack**, and **any deployment platform**.

---

## How It Works

### 1. Drop it in
Copy the framework files into the root of your project.

### 2. Start your AI assistant
Open the project with your AI coding tool. The framework detects it's a fresh setup and walks you through configuration:

- Project name and description
- Deployment platform (Vercel, Cloudflare, AWS, Netlify, Railway, etc.)
- Deploy command
- Tech stack
- Team members
- Repository URL
- Branch strategy

Your answers are saved to `PROJECT-CONFIG.md` — the AI references this for every future session.

### 3. Build with guardrails
From here, the framework enforces:

- **Changelog updates** before every commit
- **Daily work tracking** with date-stamped entries
- **Strict git workflow** — dev branch first, review, then merge to main
- **User confirmation** at every critical step (no surprise pushes)
- **Deployment** using your configured deploy command

---

## What's Included

| File | Purpose |
|------|---------|
| `AI-INSTRUCTIONS.md` | Core framework — setup questions, workflow rules, and user commands |
| `GIT_PROCEDURE.md` | Step-by-step git workflow that AI assistants follow strictly |
| `GIT-GUIDE.md` | Simple git guide for team members (beginner-friendly) |
| `CHANGELOG.md` | Auto-maintained version history — what, when, and who |
| `PROJECT-TRACKER.md` | Auto-maintained daily work log |
| `ABOUT.md` | Framework overview and usage guide |

> `PROJECT-CONFIG.md` is generated automatically during first-time setup.

---

## User Commands

Type these at any time during a session:

| Command | What it does |
|---------|-------------|
| `/deploy` | Merge dev to main and deploy — for when you've already reviewed |
| `/status` | Show today's work, changelog state, current branch, and uncommitted changes |
| `/release <version>` | Move unreleased changelog items under a new version and kick off deploy |

---

## Quick Start

```bash
# Clone the framework
git clone https://github.com/NandunGodage/Tans-Framework.git

# Copy the files into your project
cp tans-framework/AI-INSTRUCTIONS.md your-project/
cp tans-framework/GIT_PROCEDURE.md your-project/
cp tans-framework/GIT-GUIDE.md your-project/
cp tans-framework/CHANGELOG.md your-project/
cp tans-framework/PROJECT-TRACKER.md your-project/
cp tans-framework/ABOUT.md your-project/

# Open your project with your AI assistant and start building
```

Or just download the files directly and drop them into your project root.

---

## Version History

| Version | Date | What Changed |
|---------|------|-------------|
| v3.0.0 | 2026-05-07 | Commit-without-deploy flow, GIT-GUIDE supports both branch strategies, session start handles missing remote |
| v2.0.0 | 2026-05-07 | User commands, session start behavior, git init detection, branch strategy support, confirmation rejection handling, diff review, tracker fix, ABOUT.md fix |
| v1.0.0 | — | Initial release — core workflow, changelog, tracker, git procedure, team guide |

---

## Why I Built This

I got tired of AI assistants making changes with zero accountability — no changelogs, no tracking, no process. Every project I started had the same problems. So I built the workflow I wanted and made it reusable.

This framework exists because every project deserves clean version control, clear accountability, and a workflow that doesn't fall apart when things move fast.

---

## Author

**Tan** — [@1simply_tan](https://instagram.com/1simply_tan)

---

## License

Free to use.

Just remember that someone out there helped you with something in life. Pass it on — help the next person the way this helped you. Spread harmony.


## A Note from Tan

I believe in a world where people stand together — without borders drawn by language, religion, skin color, country, caste, or anything else that divides us. We are one. We share this life. Let's live it and help each other.

If this framework saved you time, go help someone else. That's how we build a better world, one person at a time.

-- Tan | [@1simply_tan](https://instagram.com/1simply_tan)
