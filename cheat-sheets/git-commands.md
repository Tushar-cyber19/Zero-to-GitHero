# Git Commands Cheat Sheet

A concise reference sheet for daily Git usage.

---

## Setup & Config

```bash
# User identity
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main

# Line ending handling
git config --global core.autocrlf true         # Windows
git config --global core.autocrlf input        # macOS / Linux

# Useful aliases
git config --global alias.st "status -sb"
git config --global alias.lg "log --oneline --graph --decorate --all"
git config --global alias.cm "commit -m"
```

---

## Daily Workflow

```bash
# Initialize & inspect status
git init
git status -sb

# Staging
git add <file>
git add .
git add -p <file>                # Interactive hunk staging

# Committing
git commit -m "feat: description"
git commit --amend --no-edit     # Amend previous unpushed commit

# Comparing
git diff                         # Working tree vs staging
git diff --staged                # Staged changes vs HEAD
git diff branchA..branchB        # Compare two branches
```

---

## Branching & Merging

```bash
# Modern navigation
git switch <branch>              # Switch to branch
git switch -c <new-branch>       # Create and switch to new branch
git switch -                     # Switch to previously active branch

# Inspecting & Deleting
git branch -vv                   # Tracking status and ahead/behind counts
git branch -d <branch>           # Safe delete (merged branches)
git branch -D <branch>           # Force delete (unmerged branches)

# Merging
git merge <branch>               # Fast-forward or 3-way merge
git merge --no-ff <branch>       # Enforce merge commit creation
git merge --abort                # Cancel conflicted merge
```

---

## Remotes & Sync

```bash
# Remote management
git remote add origin <url>
git remote -v
git remote set-url origin <new-url>

# Synchronization
git push -u origin <branch>      # Push and configure upstream tracking
git push                         # Push tracked branch
git fetch --prune                # Fetch and delete stale remote tracking branches
git pull --rebase origin main    # Pull and rebase to prevent merge bubbles
git push --force-with-lease      # Safe force push
```

---

## Stashing & File Operations

```bash
# Stash operations
git stash push -u -m "message"   # Stash including untracked files with label
git stash list                   # View stash stack
git stash pop                    # Apply and drop latest stash
git stash apply stash@{0}        # Apply stash without dropping
git stash branch <new-branch>    # Turn stash into a new branch

# File operations
git rm <file>                    # Remove file from disk and stage
git rm --cached <file>           # Stop tracking file (keep on disk)
git mv <old> <new>               # Rename tracked file
```
