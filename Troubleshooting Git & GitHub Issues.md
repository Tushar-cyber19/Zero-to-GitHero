# 🧩 Troubleshooting Git & GitHub Issues

## 🎯 Topic: Resolving Conflicts, Authentication, Credentials & System Errors

Every developer encounters Git errors. Whether it is an SSH permission rejection, an unexpected merge conflict, a detached HEAD state, or a Windows line-ending warning, this encyclopedia will give you exact, tested diagnostic steps across **Windows PowerShell**, **Git Bash**, and **macOS/Linux**.

---

## 🌟 What You’ll Learn

By the end of this guide, you’ll master:
- ✅ Resolving merge conflicts with visual markers
- ✅ Fixing SSH key errors on Windows PowerShell, Git Bash, and macOS
- ✅ How Git Credential Manager works and how to reset saved credentials
- ✅ Escaping and recovering from a Detached HEAD state
- ✅ Windows vs Unix line ending problems (`CRLF` vs `LF`)
- ✅ Recovering from rejected pushes (`[rejected] - fetch first`)
- ✅ Safe cleaning of untracked clutter without losing uncommitted work

---

## 🔒 1. Fixing Authentication & Permission Denied (`publickey`)

### 🚫 The Error:
```text
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
```

### 🔍 Diagnosis:
Git is trying to communicate with GitHub over SSH, but GitHub cannot verify your SSH private key against the public keys saved on your GitHub account.

---

### 🛠️ Step 1: Start the SSH Agent (Platform-Specific)

#### On Windows (PowerShell - Run as Administrator if service is stopped):
```powershell
# 1. Enable and start the Windows OpenSSH Authentication Agent service
Get-Service ssh-agent | Set-Service -StartupType Automatic
Start-Service ssh-agent

# 2. Add your private key
ssh-add $HOME\.ssh\id_ed25519
```

#### On Git Bash (Windows):
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

#### On macOS / Linux:
```bash
eval "$(ssh-agent -s)"
ssh-add --apple-use-keychain ~/.ssh/id_ed25519   # On macOS
# Or on Linux:
ssh-add ~/.ssh/id_ed25519
```

---

### 🛠️ Step 2: Copy Your Public Key to GitHub

#### On Windows PowerShell:
```powershell
Get-Content $HOME\.ssh\id_ed25519.pub | Set-Clipboard
```

#### On macOS:
```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

#### On Linux:
```bash
cat ~/.ssh/id_ed25519.pub
```

1. Go to **GitHub → Settings → SSH and GPG keys**.
2. Click **New SSH key**, paste your public key, and save.
3. Test the connection:
   ```bash
   ssh -T git@github.com
   ```
   ✅ Expected success: `Hi username! You've successfully authenticated...`

---

## 🔑 2. Fixing HTTPS Credential Problems

When connecting over HTTPS, Git stores your Personal Access Token (PAT) or OAuth token in your operating system's Credential Manager. If your password or token changes, Git commands will fail with:
`fatal: Authentication failed for 'https://github.com/...'`

### 🔍 Inspect Your Configured Credential Helper:
```bash
git config --show-origin --get-all credential.helper
```

### 🩹 How to Reset Cached Credentials:

#### 1. On Windows:
1. Press the Windows Key and search for **Credential Manager**.
2. Click **Windows Credentials**.
3. Under **Generic Credentials**, find any entry starting with `git:https://github.com`.
4. Click **Remove** (or edit and paste your new Personal Access Token).
5. The next time you run `git push`, Git will prompt you to log in cleanly via browser or token.

#### 2. On macOS:
1. Open **Keychain Access** app.
2. Search for `github.com`.
3. Right-click and delete the internet password entry.

#### 3. Command Line: Resetting via `git credential reject`
> [!IMPORTANT]
> `git credential reject` requires specific protocol and host parameters passed into standard input. Running it without input does nothing!

**In Git Bash / macOS / Linux:**
```bash
printf "protocol=https\nhost=github.com\n\n" | git credential reject
```

