# 🚑 Git Rescue Handbook

## 🎯 Topic: Recovering from Disasters, Reflog Mastery & Undoing Mistakes

Even the most senior software engineers make Git mistakes: accidentally running `git reset --hard`, deleting the wrong branch, committing to `main` by mistake, or dropping an unpushed commit.

The good news: **Git almost never permanently deletes committed work.** As long as a commit was recorded locally, Git keeps it in an internal safety net called the **Reflog** for at least 30 to 90 days.

This handbook is your emergency field manual when things go wrong.

---

## 🌟 What You’ll Learn

By the end of this emergency guide, you’ll know how to:
- ✅ Recover lost commits after an accidental `git reset --hard`
- ✅ Restore a branch that was accidentally deleted
- ✅ Master the Git reference log (`git reflog`)
- ✅ Rescue changes committed to the wrong branch
- ✅ Undo a bad merge or interactive rebase
- ✅ Safely push rewritten history with `--force-with-lease`
- ✅ Understand destructive commands and when data is truly gone

---

## 🧭 The Emergency Cheat Table

| What Happened | Immediate Rescue Command |
|---|---|
| Ran `git reset --hard` by mistake | `git reflog` → find hash → `git switch -c recovery <hash>` |
| Deleted a branch with `git branch -D` | `git reflog` → find branch tip hash → `git switch -c <branch> <hash>` |
| Committed to `main` instead of a feature branch | `git branch my-feature` → `git reset --hard HEAD~1` |
| Accidentally amended the wrong commit | `git reflog` → find hash before amend → `git reset --hard <hash>` |
| Stashed changes disappeared | `git fsck --lost-found` or `git log -g --walk-reflogs --grep="WIP"` |
| Pushed bad code to a shared branch | `git revert <bad-commit-hash>` |
| In the middle of a disastrous merge | `git merge --abort` |
| In the middle of a disastrous rebase | `git rebase --abort` |

---

## 🔍 1. `git reflog`: The Ultimate Git Time Machine

Every time `HEAD` moves in your local repository — whether by commit, checkout, switch, rebase, merge, or reset — Git records the previous position in the **reference log (reflog)**.

```bash
git reflog
```

✅ **Output Example:**
```text
7b3e1a2 (HEAD -> main) HEAD@{0}: reset: moving to HEAD~2
4c8d9e0 HEAD@{1}: commit: feat: complete stripe payment integration
1a2b3c4 HEAD@{2}: commit: feat: add stripe webhooks
9e8f7a6 HEAD@{3}: checkout: moving from feature/cart to main
```

### 🧠 How to Read Reflog Output:
- `HEAD@{0}`: Where your HEAD is right now.
- `HEAD@{1}`: Where HEAD was 1 step ago.
- `HEAD@{2}`: Where HEAD was 2 steps ago.
- The 7-character hash on the left is the exact commit SHA!

---

## 🚨 Disaster 1: "I ran `git reset --hard` and lost my commits!"

### Scenario:
You accidentally moved your branch back 2 commits with `git reset --hard HEAD~2`. Your recent work seems to have vanished from `git log`.

### The Rescue Steps:
1. Open your terminal and view your local history:
   ```bash
   git reflog
   ```
2. Find the entry right before the reset occurred:
   ```text
   4c8d9e0 HEAD@{1}: commit: feat: complete stripe payment integration
   ```
3. Create a recovery branch pointing directly to that commit:
   ```bash
   git switch -c rescued-work 4c8d9e0
   ```
4. Verify your commits:
   ```bash
   git log --oneline
   ```
🎉 **Success:** All your commits, files, and history are 100% restored!

---

## 🚨 Disaster 2: "I accidentally deleted a branch!"

### Scenario:
You ran `git branch -D feature/analytics` thinking it was merged, but it still contained unmerged commits.

### The Rescue Steps:
1. Run `git reflog`:
   ```bash
   git reflog
   ```
2. Look for the last commit made on that branch:
   ```text
   8f9a0b1 HEAD@{4}: commit: feat(analytics): track user conversions
   ```
3. Re-create the branch from that exact commit:
   ```bash
   git switch -c feature/analytics 8f9a0b1
   ```
🎉 **Success:** The deleted branch is immediately recreated with all its commits intact!

---

## 🚨 Disaster 3: "I committed directly to `main` instead of a new branch!"

### Scenario:
You made 3 commits intended for a new feature, but realized you were on `main`.

### The Rescue Steps:
```bash
# 1. Create a new branch pointing to your current commits
git branch feature/my-cool-feature

# 2. Reset the local main branch back 3 commits
git reset --hard HEAD~3

# 3. Switch to your feature branch
git switch feature/my-cool-feature
```
Now `main` is clean, and your 3 commits are safely on `feature/my-cool-feature`!

---

## 🚨 Disaster 4: "My rebase went terribly wrong!"

### Scenario:
During an interactive rebase (`git rebase -i`), you hit confusing conflicts, deleted the wrong commits, or feel lost.

### Option A: Abort if still in progress:
```bash
git rebase --abort
```

### Option B: Undo a completed bad rebase:
If the rebase already finished:
1. Run `git reflog`.
2. Look for the entry labeled `rebase (start)`:
   ```text
   3a4b5c6 HEAD@{5}: rebase (start): checkout main
   d7e8f9a HEAD@{6}: commit: feat: work before rebase
   ```
3. Reset your branch to the state right before the rebase started:
   ```bash
   git reset --hard HEAD@{6}
   ```

---

## ⚠️ Destructive Commands: When Is Data TRULY Lost?

Git protects committed data, but cannot protect data that was **never committed**.

| Command | Can it be recovered? | Why? |
|---|---|---|
| `git restore <file>` | ❌ **No** | Discards unstaged working directory changes. Git never saved a snapshot. |
| `git checkout -- <file>` | ❌ **No** | Same as above. Working tree edits are overwritten. |
| `git clean -fd` | ❌ **No** | Permanently deletes untracked files from disk. |
| `git reset --hard` | ✅ **Yes** | Any committed work can be recovered via `git reflog`. |
| `git branch -D` | ✅ **Yes** | Commit objects still exist in `.git/objects` and `git reflog`. |
| `git stash drop` | ✅ **Yes** (within 30 days) | Commit hash can be found with `git fsck --lost-found`. |

---

## 🛡️ Best Practices to Prevent Disasters

1. **Commit frequently:** Small, frequent commits are easy to rescue. Uncommitted code in your working directory cannot be salvaged by reflog.
2. **Use `git stash -u`:** Always stash including untracked files before experimenting.
3. **Use `--force-with-lease`:** Never use plain `--force` when pushing.
4. **Inspect with dry-runs:** Always run `git clean -n` before `git clean -f`.

---

## 🏆 Recap & Next Steps

Whenever disaster strikes, take a breath, don't close your terminal, and remember: **`git reflog` is your best friend.**

➡️ **Next Guide:** [Advanced Git - Bisect, Worktrees, Submodules & LFS](Advanced%20Git%20-%20Bisect,%20Worktrees,%20Submodules%20&%20LFS.md) — Master binary search debugging, parallel worktrees, external submodules, and large file storage.

