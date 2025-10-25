---

## 📘 `01-getting-started.md`

````markdown
# 🏁 Getting Started with Git & GitHub

Welcome!  
In this section, you’ll learn what **Git** and **GitHub** are, how to install Git, and how to create your first repository.

---

## 🧩 What is Git?

**Git** is a version control system that helps developers track changes in code, revert to previous versions, and collaborate with others.

Think of it like a *time machine* for your project — you can go back in time, see who changed what, and merge everyone’s work easily.

---

## 🌐 What is GitHub?

**GitHub** is an online platform that hosts Git repositories.  
It allows developers to:
- Store their projects in the cloud
- Collaborate with others
- Review code and track issues
- Deploy websites and projects

> Example:  
> You write code on your computer using Git, and push it to GitHub to back it up or share it.

---

## ⚙️ Installing Git

### 🪟 On Windows
1. Visit [git-scm.com/downloads](https://git-scm.com/downloads)
2. Download the Windows installer
3. Follow the setup wizard and accept defaults
4. After installation, open **Git Bash**

### 🍎 On macOS
```bash
brew install git
````

### 🐧 On Linux (Ubuntu/Debian)

```bash
sudo apt install git
```

---

## 🧠 Configure Git (Important Step)

Before using Git, set your username and email.
These details are used to tag your commits.

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

✅ **Expected Output:**
*(No output if successful)*

To verify:

```bash
git config --list
```

🧾 **Example Output:**

```
user.name=Your Name
user.email=you@example.com
```

---

## 🗂️ Create Your First Git Project

Let’s make a new project folder and initialize Git inside it.

```bash
mkdir my-first-repo
cd my-first-repo
git init
```

✅ **Expected Output:**

```
Initialized empty Git repository in /path/to/my-first-repo/.git/
```

Now Git is tracking this folder — any changes here can be recorded.

---

## ✍️ Create and Track a File

```bash
echo "Hello, Git!" > hello.txt
git add hello.txt
git commit -m "Added hello.txt"
```

✅ **Expected Output:**

```
[main (root-commit) abc1234] Added hello.txt
 1 file changed, 1 insertion(+)
 create mode 100644 hello.txt
```

---

## 🌍 Connect to GitHub

### Step 1: Create a Repository

1. Go to [GitHub.com](https://github.com)
2. Click **New Repository**
3. Name it `my-first-repo`
4. Leave it **public** and **don’t** initialize with a README

### Step 2: Link Local Repo to GitHub

```bash
git remote add origin https://github.com/<your-username>/my-first-repo.git
git branch -M main
git push -u origin main
```

✅ **Expected Output:**

```
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 250 bytes | 250.00 KiB/s, done.
To https://github.com/<username>/my-first-repo.git
 * [new branch]      main -> main
```

Now your project is live on GitHub 🎉

---

## 🔄 Verify Connection

```bash
git remote -v
```

✅ **Expected Output:**

```
origin  https://github.com/<username>/my-first-repo.git (fetch)
origin  https://github.com/<username>/my-first-repo.git (push)
```

---

## 🧹 Summary

| Step | Command                         | Description        |
| ---- | ------------------------------- | ------------------ |
| 1    | `git config --global user.name` | Set your name      |
| 2    | `git init`                      | Start a repository |
| 3    | `git add <file>`                | Stage changes      |
| 4    | `git commit -m "msg"`           | Save snapshot      |
| 5    | `git push`                      | Upload to GitHub   |

---

🎯 **Next Chapter:** [Basic Git Commands →](./02-git-commands.md)

```

---