**In Windows PowerShell:**
```powershell
@"
protocol=https
host=github.com

"@ | git credential reject
```

---

## 🧠 3. Escaping the "Detached HEAD" State

### ⚡ What It Means:
You checked out a specific commit hash, tag, or remote branch directly rather than a local branch name. `HEAD` is pointing directly to a commit, not to a branch pointer. Any new commits you make will be orphaned and lost if you switch away!

### 👀 Check Your State:
```bash
git status
```
Output shows: `HEAD detached at 5a0e23d`

### 🩹 How to Fix:

#### Scenario A: You made commits while detached and want to KEEP them:
Simply create a new branch containing those commits:
```bash
git switch -c my-recovered-feature
```
Now those commits belong safely to `my-recovered-feature`!

#### Scenario B: You were just inspecting and want to DISCARD and return to normal:
Switch back to your main branch:
```bash
git switch main
```

---

## 📄 4. Line Ending Conflicts: CRLF vs LF

On Windows, line breaks are represented by Carriage Return + Line Feed (`\r\n` or `CRLF`). On macOS and Linux, line breaks are just Line Feed (`\n` or `LF`).

### 🚨 Common Warning:
```text
warning: in the working copy of 'index.js', LF will be replaced by CRLF the next time Git touches it
```

### 🩹 Fix: Configure `core.autocrlf`

#### For Windows Developers:
```powershell
git config --global core.autocrlf true
```
*(Git converts CRLF to LF when committing, and LF to CRLF when checking out).*

#### For macOS / Linux Developers:
```bash
git config --global core.autocrlf input
```

#### Best Practice for Teams: Add a `.gitattributes` file:
Create a file named `.gitattributes` in your repository root:
```text
# Set default behavior to automatically normalize line endings
* text=auto

# Enforce LF for shell scripts
*.sh text eol=lf

# Enforce CRLF for Windows batch files
*.bat text eol=crlf
```

---

## 🔁 5. Fixing "Updates Were Rejected (Fetch First)"

```text
! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/...'
hint: Updates were rejected because the remote contains work that you do not have locally.
```

### 🩹 The Clean Solution:
Do not force push! Pull the remote changes, rebase your local commits on top, and then push:

```bash
git pull --rebase origin main
git push origin main
```

---

## 🧹 6. Cleaning Untracked Files Safely (`git clean`)

When temporary files, build outputs, or scratch logs clutter your working tree:

### 1. Always do a dry run first (`-n`):
```bash
git clean -nd
```
Git will list every file and folder that **would** be deleted without actually deleting anything.

### 2. Perform the deletion (`-fd`):
```bash
git clean -fd
```
> [!CAUTION]
> `git clean -fd` deletes untracked files permanently from your hard drive! Git has never tracked them, so they **cannot** be recovered via `git reflog`. Always review with `git clean -nd` first!

---

## 💣 7. Troubleshooting Quick Matrix

| Error Message | Root Cause | Immediate Fix |
|---|---|---|
| `fatal: not a git repository` | Not inside a Git repo folder | Navigate to project root or run `git init` |
| `error: src refspec main does not match any` | Branch has 0 commits | Create your initial commit: `git commit -m "initial"` |
| `fatal: refusing to merge unrelated histories` | Two distinct repos being joined | `git pull origin main --allow-unrelated-histories` |
| `fatal: remote origin already exists` | Remote name already mapped | Check with `git remote -v` or run `git remote set-url` |
| `error: Your local changes would be overwritten by merge` | Uncommitted work conflicts with pull | Stash first: `git stash -u`, then pull, then `git stash pop` |

---

## 🏆 Recap & Next Steps

You now know how to diagnose and resolve the trickiest authentication, line-ending, and repository issues across Windows, macOS, and Linux!

➡️ **Next Guide:** [Best Practices & Professional Workflow](Best%20Practices%20&%20Professional%20Workflow.md) — Learn how professional software teams structure branches, write conventional commits, and manage releases.
