# Git Guide for Team Members

## One-Time Setup

### 1. Install Git
- Download from [git-scm.com](https://git-scm.com/downloads) and install with default settings.

### 2. Configure Your Name and Email
Open a terminal and run:
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### 3. Clone the Repository
Replace the URL with your project's repository URL (found in `PROJECT-CONFIG.md`):
```bash
git clone <your-repo-url>
cd <your-project-folder>
```

### 4. Switch to Your Working Branch

**If your project uses a `development` branch** (check `PROJECT-CONFIG.md`):
```bash
git checkout development
```

**If your project works directly on `main`**, you're already on the right branch. No action needed.

You're all set!

---

## Daily Workflow

### Before You Start Working
Always pull the latest changes first:

**If using a development branch:**
```bash
git pull origin development
```

**If working directly on main:**
```bash
git pull origin main
```

### After You Make Changes

**If using a development branch:**
```bash
git add .
git commit -m "Brief description of what you changed"
git push origin development
```

**If working directly on main:**
```bash
git add .
git commit -m "Brief description of what you changed"
git push origin main
```

### Example
```bash
git pull origin development
# ... edit some files ...
git add .
git commit -m "Updated login page styling"
git push origin development
```

---

## Important Rules

1. **Always pull before you start working** — this avoids conflicts.
2. **Only work on your designated branch** — if the project uses a `development` branch, never push directly to `main`. If the project works on `main`, push to `main`.
3. **Communicate with the team** — if you're editing a file, let others know so two people don't edit the same file at the same time.
4. **Write clear commit messages** — describe what you changed so others can understand.
5. **Update the CHANGELOG** — before committing, add a note to `CHANGELOG.md` about what you changed.
6. **Check your .gitignore** — make sure files like `.env`, `node_modules/`, and other secrets or dependencies are listed in `.gitignore` so they don't get pushed to the repository.

---

## Handling Merge Conflicts

If you see a merge conflict when pulling, it means someone else changed the same file you did. Here's what to do:

1. Open the conflicted file — you'll see something like:
   ```
   <<<<<<< HEAD
   your changes
   =======
   their changes
   >>>>>>> origin/development
   ```
2. Edit the file to keep the correct version (remove the `<<<<<<<`, `=======`, and `>>>>>>>` markers).
3. Save the file, then:
   ```bash
   git add .
   git commit -m "Resolved merge conflict in filename"
   git push origin development
   ```

If you're unsure, ask the project lead for help before pushing.

---

## Quick Reference

**If using a development branch:**

| What you want to do          | Command                                      |
|------------------------------|----------------------------------------------|
| Get latest changes           | `git pull origin development`                |
| See what files you changed   | `git status`                                 |
| Stage all changes            | `git add .`                                  |
| Commit your changes          | `git commit -m "your message"`               |
| Push to remote               | `git push origin development`                |
| Check which branch you're on | `git branch`                                 |
| Switch to development branch | `git checkout development`                   |

**If working directly on main:**

| What you want to do          | Command                                      |
|------------------------------|----------------------------------------------|
| Get latest changes           | `git pull origin main`                       |
| See what files you changed   | `git status`                                 |
| Stage all changes            | `git add .`                                  |
| Commit your changes          | `git commit -m "your message"`               |
| Push to remote               | `git push origin main`                       |
| Check which branch you're on | `git branch`                                 |
