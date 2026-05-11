# AI-INSTRUCTIONS.md — AI Instructions for Tan's Framework

## Start of Session

**Every time a new conversation or session begins**, the AI assistant MUST:

1. Check if `PROJECT-CONFIG.md` exists in the project root.
   - If it does NOT exist, run the **First-Time Project Setup** below.
   - If it does exist, read it and greet the user with a brief summary: project name, current branch, and any uncommitted changes.
2. Ensure the user is on the correct working branch (usually `development`). If they are on `main` and the project uses a development branch, let them know and ask if they'd like to switch to `development` before starting work.
3. If a remote is configured, pull the latest changes from the remote for the current branch to avoid working on stale code. If no remote is configured yet, skip this step silently.

---

## First-Time Project Setup

**When `PROJECT-CONFIG.md` does not exist, the AI assistant MUST ask the user the following setup questions before doing any work. Store the answers in a `PROJECT-CONFIG.md` file in the project root.**

### Required Setup Questions

Ask these questions one at a time. Wait for each answer before asking the next:

1. **Project Name** — "What is the name of your project?"
2. **Project Description** — "In one or two sentences, what does your project do?"
3. **Deployment Platform** — "Where will this project be deployed? (e.g., Cloudflare Workers, Vercel, Netlify, AWS, Railway, Fly.io, DigitalOcean, GitHub Pages, self-hosted, other)"
4. **Deploy Command** — "What is the command to deploy your project? (e.g., `npx wrangler deploy`, `vercel --prod`, `npm run deploy`, or 'none' if manual)"
5. **Tech Stack** — "What technologies does this project use? (e.g., Python, Node.js, React, vanilla JS, etc.)"
6. **Team Members** — "Who is working on this project? (list names so commits and changelog entries can be attributed)"
7. **Repository URL** — "What is the Git repository URL? (e.g., https://github.com/username/repo.git, or 'none' if not set up yet)"
8. **Branch Strategy** — "Do you use a `development` branch before merging to `main`? (yes/no — default: yes)"

After collecting answers, generate `PROJECT-CONFIG.md` with the responses and confirm with the user.

### Git Repository Detection

After setup, the AI assistant MUST also check:
- If the project is **not** a git repository, ask the user: "This project isn't a git repo yet. Want me to run `git init` and set it up?"
- If there is **no `.gitignore`** file, create a sensible one based on the tech stack (e.g., `node_modules/`, `.env`, `__pycache__/`, etc.) and confirm with the user.
- If a repository URL was provided but no remote is configured, set it up with `git remote add origin <url>`.

---

## Git Workflow

**STRICT: Follow `GIT_PROCEDURE.md` for all code changes, commits, and pushes. No exceptions.**

### If the user chose a `development` branch (default):
1. Make changes
2. Update `CHANGELOG.md` before every commit
3. Update `PROJECT-TRACKER.md` with today's work
4. Commit to local `development` branch (wait for user confirmation)
5. Push to `origin/development` (wait for user confirmation)
6. **Stop here.** Ask the user: "Changes pushed to development. Want to merge to main and deploy, or keep working?"
   - If the user wants to **keep working**, stop the workflow. Resume from step 1 when they make more changes.
   - If the user wants to **merge and deploy**, continue to step 7.
7. Show the user a diff summary of dev vs main and ask them to review (wait for user confirmation)
8. Checkout `main`, pull latest from `origin/main`, merge `development` into local `main` (wait for user confirmation)
9. Push local `main` to `origin/main` (wait for user confirmation)
10. Deploy using the project's deploy command from `PROJECT-CONFIG.md` (wait for user confirmation)

### If the user chose NO development branch (direct to main):
1. Make changes
2. Update `CHANGELOG.md` before every commit
3. Update `PROJECT-TRACKER.md` with today's work
4. Commit to local `main` branch (wait for user confirmation)
5. Push to `origin/main` (wait for user confirmation)
6. Ask the user: "Changes pushed to main. Want to deploy now, or keep working?"
   - If the user wants to **keep working**, stop the workflow.
   - If the user wants to **deploy**, continue to step 7.
7. Deploy using the project's deploy command from `PROJECT-CONFIG.md` (wait for user confirmation)

Never skip steps. Never push to main without explicit user approval.

### When the User Says "No" at a Confirmation Step

If the user rejects or says "no" at any confirmation step:
- **Do NOT proceed** to the next step.
- **Ask the user what they'd like to change.** For example: "Got it — what would you like me to change before we continue?"
- If the rejection is at the commit step, the user likely wants to modify the code or the changelog entry. Make the requested changes and restart from that step.
- If the rejection is at the merge or deploy step, confirm whether they want to go back to development and make more changes, or stop entirely.
- **Never undo or roll back commits** unless the user explicitly asks for it.

---

## User Commands

**The user can type these commands at any time. When the AI assistant sees one of these, execute the corresponding action immediately.**

### `/deploy`
The user has already reviewed `development` and is ready to ship. Execute the merge-and-deploy steps:
1. Checkout `main` and pull latest from `origin/main`
2. Merge `development` into local `main` (wait for user confirmation)
3. Push local `main` to `origin/main` (wait for user confirmation)
4. Deploy using the project's deploy command from `PROJECT-CONFIG.md` (wait for user confirmation)

If the project uses a direct-to-main workflow (no development branch), simply deploy using the deploy command.

### `/status`
Show a quick summary of the current project state:
1. Today's entries from `PROJECT-TRACKER.md` (if any)
2. The current version and any [Unreleased] items from `CHANGELOG.md`
3. Which branch the user is currently on
4. Whether there are uncommitted changes

### `/release <version>`
Create a new version release in the changelog. For example, `/release v1.2.0`:
1. Move all [Unreleased] items in `CHANGELOG.md` under a new version heading with today's date
2. Update `PROJECT-TRACKER.md` with a release entry for today
3. Commit the changelog and tracker updates to `development` (or `main` if no dev branch)
4. Follow the standard merge-and-deploy workflow from the review step onward

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
