# 🧠 Git Commands with Examples

## 🎯 Topic: Basic Git Commands for Daily Use

---

## 🌟 What You’ll Learn

By the end of this file, you’ll understand and practice:
✅ Initializing and checking repo status
✅ Adding and committing changes
✅ Creating, switching, and merging branches
✅ Connecting to remotes
✅ Pushing and pulling updates
✅ Undoing mistakes safely

---

## ⚙️ 1. `git init` — Initialize a Repository

Creates a new local Git repository in your current directory.

```bash
git init
```

✅ **Result:**

```
Initialized empty Git repository in /path/to/folder/.git/
```

📘 *Use this command in the folder where your project is stored.*

---

## 🧐 2. `git status` — Check Repository Status

Shows which files are changed, staged, or untracked.

```bash
git status
```

✅ **Output Example:**

```
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        index.html
```

---

## 🗃️ 3. `git add` — Stage Files for Commit

Adds files to the staging area before committing.

```bash
git add filename.txt
```

✨ Add all files:

```bash
git add .
```

✅ **Result:**

```
Changes to be committed:
  new file: filename.txt
```

---

## 💾 4. `git commit` — Save Your Changes

Commits staged changes with a message.

```bash
git commit -m "Added homepage"
```

✅ **Result:**

```
[main 5a0e23d] Added homepage
 1 file changed, 10 insertions(+)
 create mode 100644 index.html
```

---

## 🕰️ 5. `git log` — View Commit History

Displays a list of all commits in the current branch.

```bash
git log
```

✅ **Output Example:**

```
commit 5a0e23df8b (HEAD -> main)
Author: Tushar Manaktala <tushar@example.com>
Date:   Sat Nov 8 2025

    Added homepage
```

💡 Press **Q** to exit log view.

---

## 🌿 6. `git branch` — Manage Branches

### 📌 Create a new branch:

```bash
git branch feature-1
```

### 🔁 Switch to another branch:

```bash
git checkout feature-1
```

### 🧾 View all branches:

```bash
git branch
```

✅ **Output Example:**

```
* main
  feature-1
```

---

## 🔀 7. `git merge` — Merge Branches

Merges another branch into the current one.

```bash
git merge feature-1
```

✅ **Result:**

```
Updating 5a0e23d..b3a29ac
Fast-forward
 index.html | 10 ++++++++++
```

💡 *If there’s a conflict, Git will ask you to resolve it manually.*

---

## 🌎 8. `git remote` — Manage Remote Repositories

### Add a remote repository:

```bash
git remote add origin https://github.com/username/github-guide.git
```

### Verify remote connections:

```bash
git remote -v
```

✅ **Output Example:**

```
origin  https://github.com/username/github-guide.git (fetch)
origin  https://github.com/username/github-guide.git (push)
```

---

## ⬆️ 9. `git push` — Upload Changes to GitHub

Push local commits to the remote repository.

```bash
git push origin main
```

✅ **Result:**

```
Enumerating objects: 5, done.
Writing objects: 100% (5/5), done.
To https://github.com/username/github-guide.git
```

---

## ⬇️ 10. `git pull` — Download Latest Changes

Fetches and merges changes from the remote repository.

```bash
git pull origin main
```

✅ **Result:**

```
Updating a12b3cd..d45e6f7
Fast-forward
 index.html | 2 ++
```

---

## 📥 11. `git clone` — Copy a Repository

Creates a copy of an existing remote repository.

```bash
git clone https://github.com/username/github-guide.git
```

✅ **Result:**

```
Cloning into 'github-guide'...
```

---

## ⚙️ 12. `git config --list` — View Git Configuration

Lists your Git settings and user details.

```bash
git config --list
```

✅ **Result:**

```
user.name=Tushar Manaktala
user.email=tushar@example.com
core.editor=code --wait
```

---

## 🧹 13. `git reset` / `git checkout` — Undo Changes

### Undo staged files (before commit):

```bash
git reset filename.txt
```

### Revert file to last committed state:

```bash
git checkout -- filename.txt
```

💡 *Use carefully — this will discard local changes.*

---

## 🔍 14. `git diff` — See What Changed

Compare differences between working directory and last commit.

```bash
git diff
```

✅ **Example Output:**

```
- old line
+ new line
```

---

## 📚 15. `git help` — Get Command Help

Need help with a specific command?

```bash
git help commit
```

Or see all options:

```bash
git help -a
```

---

## 🧩 Quick Reference Table

| Command        | Description         | Example                   |
| -------------- | ------------------- | ------------------------- |
| `git init`     | Initialize new repo | `git init`                |
| `git status`   | Check repo status   | `git status`              |
| `git add`      | Stage changes       | `git add .`               |
| `git commit`   | Commit changes      | `git commit -m "Message"` |
| `git log`      | View history        | `git log`                 |
| `git branch`   | Manage branches     | `git branch feature`      |
| `git checkout` | Switch branch       | `git checkout main`       |
| `git merge`    | Merge branches      | `git merge dev`           |
| `git remote`   | Manage remotes      | `git remote -v`           |
| `git push`     | Upload commits      | `git push origin main`    |
| `git pull`     | Download updates    | `git pull origin main`    |
| `git clone`    | Clone repo          | `git clone <URL>`         |
| `git diff`     | Compare changes     | `git diff`                |
| `git reset`    | Unstage files       | `git reset`               |

---

## 🎉 Recap

You’ve learned all essential Git commands!
Now you can:
💡 Initialize a repository
💡 Commit changes safely
💡 Work with branches
💡 Push and pull updates from GitHub

---

➡️ **Next Step:** [Branching and Merging](Branching%20and%20Merging.md) to learn how to work on multiple features, merge them, and handle conflicts like a pro.
