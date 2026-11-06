# 📝 Changelog

All notable changes to the **Zero-to-GitHero** project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [v1.2.0] - 2026-11-07

### Added
- **Modern Git Commands:** Added complete documentation for `git switch`, `git restore`, `git diff --staged`, `git add -p`, `git status -sb`, `git rm`, and `git mv`.
- **Git Rescue Handbook:** Dedicated chapter covering `git reflog`, recovering dropped commits, recovering deleted branches, recovering from detached HEAD, and safe force pushing with `--force-with-lease`.
- **Advanced Git Guide:** In-depth guide covering `git bisect` (binary search debugging), `git worktree` (parallel working trees), `git submodule` (nested repositories), and `git lfs` (Large File Storage).
- **GitHub Actions & CI/CD Guide:** Modern production-grade workflows using `actions/checkout@v4`, `actions/setup-node@v4` with cache, `npm ci`, and explicit security permissions.
- **GitHub Security & Governance:** Detailed guide on modern Repository Rulesets, Branch Protection Rules, `CODEOWNERS`, Dependabot alerts & version updates, and Secret Scanning.
- **Cheat Sheets:** Added dedicated reference cheat sheets for core Git commands, Git disaster recovery, and GitHub CLI.
- **Repository Standards:** Added `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `.github/ISSUE_TEMPLATE`, `.github/PULL_REQUEST_TEMPLATE.md`, and `.github/CODEOWNERS`.

### Changed
- **Consolidated GitHub Pages:** Merged redundant GitHub Pages guides into a single authoritative guide (`Hosting Websites with GitHub Pages.md`), clarifying static hosting vs. SSR frameworks and custom domains.
- **Cross-Platform Troubleshooting:** Overhauled `Troubleshooting Git & GitHub Issues.md` with explicit commands for Windows PowerShell, Git Bash, and macOS, fixing previous Unix-only syntax (e.g., `eval $(ssh-agent -s)`).
- **Corrected Credential Guidance:** Detailed explanation of Git credential helpers across Windows Credential Manager, macOS Keychain, and proper `git credential reject` protocol.
- **Mermaid Diagrams:** Added visual architecture flowcharts for staging pipelines, 3-way merges vs. rebases, and remote workflows.

---

## [v1.1.0] - 2025-11-20

### Added
- Advanced tips, productivity hacks, and Git aliases.
- GitHub CLI comprehensive reference (`gh` commands).
- Best practices for team collaboration and commit conventions.

---

## [v1.0.0] - 2025-10-15

### Added
- Initial release of Zero-to-GitHero guide.
- Core Git commands (`init`, `status`, `add`, `commit`, `log`, `branch`, `merge`, `remote`, `push`, `pull`, `clone`).
- Fundamentals of GitHub collaboration (Issues, Pull Requests, Forks).
- Basic troubleshooting and GitHub Pages hosting introduction.

