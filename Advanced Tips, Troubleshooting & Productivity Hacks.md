# 🧠 **Advanced Tips, Troubleshooting & Productivity Hacks **

---

## 🎯 **Objective**

This final file will help you go **beyond the basics** — focusing on productivity shortcuts, common troubleshooting fixes, and professional-level Git habits.
It’s your **GitHub mastery toolkit** 🧰 — everything pros do to save time, stay organized, and avoid mistakes.

---

## ⚙️ **1. Productivity Boosters for Git & GitHub**

### ⌨️ **Command Shortcuts**

| Command  | Description               |
| :------- | :------------------------ |
| `git st` | Alias for `git status`    |
| `git co` | Alias for `git checkout`  |
| `git cm` | Alias for `git commit -m` |
| `git br` | Alias for `git branch`    |
| `git lg` | Compact log view          |

🪄 **Example:**

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.cm "commit -m"
git config --global alias.br branch
git config --global alias.lg "log --oneline --graph --decorate --all"
```

Now, type `git lg` to see a colorful, simple commit history 🌈

---

## 📁 **2. Clean & Organized Repositories**

Keep your project structured like a pro 🧑‍💻

```
project/
├── src/           # Source code
├── docs/          # Documentation
├── assets/        # Images, icons, etc.
├── tests/         # Test files
├── .gitignore     # Ignore unnecessary files
└── README.md      # Project overview
```

### 💡 Pro Tip:

Add a `.gitignore` to prevent clutter from logs, temp files, or build artifacts.

Example `.gitignore` for Node.js:

```
node_modules/
dist/
.env
logs/
```

---

## 🧰 **3. Troubleshooting Common Git Problems**

### ❌ **Problem 1: Wrong Commit Message**

**Fix:**

```bash
git commit --amend -m "New commit message"
```

---

### ⚠️ **Problem 2: Accidentally Committed a File**

**Fix:**

```bash
git reset HEAD <filename>
```

---

### 🔁 **Problem 3: Pushed Wrong Code**

**Fix:**

```bash
git revert <commit_id>
```

This creates a new commit that undoes the previous one — safe and clean.

---

### 🔒 **Problem 4: Permission Denied (SSH)**

**Fix:**

1. Generate SSH key:

   ```bash
   ssh-keygen -t ed25519 -C "you@example.com"
   ```
2. Copy the public key:

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
3. Add it to **GitHub → Settings → SSH and GPG keys**

---

### 🧩 **Problem 5: Merge Conflicts**

**Fix:**

1. Open the conflicted file.
2. Look for:

   ```
   <<<<<<< HEAD
   Your changes
   =======
   Incoming changes
   >>>>>>> branch-name
   ```
3. Edit manually → save →

   ```bash
   git add .
   git commit
   ```

✅ Conflict resolved!

---

## 🪄 **4. Useful Git Config Tweaks**

Set your preferred text editor:

```bash
git config --global core.editor "code --wait"
```

Auto-colorize Git output:

```bash
git config --global color.ui auto
```

Show last commit info when you run `git status`:

```bash
git config --global status.showUntrackedFiles all
```

---

## 🧠 **5. Smart Commit Practices**

| 💬 Rule                     | ✅ Example                              |
| :-------------------------- | :------------------------------------- |
| Keep messages short & clear | `git commit -m "Add login validation"` |
| Use present tense           | “Fix bug” not “Fixed bug”              |
| Group related changes       | Don’t mix unrelated edits              |
| Commit often                | Easier rollback & history tracking     |
| Avoid committing secrets    | Never commit `.env` or API keys        |

---

## 🧹 **6. Keeping Repositories Clean**

Remove untracked files:

```bash
git clean -fd
```

Prune old branches:

```bash
git branch --merged
git branch -d old-branch
```

Clear Git cache:

```bash
git rm -r --cached .
```

---

## 🧩 **7. Advanced Git Logs & Diffs**

### 🔍 View commit graph:

```bash
git log --oneline --graph --decorate --all
```

### 🕵️ Compare commits:

```bash
git diff commit1 commit2
```

### 🧾 View changes by author:

```bash
git log --author="Tushar" --oneline
```

---

## 💡 **8. Git Hooks – Automation Magic 🪄**

Git hooks are scripts that run automatically on specific actions.

Examples:

| Hook          | When it runs   | Example use                |
| :------------ | :------------- | :------------------------- |
| `pre-commit`  | Before commit  | Run tests or linting       |
| `post-commit` | After commit   | Notify a team or log event |
| `pre-push`    | Before pushing | Run build checks           |

🧩 Example:
Create `.git/hooks/pre-commit`:

```bash
#!/bin/bash
npm test
```

Then make it executable:

```bash
chmod +x .git/hooks/pre-commit
```

---

## 🧩 **9. GitHub Power Tools**

| Tool                  | Purpose                                 |
| :-------------------- | :-------------------------------------- |
| **GitHub CLI (`gh`)** | Manage repos, PRs, issues from terminal |
| **GitHub Actions**    | Automate testing and deployment         |
| **Dependabot**        | Automatically update dependencies       |
| **CodeQL**            | Find security issues in code            |
| **GitHub Projects**   | Kanban-style boards for task management |

---

## 🚀 **10. Security & Maintenance Tips**

✅ Use `.gitignore` to hide sensitive files
✅ Rotate SSH keys regularly
✅ Don’t push API keys or credentials
✅ Use branch protection rules for main branches
✅ Keep dependencies updated with Dependabot

---

## 🧭 **11. When to Rebase vs Merge**

| Situation                                | Use               |
| :--------------------------------------- | :---------------- |
| You want a linear history                | `git rebase`      |
| You want to preserve commit history      | `git merge`       |
| You are syncing feature branch with main | `git rebase main` |

⚠️ Never rebase public branches others are using!

---

## 🧩 **12. Backup & Restore**

Create a mirror backup:

```bash
git clone --mirror https://github.com/user/repo.git
```

Restore from backup:

```bash
git clone --bare repo.git
```

---

## 🏁 **Conclusion**

🎉 You’ve completed the **Git & GitHub Mastery Journey**!
From installation to automation, you now know how to:

* Collaborate efficiently
* Manage code like a pro
* Troubleshoot issues
* Automate workflows

Keep exploring open-source, contribute often, and stay curious 💫
Your **GitHub profile** is your digital portfolio — make every commit count 🖋️

---

➡️ **Next Step:** [README](README.md) to review the complete guide overview and contribute to the project.
