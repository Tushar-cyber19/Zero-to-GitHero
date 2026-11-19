# 🤝 Contributing to Zero-to-GitHero

Thank you for your interest in contributing to **Zero-to-GitHero**! 🎉 This project thrives on community contributions to help developers worldwide master Git and GitHub from the ground up.

Whether you're fixing a typo, improving an explanation, adding a real-world scenario, or updating command flags, your help is warmly welcomed.

---

## 🌟 Code of Conduct

By participating in this project, you agree to abide by our [Code of Conduct](CODE_OF_CONDUCT.md). Please treat all contributors and learners with respect and kindness.

---

## 🧭 Ways to Contribute

1. 🐛 **Report Issues**: Found a technical error, broken link, or outdated command syntax? Open an issue using our issue templates.
2. ✍️ **Improve Content**: Enhance explanations, add visual diagrams, or clarify confusing sections.
3. 💻 **Add New Guides / Topics**: Propose and draft new guides covering modern developer workflows.
4. 🪟 **Cross-Platform Compatibility**: Help verify and provide instructions for Windows (PowerShell/CMD), macOS (zsh), and Linux (bash).
5. 🌐 **Translations**: Help translate guides into other languages so more developers can benefit.

---

## 🛠️ Step-by-Step Contribution Workflow

### 1. Fork and Clone
Fork the repository on GitHub, then clone your fork locally:

```bash
git clone https://github.com/<your-username>/Zero-to-GitHero.git
cd Zero-to-GitHero
```

### 2. Create a Feature Branch
Create a descriptive branch for your changes:

```bash
git switch -c docs/improve-git-stash
# or using classic syntax
git checkout -b docs/improve-git-stash
```

*Branch naming conventions:*
- `docs/<description>` for documentation improvements or additions
- `fix/<description>` for bug or typo fixes
- `feat/<description>` for new guides or tools

### 3. Make Your Changes
Follow these writing and style rules:
- **Accuracy First:** Test every command in a disposable test repository before submitting it.
- **Modern Commands:** Teach modern commands (`git switch`, `git restore`) alongside historical ones (`git checkout`, `git reset`).
- **Cross-Platform:** When shell commands differ, provide both Windows PowerShell and Unix (Git Bash / macOS) versions.
- **Safety Alerts:** Always flag destructive commands (like `git reset --hard` or `git push --force`) with clear warning callouts.
- **Formatting:** Use standard GitHub Flavored Markdown (GFM). Use fenced code blocks with appropriate language tags (`bash`, `powershell`, `yaml`, `mermaid`).

### 4. Commit Your Changes
We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```bash
git commit -m "docs(stash): add -u and -p interactive examples"
```

Common prefixes:
- `docs:` Documentation only changes
- `fix:` Correction of errors, typos, or inaccurate commands
- `feat:` Addition of new chapters, tools, or cheat sheets
- `chore:` Maintenance, repository meta files, or workflow changes

### 5. Push and Open a Pull Request
Push your branch to your GitHub fork:

```bash
git push -u origin docs/improve-git-stash
```

Then visit the GitHub repository and click **Compare & pull request**. Please fill out the provided Pull Request template.

---

## 📋 Pull Request Review Process

1. **Automated Checks:** Our CI checks verify markdown formatting and link integrity.
2. **Review:** Maintainers will review your PR and may suggest improvements.
3. **Merge:** Once approved, your PR will be squashed and merged into the main repository. You will be credited in the release notes!

Thank you for helping make Zero-to-GitHero the most accessible and practical Git resource on the web! 🚀

