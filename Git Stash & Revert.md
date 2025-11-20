# 🌟 **Advanced: Git Stash & Revert**

---

## 🎯 **Objective**

In this file, we’ll learn about two very powerful Git commands —
**git stash** and **git revert** — that help you manage your work safely and efficiently.

---

## 🧳 **1. Git Stash — Save Work Temporarily**

### 💡 **What is Git Stash?**

`git stash` lets you **save your uncommitted changes temporarily** so you can switch branches or work on something else — without committing those changes.

It’s like saying:

> “Hold my code for a bit, I’ll come back later!” 😄

---

### 🧠 **When to Use It**

* You’re working on a feature, but need to switch to another branch to fix a bug.
* You’re not ready to commit yet, but don’t want to lose your progress.

---

### 🧩 **Basic Commands**

#### ➤ **Save your changes**

```bash
git stash
```

🧾 *Temporarily saves both staged and unstaged changes.*

#### ➤ **View stashed changes**

```bash
git stash list
```

📋 *Shows a list of all your stashes.*

**Example Output:**

```
stash@{0}: WIP on main: 4e6a2ab updated README
stash@{1}: WIP on feature/login: d14f89c added login form
```

#### ➤ **Apply the latest stash**

```bash
git stash apply
```

💫 *Brings back the most recently stashed changes.*

#### ➤ **Apply a specific stash**

```bash
git stash apply stash@{1}
```

#### ➤ **Remove a stash after applying**

```bash
git stash drop stash@{0}
```

#### ➤ **Apply and remove in one step**

```bash
git stash pop
```

🔥 *Applies the latest stash and deletes it.*

#### ➤ **Clear all stashes**

```bash
git stash clear
```

⚠️ *Removes all stored stashes permanently.*

---

### 🧰 **Example Workflow**

1️⃣ You are coding a new feature:

```bash
git add .
```

2️⃣ But your manager says, “Fix that urgent bug!”

```bash
git stash
```

3️⃣ Switch to main branch:

```bash
git checkout main
```

4️⃣ Fix the bug, commit the fix, then come back:

```bash
git checkout feature-branch
git stash pop
```

✅ Your work is back, just as you left it!

---

## 🕓 **2. Git Revert — Undo a Commit Safely**

### 💡 **What is Git Revert?**

`git revert` creates a **new commit** that undoes the changes made by a previous commit.
Unlike `git reset`, it **doesn’t delete history**, so it’s **safe for shared branches**. 🛡️

---

### 🧩 **Basic Commands**

#### ➤ **Revert a specific commit**

```bash
git revert <commit-hash>
```

**Example:**

```bash
git revert a1b2c3d
```

🪄 This creates a new commit that cancels out the effects of commit `a1b2c3d`.

---

#### ➤ **Revert multiple commits**

```bash
git revert <oldest-commit>^..<newest-commit>
```

**Example:**

```bash
git revert a1b2c3d^..f6g7h8i
```

---

### ⚠️ **If You Get a Merge Conflict**

* Git will stop and ask you to resolve conflicts manually.
* After fixing the files, run:

```bash
git add .
git revert --continue
```

---

### 🎉 **Undoing a Revert (Re-Revert)**

If you accidentally reverted something and want it back:

```bash
git revert <revert-commit-hash>
```

😄 *Yes, you can “revert the revert”!*

---

## 🚀 **Quick Comparison**

| Command      | Purpose                        | Deletes History? | Use When                        |
| ------------ | ------------------------------ | ---------------- | ------------------------------- |
| `git stash`  | Temporarily save local changes | ❌ No             | Need to switch tasks/branches   |
| `git revert` | Undo a specific commit safely  | ❌ No             | Undo a mistake in shared branch |

---

## 🧠 **Pro Tips**

💎 Combine stash and revert with other advanced commands:

* `git stash show -p` → See what’s inside your stash.
* `git stash branch <branchname>` → Create a new branch from stashed work.
* Always prefer `git revert` over `git reset` when working on shared repos.

---

## 🏁 **Summary**

✨ **Git Stash** → Temporarily saves unfinished work.
✨ **Git Revert** → Safely undoes a commit without losing history.

Both commands keep your workflow clean, flexible, and professional! 💼

---

➡️ **Next Step:** [Git Rebase & Cherry-pick](Git%20Rebase%20&%20Cherry-pick.md) to master advanced Git techniques for clean history.

Continue to **Git Rebase & Cherry-pick** 