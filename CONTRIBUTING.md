# Contributing to Tan's Framework

This document explains how Tan's Framework is structured, how to make changes, and how to release new versions. If you're an AI assistant helping with this project, read this first.

---

## Project Structure

Tan's Framework is a collection of markdown files that users drop into any project. There is no code to compile, no dependencies to install, and no build step. The framework works by AI assistants reading the markdown files and following the instructions within them.

### Files

| File | Role |
|------|------|
| `AI-INSTRUCTIONS.md` | The brain — tells AI assistants how to behave, what questions to ask, and what workflow to follow |
| `GIT_PROCEDURE.md` | The rulebook — step-by-step git workflow that AI assistants enforce |
| `GIT-GUIDE.md` | The team guide — beginner-friendly git instructions for human team members |
| `CHANGELOG.md` | Template — users' projects use this to track their own changes |
| `PROJECT-TRACKER.md` | Template — users' projects use this to track daily work |
| `ABOUT.md` | Overview — explains what the framework is and how to use it |
| `README.md` | Public-facing — what people see on GitHub, includes version history and what's new |

### How the files connect

- `AI-INSTRUCTIONS.md` is the entry point. AI assistants read this first and it references `GIT_PROCEDURE.md` and `PROJECT-CONFIG.md`.
- `GIT_PROCEDURE.md` contains the detailed steps that `AI-INSTRUCTIONS.md` summarizes.
- `GIT-GUIDE.md` is standalone — it's for human team members, not AI assistants.
- `CHANGELOG.md` and `PROJECT-TRACKER.md` are blank templates. The framework tells AI assistants to fill them in during the user's project.
- `ABOUT.md` and `README.md` are informational. They don't affect how the framework works.

---

## Design Principles

Keep these in mind when making changes:

1. **Simplicity over features.** The framework is powerful because it's simple. Don't add complexity unless it solves a real problem.
2. **AI-tool agnostic.** Everything works through markdown files that any AI assistant can read. Never tie the framework to a specific tool (Claude, Cursor, etc.).
3. **Stack agnostic.** The framework works with any programming language, any deployment platform, and any project type. Don't add instructions that assume a specific tech stack.
4. **User always in control.** Every destructive or irreversible action requires user confirmation. The AI suggests, the user decides.
5. **No jargon.** The target audience includes beginners. Write instructions that anyone can follow.

---

## How to Make Changes

### 1. Understand the current version
- Read through all files in the latest version folder to understand the current state.
- Check `README.md` for the version history to understand what changed in previous versions.

### 2. Identify the problem
- Be specific about what's broken, missing, or confusing.
- Check if the issue affects `AI-INSTRUCTIONS.md`, `GIT_PROCEDURE.md`, or both — they must stay in sync.

### 3. Make the change
- If a rule exists in `AI-INSTRUCTIONS.md`, it should also be in `GIT_PROCEDURE.md` (and vice versa). Keep them consistent.
- If you change the workflow steps, make sure the step numbers are correct in both files.
- If you add a new user command, add it to `AI-INSTRUCTIONS.md` under the User Commands section and mention it in `README.md` and `ABOUT.md`.
- If you change anything about branch strategy, update `GIT-GUIDE.md` too — it covers both development-branch and direct-to-main workflows.

### 4. Test by reading
Since this is a markdown-only framework, "testing" means reading the files as an AI assistant would and checking:
- Are the instructions clear and unambiguous?
- Are there contradictions between files?
- Are there gaps where the AI wouldn't know what to do?
- Does every workflow path have a defined behavior (including when the user says "no")?

---

## How to Release a New Version

1. **Create a new folder** named `Tan's Framework v<number>` (e.g., `Tan's Framework v4`).
2. **Copy all files** from the previous version into the new folder.
3. **Make your changes** in the new folder. Do not modify previous version folders.
4. **Update `README.md`**:
   - Change the version number in the title (e.g., `v4.0.0`).
   - Add a "What's New in v4.0.0" section at the top, below the description.
   - Add the new version to the Version History table at the bottom.
5. **Keep previous "What's New" sections** in the README so the full history is visible.

### Version numbering

This project uses simple versioning: `v1.0.0`, `v2.0.0`, `v3.0.0`, etc. Each release that changes behavior gets a new major version. There's no need for minor or patch versions at this scale.

---

## Common Pitfalls

Things that have gone wrong before — avoid repeating them:

- **Files referencing other files that don't exist.** If you rename a file, search all other files for references to the old name.
- **Workflow assumes a development branch when the user chose not to use one.** Always check that both branch strategies are covered.
- **Forgetting to update the tracker before a commit.** Every commit rule must include both CHANGELOG and PROJECT-TRACKER updates.
- **Commands that break the framework's own rules.** If the framework says "update tracker before every commit," then every command that commits must also update the tracker.
- **Pulling from remote when no remote exists.** New projects after `git init` won't have a remote. Always check first.
- **Forcing the full pipeline when the user just wants to commit.** Always give the user a chance to stop after pushing, rather than dragging them through merge and deploy.

---

## Questions to Ask Before Any Change

1. Does this change make the framework simpler or more complex?
2. Does this work with every AI tool, or does it tie us to one?
3. Does this work with every tech stack?
4. Is the instruction clear enough that an AI won't misinterpret it?
5. Did I update every file that needs to stay in sync?

---

## Author

**Tan** — [@1simply_tan](https://instagram.com/1simply_tan)
