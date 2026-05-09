# Git Procedure — STRICT RULES

**All AI assistants MUST follow this procedure exactly. No steps may be skipped or combined without explicit user confirmation.**

---

## Workflow Steps

### Step 1: Make Changes
- Implement the requested code changes.

### Step 2: Update CHANGELOG
- **Before every commit**, update `CHANGELOG.md` with what was changed, the date, and who made the change.
- Wait for user confirmation before proceeding.

### Step 3: Update PROJECT-TRACKER
- **Before every commit**, update `PROJECT-TRACKER.md` with today's work summary under the current date.
- If today's date already exists, append the new work — do not overwrite previous entries for the same day.

### Step 4: Commit to Local Dev
- Commit all changes (including changelog and tracker updates) to the local `development` branch.
- Wait for user confirmation before proceeding.

### Step 5: Push to Remote Dev
- Push the local `development` branch to `origin/development`.
- Wait for user confirmation before proceeding.

### Step 6: User Reviews Remote Dev vs Remote Main
- The user will compare `origin/development` against `origin/main` to review what will be merged.
- **Do NOT proceed until the user explicitly confirms** they are happy with the changes.

### Step 7: Merge to Local Main
- Checkout `main`, pull latest, and merge `development` into local `main`.
- Wait for user confirmation before proceeding.

### Step 8: Push Local Main to Remote Main
- Only after user confirmation, push local `main` to `origin/main`.

### Step 9: Deploy
- After pushing to `origin/main`, deploy using the project's deploy command (defined in `PROJECT-CONFIG.md`).
- If no deploy command is configured, skip this step and inform the user.
- Wait for user confirmation before deploying.

---

## Key Rules

1. **Always update CHANGELOG.md** before committing any change — no exceptions.
2. **Always update PROJECT-TRACKER.md** with today's work before committing.
3. **Wait for user confirmation** at every step before moving to the next.
4. **Never push to main** without the user first reviewing the dev-to-main diff and explicitly approving.
5. **Never skip steps** or combine multiple steps without explicit permission.
