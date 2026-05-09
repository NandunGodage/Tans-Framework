# AI-INSTRUCTIONS.md — AI Instructions for Tan's Framework

## First-Time Project Setup

**When this framework is used in a new project for the first time, the AI assistant MUST ask the user the following setup questions before doing any work. Store the answers in a `PROJECT-CONFIG.md` file in the project root.**

### Required Setup Questions

Ask these questions one at a time. Wait for each answer before asking the next:

1. **Project Name** — "What is the name of your project?"
2. **Project Description** — "In one or two sentences, what does your project do?"
3. **Deployment Platform** — "Where will this project be deployed? (e.g., Cloudflare Workers, Vercel, Netlify, AWS, Railway, Fly.io, DigitalOcean, GitHub Pages, self-hosted, other)"
4. **Deploy Command** — "What is the command to deploy your project? (e.g., `npx wrangler deploy`, `vercel --prod`, `npm run deploy`, or 'none' if manual)"
5. **Tech Stack** — "What technologies does this project use? (e.g., Python, Node.js, React, vanilla JS, etc.)"
6. **Team Members** — "Who is working on this project? (list names so commits and changelog entries can be attributed)"
7. **Repository URL** — "What is the Git repository URL? (e.g., https://github.com/username/repo.git)"
8. **Branch Strategy** — "Do you use a `development` branch before merging to `main`? (yes/no — default: yes)"

After collecting answers, generate `PROJECT-CONFIG.md` with the responses and confirm with the user.

---

## Git Workflow

**STRICT: Follow `GIT_PROCEDURE.md` for all code changes, commits, and pushes. No exceptions.**

Summary:
1. Make changes
2. Update `CHANGELOG.md` before every commit
3. Update `PROJECT-TRACKER.md` with today's work
4. Commit to local `development` branch (wait for user confirmation)
5. Push to `origin/development` (wait for user confirmation)
6. User reviews remote dev vs remote main (wait for user confirmation)
7. Merge into local `main` (wait for user confirmation)
8. Push local `main` to `origin/main` (wait for user confirmation)
9. Deploy using the project's deploy command from `PROJECT-CONFIG.md` (wait for user confirmation)

Never skip steps. Never push to main without explicit user approval.

---

## User Commands

**The user can type these commands at any time. When the AI assistant sees one of these, execute the corresponding action immediately.**

### `/deploy`
Skip straight to the merge-and-deploy steps. This means the user has already reviewed `development` and is ready to ship.
1. Merge `development` into local `main` (wait for user confirmation)
2. Push local `main` to `origin/main` (wait for user confirmation)
3. Deploy using the project's deploy command from `PROJECT-CONFIG.md` (wait for user confirmation)

### `/status`
Show a quick summary of the current project state:
1. Today's entries from `PROJECT-TRACKER.md` (if any)
2. The current version and any [Unreleased] items from `CHANGELOG.md`
3. Which branch the user is currently on
4. Whether there are uncommitted changes

### `/release <version>`
Create a new version release in the changelog. For example, `/release v1.2.0`:
1. Move all [Unreleased] items in `CHANGELOG.md` under a new version heading with today's date
2. Commit the changelog update to `development`
3. Follow the standard merge-and-deploy workflow (steps 6–9 from the Git Workflow)

---

## Daily Work Tracking

**Before every commit**, the AI assistant MUST:
1. Update `CHANGELOG.md` with the version, date, what changed, and who made the change.
2. Update `PROJECT-TRACKER.md` with today's date and a summary of the work done. If today's date already has entries, append to it — do not overwrite.

---

## File Reference

| File | Purpose |
|------|---------|
| `AI-INSTRUCTIONS.md` | AI assistant instructions (this file) |
| `PROJECT-CONFIG.md` | Project-specific settings (generated on first setup) |
| `GIT_PROCEDURE.md` | Step-by-step git workflow rules |
| `GIT-GUIDE.md` | Git guide for team members |
| `CHANGELOG.md` | Version history — what changed, when, and who did it |
| `PROJECT-TRACKER.md` | Daily work log — date-stamped record of all work done |
| `ABOUT.md` | About this framework |
