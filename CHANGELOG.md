# Changelog

All notable changes to this project will be documented in this file.

Format: Each entry includes the version, date, what was changed, and who made the change.

---

## [3.0.0] - 2026-05-11

### Added
- **Commit without deploying** — After pushing to dev (or main), the AI now asks "want to merge and deploy, or keep working?" instead of forcing you through the full pipeline every time.
- **GIT-GUIDE.md supports both branch strategies** — The team guide now covers both development-branch and direct-to-main workflows.
- **Session start handles missing remote** — Brand new projects after `git init` won't error on pull if no remote is configured.

---

## [2.0.0] - 2026-05-07

### Added
- **User Commands** — `/deploy`, `/status`, and `/release <version>` trigger common actions instantly.
- **Session Start Behavior** — AI greets with project context, checks branch, and pulls latest changes.
- **Git Init & .gitignore Detection** — Detects if project isn't a git repo and offers setup.

### Fixed
- Branch strategy choice is now respected.
- "No" at confirmation steps is now handled correctly.
- `/deploy` now pulls latest main first.
- `/release` now updates `PROJECT-TRACKER.md`.
- Review step now shows a diff (`git log` and `git diff --stat`).
- Fixed `ABOUT.md` referencing non-existent file.

---

## [1.0.0] - 2026-05-11

### Added
- Initial release — core workflow, changelog, tracker, git procedure, team guide.
