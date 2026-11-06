# ⚡ Git Commands Cheat Sheet

A concise, high-density reference sheet for daily Git usage.

---

## 🚀 Setup & Config

```bash
# Global configuration
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
git config --global core.autocrlf true         # Windows
git config --global core.autocrlf input        # macOS / Linux

# Useful aliases
git config --global alias.st "status -sb"
git config --global alias.lg "log --oneline --graph --decorate --all"
git config --global alias.cm "commit -m"
```

---

## 🛠️ Daily Workflow

```bash
# Initialize & check status
git init
git status -sb

# Staging
git add <file>
git add .
git add -p <file>                # Interactive hunk staging

# Committing
git commit -m "feat: description"
git commit --amend --no-edit     # Fix up last commit (unpushed only!)

# Diffing
git diff                         # Working tree vs staging
git diff --staged                # Staged vs HEAD
git diff branchA..branchB        # Compare two branches
```

---

## 🌿 Branching & Merging

```bash
# Modern navigation (Git 2.23+)
git switch <branch>              # Switch to branch
git switch -c <new-branch>       # Create & switch to new branch
git switch -                     # Switch to previous branch

# Inspecting & Deleting
git branch -vv                   # Detailed tracking status
git branch -d <branch>           # Safe delete (merged only)
git branch -D <branch>           # Force delete (unmerged)

# Merging
git merge <branch>               # Fast-forward or 3-way merge
git merge --no-ff <branch>       # Force a merge commit
git merge --abort                # Cancel conflicted merge
```

---

## ☁️ Remotes & Sync

```bash
# Setup remotes
git remote add origin <url>
git remote -v
git remote set-url origin <new-url>

# Syncing
git push -u origin <branch>      # Push & track
git push                         # Push tracked branch
git fetch --prune                # Fetch & remove deleted remote branches
git pull --rebase origin main    # Pull without creating merge bubbles
git push --force-with-lease      # Safe force push
```

---

## 🧳 Stashing & Moving

```bash
# Stashing
git stash push -u -m "msg"       # Stash with untracked files and label
git stash list
git stash pop                    # Apply & remove latest
git stash apply stash@{0}        # Apply without removing
git stash branch <new-branch>    # Turn stash into a new branch

# Files
git rm <file>                    # Delete file & stage removal
git rm --cached <file>           # Stop tracking file (keep on disk)
git mv <old> <new>               # Rename tracked file
```

