# 🧩 **Working with GitHub Issues & Pull Requests**

---

## 🎯 **Objective**

Learn how to **collaborate effectively** on GitHub using **Issues**, **Pull Requests (PRs)**, and **Code Reviews** — the backbone of every open-source and professional workflow! 💪

---

## 🗂️ **1. Understanding GitHub Issues**

### 💡 **What Are Issues?**

**Issues** are GitHub’s way to **track bugs 🐞, enhancements ✨, or tasks 📋** within a project.
Each issue can have:

* A **title** and **description** 📝
* **Assignees** 👤 (who’s responsible)
* **Labels** 🏷️ (e.g., bug, enhancement)
* **Comments** 💬 (for discussion)
* **Milestones** 🎯 (group of issues)

---

### 🧩 **Creating an Issue**

1️⃣ Go to your GitHub repository.
2️⃣ Click on the **“Issues”** tab.
3️⃣ Click **“New Issue”** ➕.
4️⃣ Fill in:

* **Title:** e.g. “Fix login button alignment”
* **Description:** explain what’s wrong or what’s needed.

**Example:**

```
Title: Fix login button misalignment on mobile
Description: On smaller screens, the login button overlaps with footer content. Needs padding adjustments.
```

✅ Assign labels like `bug`, `UI`, or `frontend`.

---

### 💬 **Commenting on Issues**

Collaborators can add:

```text
@username please check this issue
```

This tags someone for attention.

💡 Tip: Use Markdown formatting in issue comments (`**bold**`, `- lists`, etc.)

---

### 🏷️ **Using Labels**

Labels help organize issues.
You can create or edit them under **Issues → Labels**.

Common labels:

* 🐞 `bug`
* 🚀 `feature`
* 💡 `enhancement`
* 📄 `documentation`
* ⚙️ `backend`
* 🎨 `frontend`

---

## 🔀 **2. Understanding Pull Requests (PRs)**

### 💡 **What Is a Pull Request?**

A **Pull Request (PR)** is how you propose changes to a repository.
It lets others **review**, **discuss**, and **merge** your code safely.

Think of it like:

> “Hey team, I’ve made these changes — please review and merge them!” 😄

---

### ⚙️ **Basic Pull Request Workflow**

1️⃣ **Fork or clone** the repository.
2️⃣ Create a **new branch** for your changes:

```bash
git checkout -b feature/update-login-ui
```

3️⃣ Make changes, then **commit and push**:

```bash
git add .
git commit -m "Updated login button UI"
git push origin feature/update-login-ui
```

4️⃣ Go to your repo on GitHub → click **“Compare & pull request”**.

5️⃣ Add a **title** and **description** for your PR.
6️⃣ Click **“Create Pull Request”** ✅

---

### ✍️ **Example PR Description**

```
Title: Fix: Updated login button padding for mobile view

Description:
- Fixed overlapping issue on small screens
- Updated CSS for better alignment

Closes #14
```

💡 The keyword **“Closes #14”** automatically closes Issue #14 when this PR is merged.

---

### 🧠 **Best Practices for Pull Requests**

✅ Use clear and descriptive titles.
✅ Make sure your branch name explains the feature/fix.
✅ Keep PRs small and focused on one purpose.
✅ Add screenshots or videos for UI changes.
✅ Request reviewers (`@username`) for feedback.

---

## 🧩 **3. Reviewing & Merging Pull Requests**

### 👀 **Code Review**

Collaborators can:

* View diffs (changes made)
* Leave comments or suggestions 💬
* Approve ✅ or request changes 🔁

### 🧠 **Approving a PR**

If everything looks good:

* Click **“Review changes” → “Approve” → “Submit review”**

### 🔗 **Merging a PR**

Once approved:

* Click **“Merge pull request”**
* Choose the merge option:

  * **Merge commit** (default)
  * **Squash and merge** (combine commits)
  * **Rebase and merge** (linear history)

---

### 🧹 **Deleting Branch After Merge**

GitHub shows a button:

```
Delete branch
```

Click it to keep your repo clean. 🧼

---

## 🗣️ **4. Discussions & Collaboration**

### 💬 **GitHub Discussions**

Used for open-ended topics like:

* Feature ideas 💡
* Design feedback 🎨
* Q&A from contributors ❓

To enable:
1️⃣ Go to **Settings → Discussions → Enable discussions**
2️⃣ Collaborators can start new topics or comment on threads.

---

## 🛠️ **5. GitHub Project Boards**

Project boards = visual task management (like Trello!).

Use under **Projects** tab:

* Columns: `To Do`, `In Progress`, `Done`
* Add issues and PRs to track status

**Command-line helper (optional):**

```bash
gh project list
```

*(using GitHub CLI)*

---

## 🧩 **6. Linking Issues and PRs**

You can **link** them by keywords in PR description:

| Keyword      | Action                |
| ------------ | --------------------- |
| closes #ID   | Closes issue on merge |
| fixes #ID    | Fixes the issue       |
| resolves #ID | Same as closes        |

Example:

```
Fixes #25 — updated password reset functionality
```

---

## 🚀 **7. Real-World Example**

**Scenario:**
You found a bug 🐞 in a project.
1️⃣ Open an **Issue** describing it.
2️⃣ Fork and clone the repo.
3️⃣ Fix it in a new branch.
4️⃣ Push changes and create a **Pull Request**.
5️⃣ Mention the issue number (e.g., closes #101).
6️⃣ Get it reviewed, approved, and merged! 🎉

This is how you contribute to open-source projects like a pro! 😎

---

## 🧠 **Pro Tips**

💡 Use **Draft Pull Requests** for incomplete work (so others know it’s not ready).
💡 Add **checklists** in PRs:

```
- [x] Fixed bug
- [ ] Added unit test
```

💡 Reference commits, issues, or PRs with `#ID` or full URLs.
💡 Enable **branch protection rules** for safer merges.

---

## 🏁 **Summary**

✨ **Issues** → Track bugs, tasks, and enhancements
✨ **Pull Requests** → Propose, review, and merge code
✨ **Discussions & Projects** → Collaborate effectively

Together, they make GitHub a complete project-management and collaboration platform! 💼💻

---

➡️ **Next Step:** [GitHub CLI (Command-Line Power)](GitHub%20CLI%20(Command-Line%20Power).md) to streamline GitHub workflows directly from your terminal.

Continue to **GitHub CLI – Command-Line Power ⚡** 