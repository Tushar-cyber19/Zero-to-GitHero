# 🛡️ GitHub Security & Repository Management

## 🎯 Topic: Enterprise Governance, Rulesets, CODEOWNERS, Dependabot & Secret Scanning

A public repository or team codebase requires more than just Git commands: it requires security guardrails, automated dependency vulnerability alerts, automated code scanning, and policy enforcement to prevent accidental leaks and breaking changes.

---

## 🌟 What You’ll Learn

By the end of this guide, you’ll master:
- ✅ Modern **Repository Rulesets** vs Classic Branch Protection
- ✅ Automating code reviews using a `CODEOWNERS` file
- ✅ Setting up **Dependabot** for automated vulnerability patching
- ✅ Enabling **Secret Scanning** and Push Protection to stop credential leaks
- ✅ Running automated static security analysis with **CodeQL**
- ✅ Standardizing community input with Issue Forms and PR Templates
- ✅ Developing in cloud environments using **GitHub Codespaces**

---

## 🏰 1. Repository Rulesets vs Branch Protection

GitHub recently introduced **Repository Rulesets** as the modern replacement for classic Branch Protection Rules. Rulesets allow you to enforce branch policies across single branches or multiple repositories simultaneously.

### 🛡️ Recommended Ruleset for Production (`main`):
1. Navigate to **Settings ⚙️** → **Rules** → **Rulesets** → **New branch ruleset**.
2. Name: `Production Guardrails`.
3. Target: `Include default branch`.
4. Enable the following protections:
   - 🔒 **Restrict deletions:** Prevents anyone from deleting the production branch.
   - 🔒 **Block force pushes:** Completely prohibits `git push --force`.
   - 🔒 **Require a pull request before merging:**
     - Require at least **1 approving review**.
     - Dismiss stale pull request approvals when new commits are pushed.
     - Require review from Code Owners.
   - 🔒 **Require status checks to pass:** Select your CI/CD test workflow (e.g. `Build, Lint & Test`).
   - 🔒 **Require linear history:** Enforces squash or rebase merges to prevent messy merge commits.

---

## 👥 2. Automating Reviews with `CODEOWNERS`

The `CODEOWNERS` file automatically assigns reviewers to pull requests based on the specific files or directories modified.

### Setup:
Create a file at `.github/CODEOWNERS`:

```text
# Global owner for the entire repository
* @Tushar-cyber19

# Security team owns authentication and security workflows
/auth/              @security-team
.github/workflows/  @devops-lead

# Database specialists own migrations
/migrations/        @database-admin

# Docs team owns markdown documentation
*.md                @docs-team
```

When someone submits a PR modifying any file matching these patterns, GitHub automatically requests reviews from the specified teams or users!

---

## 🤖 3. Dependabot: Automated Vulnerability & Version Updates

Vulnerabilities in open-source third-party dependencies are one of the most common security attack vectors. GitHub Dependabot automatically monitors your dependencies and opens Pull Requests with version upgrades.

### Configuration (`.github/dependabot.yml`):

```yaml
version: 2
updates:
  # Check npm dependencies weekly
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
    open-pull-requests-limit: 5

  # Check GitHub Actions versions monthly
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "monthly"
```

### Dependabot Alerts:
In **Security → Dependabot**, GitHub flags known CVE vulnerabilities in your packages, rating them by severity (Critical, High, Moderate, Low) and providing one-click automated fix PRs.

---

## 🔑 4. Secret Scanning & Push Protection

Exposing an AWS secret key, OpenAI API key, or GitHub token in a public repository can lead to compromised infrastructure within seconds.

### How to Enable:
1. Go to **Settings ⚙️** → **Code security and analysis**.
2. Enable **Secret scanning**.
3. Enable **Push protection**.

### What Push Protection Does:
If a developer accidentally runs `git push` on a commit containing a recognized credential (such as an AWS access token or GitHub PAT), **GitHub intercepts the push and rejects it on the spot**, preventing the secret from ever touching GitHub servers!

---

## 🔍 5. Automated Static Security Scanning (CodeQL)

**CodeQL** is GitHub's semantic code analysis engine. It treats your code as data, searching for SQL injection, cross-site scripting (XSS), memory corruption, and security antipatterns.

### Enable Default Setup:
1. Navigate to **Settings ⚙️** → **Code security and analysis**.
2. Under **Code scanning**, click **Set up → Default**.
3. GitHub automatically runs CodeQL analysis on every Pull Request and alert you of vulnerabilities before code is merged into production!

---

## ☁️ 6. Instant Dev Environments: GitHub Codespaces

**GitHub Codespaces** provides a complete, cloud-hosted Visual Studio Code development environment accessible directly from your browser or local VS Code.

### Why Developers Love Codespaces:
- **Zero Local Setup:** No need to install Node, Python, Docker, or tools on a new laptop.
- **Configured via Code:** Controlled by `.devcontainer/devcontainer.json`.
- **Pre-configured Extensions & Ports:** Automatic port forwarding for web servers.

### Launching a Codespace:
Click the green **Code** button on any GitHub repository → select the **Codespaces** tab → click **Create codespace on main**. You will be dropped into a fully running terminal and editor in under 30 seconds!

---

## 📚 Security & Governance Checklist

- [ ] Repository Ruleset active on `main` branch.
- [ ] Direct pushes to `main` blocked.
- [ ] At least 1 review and status checks required to merge.
- [ ] `.github/CODEOWNERS` configured for key directory paths.
- [ ] `.github/dependabot.yml` active for daily/weekly dependency audits.
- [ ] Secret Scanning and Push Protection enabled.
- [ ] CodeQL Automated Code Scanning active.
- [ ] Issue and PR templates configured to standardize incoming contributions.

---

## 🏆 Recap & Next Steps

You now possess enterprise-grade knowledge to protect, govern, and automate code quality across your GitHub repositories!

➡️ **Next Guide:** [Hosting Websites with GitHub Pages](Hosting%20Websites%20with%20GitHub%20Pages.md) — Deploy static web applications for free with custom domains and SSL.

