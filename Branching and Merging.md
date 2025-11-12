# 🌿 Branching and Merging

## 🎯 Topic: Working with Branches in Git

---

## 🌟 What You’ll Learn

By the end of this file, you’ll be able to:
✅ Create and switch between branches
✅ Merge branches and handle conflicts
✅ View and delete branches
✅ Understand fast-forward vs no-fast-forward merges
✅ Follow a real-world branching strategy

---

## 🧩 What Is a Branch?

A **branch** is like a separate workspace where you can make changes without affecting the main project.

💡 Think of it as creating a *copy of your project’s timeline* — so you can experiment, test, or add new features safely.

---

## 🌱 1. Viewing Branches

To see all branches in your repository:

```bash
git branch
```

✅ **Example Output:**

```
* main
  feature-1
```

👉 The `*` indicates your current branch.

---

## 🌿 2. Creating a New Branch

Create a new branch named `feature-1`:

```bash
git branch feature-1
```

✅ **Result:**

```
Branch 'feature-1' created.
```

Now you have two branches — `main` and `feature-1`.

---

## 🔁 3. Switching Between Branches

Switch to your new branch:

```bash
git checkout feature-1
```

✅ **Result:**

```
Switched to branch 'feature-1'
```

✨ *Now you’re working on the `feature-1` branch. Any changes you make will stay isolated from the main branch.*

---

## 🧱 4. Creating and Switching in One Step

Save time with this shortcut:

```bash
git checkout -b feature-2
```

✅ **Result:**

```
Switched to a new branch 'feature-2'
```

---

## 💡 5. Working in a Branch

Make some changes, then commit them as usual:

```bash
echo "New Feature Added" > feature.txt
git add feature.txt
git commit -m "Added new feature file"
```

✅ **Result:**

```
[feature-1 a12b3cd] Added new feature file
 1 file changed, 1 insertion(+)
```

---

## 🌳 6. Merging Branches

Once your feature is complete, switch back to the `main` branch:

```bash
git checkout main
```

Then merge your branch into main:

```bash
git merge feature-1
```

✅ **Possible Result (Fast-Forward Merge):**

```
Updating 8b2a6e4..a12b3cd
Fast-forward
 feature.txt | 1 +
```

---

## ⚠️ 7. Handling Merge Conflicts

Sometimes two branches change the same part of a file — this causes a **conflict**.

### Example Conflict Message:

```
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

### 🛠 Steps to Fix:

1. Open the file with conflict — you’ll see something like:

   ```
   <<<<<<< HEAD
   Current content in main branch
   =======
   Content from feature branch
   >>>>>>> feature-1
   ```

2. Edit the file to keep what you want.

3. Save the file and mark as resolved:

   ```bash
   git add index.html
   git commit -m "Resolved merge conflict"
   ```

✅ **Result:**

```
[main 7d8e2f3] Resolved merge conflict
```

---

## 🧹 8. Deleting Branches

After merging, delete the branch to keep things clean.

### 🗑 Delete a local branch:

```bash
git branch -d feature-1
```

✅ **Result:**

```
Deleted branch feature-1 (was a12b3cd).
```

### 🌐 Delete a remote branch:

```bash
git push origin --delete feature-1
```

✅ **Result:**

```
- [deleted] feature-1
```

---

## 👀 9. Viewing All Branches (Local + Remote)

```bash
git branch -a
```

✅ **Output Example:**

```
* main
  feature-2
  remotes/origin/main
  remotes/origin/feature-1
```

---

## ⚡ 10. Fast-Forward vs No-Fast-Forward Merge

| Merge Type          | Description                                                                   | Command Example               |
| ------------------- | ----------------------------------------------------------------------------- | ----------------------------- |
| **Fast-Forward**    | When the branch can be directly merged without conflicts or diverging history | `git merge feature-1`         |
| **No Fast-Forward** | Keeps history of merges visible (useful for tracking feature branches)        | `git merge --no-ff feature-1` |

💡 *Teams often prefer no-fast-forward merges to keep a clear record of feature merges.*

---

## 🧠 Real-World Branching Strategy

A common and clean approach is the **Feature Branch Workflow**:

```
main
│
├── feature/login
│
├── feature/signup
│
└── bugfix/navbar
```

✅ **Steps:**

1. Create a new branch for every new feature or bug fix.
2. Commit and push changes there.
3. Create a Pull Request (PR) on GitHub.
4. After review, merge into `main`.
5. Delete the branch once done.

---

## 📚 Quick Reference Table

| Command                           | Description                        |
| --------------------------------- | ---------------------------------- |
| `git branch`                      | View all branches                  |
| `git branch <name>`               | Create a new branch                |
| `git checkout <name>`             | Switch to another branch           |
| `git checkout -b <name>`          | Create and switch in one step      |
| `git merge <branch>`              | Merge another branch into current  |
| `git branch -d <name>`            | Delete local branch                |
| `git push origin --delete <name>` | Delete remote branch               |
| `git branch -a`                   | View all branches (local + remote) |

---

## 🎉 Recap

You’ve mastered:
🌿 Creating and switching branches
🔀 Merging branches
⚡ Handling merge conflicts
🧹 Deleting branches cleanly
🧭 Understanding fast-forward merges

---

## 🚀 Next Step

Head to **Working with Remote Repositories** 🌍
You’ll learn how to connect, fetch, and sync your local and remote repos like a pro.