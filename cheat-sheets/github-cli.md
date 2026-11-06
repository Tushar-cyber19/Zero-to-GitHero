# ⚡ GitHub CLI (`gh`) Cheat Sheet

Terminal-first productivity reference for GitHub CLI commands.

---

## 🔐 Auth & Status

```bash
gh auth login                    # Authenticate interactively
gh auth status                   # Check login status & token scopes
gh browse                        # Open current repository in browser
```

---

## 🌿 Pull Requests

```bash
gh pr create                     # Create PR interactively
gh pr create --generate-notes    # Create PR with automated notes
gh pr list                       # List open pull requests
gh pr checkout <number>          # Checkout PR branch locally
gh pr diff <number>              # View PR diff in terminal
gh pr checks                     # View CI/CD build status
gh pr review --approve -b "LGTM" # Approve PR
gh pr merge --squash --delete-branch # Squash-merge and delete branch
```

---

## 🐛 Issues

```bash
gh issue create                  # Create an issue interactively
gh issue list                    # View active issues
gh issue view <number>           # Read issue details & comments
gh issue close <number>          # Close an issue
```

---

## 🚀 Releases & Workflows

```bash
# Releases
gh release create v1.0.0 --generate-notes # Create release with auto notes
gh release list                           # List all releases
gh release download v1.0.0                # Download release assets

# CI/CD Workflows
gh run list                               # View recent workflow runs
gh run view <run-id>                      # Inspect a specific run
gh run view <run-id> --log-failed         # View failed CI logs
gh run rerun <run-id> --failed            # Rerun only failed jobs
```

---

## 🔒 Secrets & Rulesets

```bash
gh ruleset list                  # List active branch rulesets
gh secret list                   # List configured secrets
gh secret set API_KEY            # Securely set secret
gh repo sync                     # Sync fork with upstream repo
```

