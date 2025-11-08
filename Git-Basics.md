### 📘 `Git-Basics.md`

````markdown
# Git Basics

This section introduces the most commonly used Git commands.  
Each command includes a short explanation, example, and expected output so beginners can understand it easily.

---

## 1. Initialize a Repository

**Command:**
```bash
git init
````

**Use:**
Creates a new Git repository in your current project folder.

**Example:**

```bash
mkdir my-project
cd my-project
git init
```

**Output:**

```
Initialized empty Git repository in /my-project/.git/
```

---

## 2. Check Repository Status

**Command:**

```bash
git status
```

**Use:**
Shows which files are staged, unstaged, or untracked.

**Example:**

```bash
git status
```

**Output:**

```
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        index.html
```

---

## 3. Add Files to Staging Area

**Command:**

```bash
git add <filename>
```

**Use:**
Moves files from the working directory to the staging area.

**Example:**

```bash
git add index.html
```

**Output:**

```
Changes to be committed:
  new file:   index.html
```

> 💡 Tip: Use `git add .` to stage *all* files at once.

---

## 4. Commit Changes

**Command:**

```bash
git commit -m "your commit message"
```

**Use:**
Saves your staged changes with a short descriptive message.

**Example:**

```bash
git commit -m "Added homepage structure"
```

**Output:**

```
[main 1a2b3c4] Added homepage structure
 1 file changed, 10 insertions(+)
 create mode 100644 index.html
```

---

## 5. View Commit History

**Command:**

```bash
git log
```

**Use:**
Displays the commit history for the repository.

**Example:**

```bash
git log
```

**Output:**

```
commit 1a2b3c4 (HEAD -> main)
Author: Tushar Manaktala <you@example.com>
Date:   Sun Oct 26 10:00:00 2025 +0530

    Added homepage structure
```

---

## 6. Create and Switch Branch

**Command:**

```bash
git checkout -b <branch-name>
```

**Use:**
Creates a new branch and switches to it.

**Example:**

```bash
git checkout -b feature-login
```

**Output:**

```
Switched to a new branch 'feature-login'
```

---

## 7. Switch Between Branches

**Command:**

```bash
git checkout <branch-name>
```

**Example:**

```bash
git checkout main
```

**Output:**

```
Switched to branch 'main'
```

---

## 8. View Branches

**Command:**

```bash
git branch
```

**Example:**

```bash
git branch
```

**Output:**

```
* main
  feature-login
```

---

## 9. Remove a File from Git Tracking

**Command:**

```bash
git rm <filename>
```

**Example:**

```bash
git rm oldfile.txt
```

**Output:**

```
rm 'oldfile.txt'
```

---

## 10. Ignore Files (Optional)

Create a `.gitignore` file to exclude unnecessary files (like logs or environment files).

**Example `.gitignore`:**

```
node_modules/
.env
*.log
```

---

✅ **Summary**

* `git init` → start a repository
* `git add` → stage files
* `git commit` → save changes
* `git branch` & `git checkout` → manage branches
* `.gitignore` → ignore unwanted files

---

Next: [GitHub-Commands.md →](./GitHub-Commands.md)