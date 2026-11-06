# ⚡ GitHub CLI (Command-Line Power)

## 🎯 Topic: Terminal-First GitHub Workflow & Automation

The **GitHub CLI (`gh`)** brings the full power of GitHub into your terminal. Instead of constantly context-switching between your terminal and browser tabs to open pull requests, review diffs, trigger CI/CD runs, publish releases, or configure secrets, you can execute everything from the command line.

---

## 🌟 What You’ll Learn

By the end of this guide, you’ll master:
- ✅ Installing and authenticating `gh` with proper OAuth scopes
- ✅ Creating, cloning, and synchronizing forks (`gh repo sync`)
- ✅ End-to-end Pull Request workflows (`gh pr create`, `checkout`, `diff`, `merge`)
- ✅ Managing GitHub Releases with auto-generated release notes (`gh release`)
- ✅ Monitoring and debugging GitHub Actions workflow runs (`gh run view --log`)
- ✅ Inspecting repository rulesets and branch policies (`gh ruleset list`)
- ✅ Managing encrypted environment secrets (`gh secret set / list`)
- ✅ JSON formatting and jq filtering for terminal automation

---

## ⚙️ 1. Installation & Authentication

### 📥 Install on Your Platform:
- **Windows (winget):** `winget install --id GitHub.cli`
- **Windows (scoop):** `scoop install gh`
- **macOS (Homebrew):** `brew install gh`
- **Linux (Debian/Ubuntu):**
  ```bash
  type -p curl >/dev/null || sudo apt install curl -y
  curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
  echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
  sudo apt update && sudo apt install gh -y
  ```

### 🔐 Authenticate with GitHub:
```bash
gh auth login
```
Follow the interactive prompts:
1. Select **GitHub.com**
2. Choose your preferred protocol (**HTTPS** or **SSH**)
3. Choose **Login with a web browser** (or paste an existing Personal Access Token)
4. Confirm authentication with one-time code.

### Verify connection:
```bash
gh auth status
```

---

## 📦 2. Repository & Fork Management

### Create a new repository on GitHub and link it locally:
```bash
gh repo create my-project --public --source=. --remote=origin --push
```

### Fork an open-source project and clone it in one command:
```bash
gh repo fork torvalds/linux --clone
```

### 🔄 Synchronize your fork with upstream:
Keep your fork completely updated with the upstream repository without typing manual fetch/merge commands:
```bash
gh repo sync
```

---

## 🌿 3. The Professional Pull Request Workflow

### Create a Pull Request interactively:
```bash
gh pr create
```

### Create a PR with title and body non-interactively:
```bash
gh pr create --title "feat: add user authentication" --body "Implements JWT login. Closes #42" --base main
```

### Check out a colleague's PR locally to test their code:
```bash
gh pr checkout 128
```
*(Automatically creates a local branch and checks out PR #128!)*

### View PR status and review checks:
```bash
# View checks and diff
gh pr checks
gh pr diff

# Open PR directly in default web browser
gh pr view --web
```

### Approve and Merge a PR:
```bash
# Submit an approval review
gh pr review --approve -b "LGTM! Verified locally."

# Squash and merge, then delete the branch automatically
gh pr merge --squash --delete-branch
```

---

## 🏷️ 4. Managing GitHub Releases

Creating versioned releases with release notes directly from your CLI:

### 🚀 Create a release with automatically generated changelog notes:
```bash
gh release create v1.2.0 --title "v1.2.0: Modern Git & Rescue Workflows" --generate-notes
```

### Attach compiled binary assets or zip archives to a release:
```bash
gh release create v1.2.0 ./dist/bundle.zip --generate-notes
```

### List releases:
```bash
gh release list
```

---

## 🤖 5. Inspecting GitHub Actions & CI/CD Runs

No need to open the GitHub Actions tab to see why your CI build failed!

### List recent workflow runs:
```bash
gh run list
```

✅ **Output Example:**
```text
STATUS  TITLE                   WORKFLOW  BRANCH  EVENT  ID          ELAPSED  AGE
✓       docs: fix typo          CI        main    push   9817234567  45s      5m
X       feat: add payment API   CI        dev     push   9817112233  1m12s    22m
```

### Inspect a specific run:
```bash
gh run view 9817112233
```

### 📜 View failure logs directly in terminal:
```bash
gh run view 9817112233 --log-failed
```

### Re-run a failed workflow:
```bash
gh run rerun 9817112233 --failed
```

---

## 🔒 6. Governance: Rulesets & Secrets

> [!NOTE]
> Managing secrets and rulesets requires repository **Admin** or **Maintainer** permissions.

### View configured repository rulesets:
```bash
gh ruleset list
```

### Manage repository secrets:
```bash
# List all secret names configured in repo
gh secret list

# Set a secret value securely (interactive prompt or pipe)
gh secret set STRIPE_SECRET_KEY
```

---

## 📊 7. Pro Automation: JSON Output & Scripting

Every `gh` command supports `--json` and `--jq` flags, enabling powerful custom bash/PowerShell automation scripts.

### Get open PR titles and numbers:
```bash
gh pr list --state open --json number,title --jq '.[] | "#\(.number): \(.title)"'
```

### Count open issues:
```bash
gh issue list --state open --json number --jq 'length'
```

---

## 📚 Essential GitHub CLI Reference Table

| Command | Description |
|---|---|
| `gh auth status` | Check authentication and token scopes |
| `gh repo sync` | Synchronize a fork with its upstream repository |
| `gh pr create --generate-notes` | Open a PR using commit messages as description |
| `gh pr checkout <number>` | Pull down and switch to a PR branch locally |
| `gh pr merge --squash --delete-branch`| Squash-merge PR and delete remote branch |
| `gh release create <tag> --generate-notes` | Publish release with automated release notes |
| `gh run list` | View recent CI/CD workflow runs |
| `gh run view <id> --log-failed` | Stream failed CI build logs to terminal |
| `gh secret set <name>` | Securely configure an environment secret |
| `gh browse` | Open current repository or branch in web browser |

---

## 🏆 Recap & Next Steps

With GitHub CLI, your terminal becomes an end-to-end command center for code review, release engineering, and CI/CD operations!

➡️ **Next Guide:** [Git Rescue Handbook](Git%20Rescue%20Handbook.md) — Learn how to recover deleted branches, salvage lost commits with `git reflog`, and undo disasters safely.
