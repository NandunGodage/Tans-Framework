# Git Procedure — STRICT RULES

**All AI assistants MUST follow this procedure exactly. No steps may be skipped or combined without explicit user confirmation.**

---

## Before Starting (Every Session)

1. Confirm the project is a git repository. If not, ask the user if they'd like to initialize one with `git init`.
2. Check that a `.gitignore` file exists. If not, create one appropriate for the project's tech stack and confirm with the user.
3. Check if a remote is configured. If yes, pull the latest changes for the current branch before making any edits. If no remote is configured, skip this step silently.

---

## Workflow Steps (Development Branch Strategy)

### Step 1: Make Changes
- Implement the requested code changes.

### Step 2: Update CHANGELOG
- **Before every commit**, update `CHANGELOG.md` with what was changed, the date, and who made the change.

### Step 3: Update PROJECT-TRACKER
- **Before every commit**, update `PROJECT-TRACKER.md` with today's work summary under the current date.
- If today's date already exists, append the new work — do not overwrite previous entries for the same day.

### Step 4: Commit to Local Dev
- Commit all changes (including changelog and tracker updates) to the local `development` branch.
- Wait for user confirmation before proceeding.

### Step 5: Push to Remote Dev
- Push the local `development` branch to `origin/development`.
- Wait for user confirmation before proceeding.

### Step 6: Check with the User
- **Stop here.** Ask the user: "Changes pushed to development. Want to merge to main and deploy, or keep working?"
- If the user wants to **keep working**, stop the workflow entirely. They will come back when ready.
- If the user wants to **merge and deploy**, continue to Step 7.
- The user can also type `/deploy` at any time later to resume from Step 7.

### Step 7: Review Dev vs Main
- Show the user a summary of what will be merged. Run `git log origin/main..origin/development --oneline` and `git diff origin/main...origin/development --stat` and present the results clearly.
- **Do NOT proceed until the user explicitly confirms** they are happy with the changes.

### Step 8: Merge to Local Main
- Checkout `main` and **pull latest from `origin/main`** to ensure local main is up to date.
- Merge `development` into local `main`.
- If there are merge conflicts, inform the user, show the conflicted files, and help resolve them. Do not proceed until conflicts are resolved.
- Wait for user confirmation before proceeding.

### Step 9: Push Local Main to Remote Main
- Only after user confirmation, push local `main` to `origin/main`.

### Step 10: Deploy
- After pushing to `origin/main`, deploy using the project's deploy command (defined in `PROJECT-CONFIG.md`).
- If no deploy command is configured or deploy command is set to 'none', inform the user: "No deploy command configured — skipping deployment."
- Wait for user confirmation before deploying.

---

## Workflow Steps (Direct to Main — No Development Branch)

Use this workflow when the user chose not to use a development branch during setup.

### Step 1: Make Changes
- Implement the requested code changes.

### Step 2: Update CHANGELOG
- **Before every commit**, update `CHANGELOG.md` with what was changed, the date, and who made the change.

### Step 3: Update PROJECT-TRACKER
- **Before every commit**, update `PROJECT-TRACKER.md` with today's work summary under the current date.

### Step 4: Commit to Local Main
- Commit all changes to the local `main` branch.
- Wait for user confirmation before proceeding.

### Step 5: Push to Remote Main
- Push local `main` to `origin/main`.
- Wait for user confirmation before proceeding.

### Step 6: Check with the User
- **Stop here.** Ask the user: "Changes pushed to main. Want to deploy now, or keep working?"
- If the user wants to **keep working**, stop the workflow entirely.
- If the user wants to **deploy**, continue to Step 7.

### Step 7: Deploy
- Deploy using the project's deploy command from `PROJECT-CONFIG.md`.
- If no deploy command is configured, skip and inform the user.
- Wait for user confirmation before deploying.

---

## When the User Says "No"

If the user says "no" or rejects at any confirmation step:
1. **Stop.** Do not proceed to the next step.
2. **Ask what they want to change.** Example: "Got it — what would you like me to change before we continue?"
3. After making the requested changes, **restart from the step that was rejected** — not from the beginning.
4. **Never undo or roll back commits** unless the user explicitly asks for it.

---

## Key Rules

1. **Always update CHANGELOG.md** before committing any change — no exceptions.
2. **Always update PROJECT-TRACKER.md** with today's work before committing.
3. **Wait for user confirmation** at every step before moving to the next.
4. **Never push to main** without the user first reviewing and explicitly approving.
5. **Never skip steps** or combine multiple steps without explicit permission.
6. **Always pull latest** before merging into main to avoid stale merges.
7. **Handle merge conflicts** by showing the user what's conflicted and helping resolve them.
8. **Don't force the full pipeline** — after pushing to dev (or main), ask the user if they want to continue or keep working.
