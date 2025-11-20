# ⚡ GitHub CLI (Command-Line Power)

---

## 🎯 **Objective**

Learn how to use **GitHub CLI (`gh`)**, a powerful command-line tool that lets you manage **repositories, issues, pull requests, and more — right from your terminal!** 🖥️💪

---

## 🧩 **1. What Is GitHub CLI?**

The **GitHub CLI (gh)** brings GitHub to your terminal!
Instead of switching between your browser and terminal, you can **create repos, manage issues, and handle pull requests** using simple commands.

✨ It’s perfect for developers who love automation and speed.

---

## ⚙️ **2. Installation & Setup**

### 🔹 **Step 1: Download & Install**

Visit 👉 [https://cli.github.com/](https://cli.github.com/)
Choose your OS and install accordingly.

**For Windows (using Scoop):**

```bash
scoop install gh
```

**For macOS (using Homebrew):**

```bash
brew install gh
```

**For Linux (Debian/Ubuntu):**

```bash
sudo apt install gh
```

---

### 🔹 **Step 2: Verify Installation**

Check if the installation was successful:

```bash
gh --version
```

✅ Output example:

```
gh version 2.59.0 (2025-11-08)
https://github.com/cli/cli/releases/latest
```

---

### 🔹 **Step 3: Authenticate with GitHub**

To connect your CLI with GitHub:

```bash
gh auth login
```

Follow the on-screen prompts:

* Choose **GitHub.com**
* Select **HTTPS** or **SSH**
* Open the authentication link in your browser
* Authorize GitHub CLI

✅ Once connected, test it:

```bash
gh auth status
```

Output example:

```
✓ Logged in to github.com as tusharmanaktala (SSH)
```

---

## 🧠 **3. Basic GitHub CLI Commands**

Let’s explore the most common and useful commands 👇

---

### 📦 **a. Working with Repositories**

**Create a new repo:**

```bash
gh repo create github-guide --public
```

✅ Output:

```
✓ Created repository 'tusharmanaktala/github-guide' on GitHub
```

**Clone a repo:**

```bash
gh repo clone username/repo-name
```

**View details about a repo:**

```bash
gh repo view username/repo-name
```

**Open repo in browser:**

```bash
gh repo view --web
```

---

### 🧩 **b. Managing Issues**

**List all issues:**

```bash
gh issue list
```

✅ Example output:

```
#12  🐞 Fix navigation bug           open   frontend
#13  ✨ Add GitHub CLI tutorial      open   documentation
```

**Create a new issue:**

```bash
gh issue create --title "Fix typo in README" --body "The word 'setup' is misspelled on line 3."
```

**View a specific issue:**

```bash
gh issue view 13
```

**Close an issue:**

```bash
gh issue close 13
```

---

### 🔀 **c. Working with Pull Requests (PRs)**

**List open pull requests:**

```bash
gh pr list
```

**View PR details:**

```bash
gh pr view 21
```

**Create a new pull request:**

```bash
gh pr create --title "Added new CLI section" --body "This PR adds File 12 to the guide." --base main --head feature/cli-guide
```

**Check out a PR locally (for testing):**

```bash
gh pr checkout 21
```

**Merge a pull request:**

```bash
gh pr merge 21
```

**Open PR in browser:**

```bash
gh pr view 21 --web
```

---

### 🗣️ **d. Managing Collaborators**

**Add collaborator:**

```bash
gh api repos/:owner/:repo/collaborators/:username --method PUT
```

**Remove collaborator:**

```bash
gh api repos/:owner/:repo/collaborators/:username --method DELETE
```

---

## 🧮 **4. Managing GitHub Actions (Automation)**

GitHub CLI can also interact with **workflows and CI/CD pipelines**!

**List workflows:**

```bash
gh workflow list
```

**Run a workflow manually:**

```bash
gh workflow run build.yml
```

**Check workflow run status:**

```bash
gh run list
```

---

## 📊 **5. GitHub Projects and Discussions**

**View all projects:**

```bash
gh project list
```

**Create a new discussion:**

```bash
gh discussion create --title "Ideas for new GitHub CLI features" --body "Let’s brainstorm CLI-based automation ideas!"
```

**List discussions:**

```bash
gh discussion list
```

---

## 🧰 **6. Helpful Utilities**

**Open any resource (issue, PR, repo) directly in browser:**

```bash
gh browse
```

**Search across repositories:**

```bash
gh search repos "github guide"
```

**View your notifications:**

```bash
gh notifications
```

**Log out:**

```bash
gh auth logout
```

---

## 💡 **7. Automation Example: Create Repo + Push Project**

Here’s how you can create a repo and push your project from terminal — all using CLI:

```bash
# Step 1: Initialize Git
git init
git add .
git commit -m "Initial commit"

# Step 2: Create repo via CLI
gh repo create my-awesome-project --public --source=. --remote=origin

# Step 3: Push to GitHub
git push -u origin main
```

✅ Your project is now live on GitHub!

---

## ⚙️ **8. GitHub CLI Shortcuts**

| Action            | Command                        |
| ----------------- | ------------------------------ |
| View your profile | `gh api user`                  |
| Star a repo       | `gh repo star username/repo`   |
| Fork a repo       | `gh repo fork username/repo`   |
| Delete a repo     | `gh repo delete username/repo` |
| Check rate limit  | `gh api rate_limit`            |

---

## 🧠 **Pro Tips**

💡 Use `--web` with any command to open that page in your browser.
💡 Use `--json` flag to get structured outputs for scripting:

```bash
gh issue list --json title,number,state
```

💡 Combine Git + GitHub CLI for full automation pipelines!
💡 You can even create GitHub Actions workflows from the terminal.

---

## 🏁 **Summary**

✨ The **GitHub CLI (gh)** allows you to:

* Manage repositories, issues, and PRs
* Automate tasks from your terminal
* Speed up collaboration and project management

No browser, no clicks — just pure **command-line power**! ⚡💻

---

➡️ **Next Step:** [Hosting Websites with GitHub Pages](Hosting%20Websites%20with%20GitHub%20Pages.md) to host your projects live on GitHub Pages.
