# Git Disaster Recovery Cheat Sheet

Emergency commands for undoing mistakes, salvaging commits, and recovering lost work.

---

## Emergency Index

| Emergency Scenario | Recovery Command |
|---|---|
| Ran `git reset --hard` by accident | `git reflog` -> find hash -> `git switch -c recovery <hash>` |
| Deleted a branch with `git branch -D` | `git reflog` -> find branch tip -> `git switch -c <name> <hash>` |
| Committed to `main` instead of feature branch | `git branch <new-feat>` -> `git reset --hard HEAD~1` |
| Accidentally staged files | `git restore --staged <file>` |
| Discard modifications in working tree | `git restore <file>` (Irreversible) |
| Undo last commit (keep changes staged) | `git reset --soft HEAD~1` |
| Undo last commit (keep changes unstaged) | `git reset HEAD~1` |
| Roll back a commit pushed to remote | `git revert <commit-hash>` |
| Abort a conflicted merge | `git merge --abort` |
| Abort a conflicted rebase | `git rebase --abort` |
| Head is detached | `git switch -c my-recovered-branch` |

---

## Using `git reflog`

```bash
git reflog
```

Output:
```text
5a0e23d (HEAD -> main) HEAD@{0}: reset: moving to HEAD~1
1b8f42a HEAD@{1}: commit: feat: work that disappeared
```

To restore commit `1b8f42a`:
```bash
git switch -c rescue-branch 1b8f42a
```

---

## Safe History Push

Never use unconditional `--force` on shared repositories:

```bash
git push --force-with-lease
```
*Guarantees you will not overwrite anyone else's new commits on the remote branch.*
