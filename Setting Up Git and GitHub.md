# ⚙️ Setting Up Git and GitHub

## 🎯 Topic: Installation and Initial Configuration

---

## 🧩 What You’ll Learn

By the end of this section, you’ll know how to:
✅ Install Git on your system
✅ Configure your Git identity
✅ Generate SSH keys and connect to GitHub
✅ Create your first repository
✅ Clone repositories and understand folder structure

---

## 💻 Step 1: Downloading and Installing Git

### 🪟 For Windows:

1. Visit 👉 [https://git-scm.com/downloads](https://git-scm.com/downloads)
2. Download the Windows installer.
3. Run the installer and keep default settings.

### 🐧 For Linux:

```bash
sudo apt update
sudo apt install git -y
```

### 🍎 For macOS:

```bash
brew install git
```

---

## 🔍 Step 2: Verify Installation

After installation, confirm Git is installed:

```bash
git --version
```

✅ **Expected Output:**

```
git version 2.43.0
```

---

## 👤 Step 3: Set Up Your Git Identity

Before using Git, configure your username and email (this information appears in commits).

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

### 💡 Tip:

Use `--global` to apply settings for all repositories, or omit it for a specific repo.

🔎 **View Your Configurations:**

```bash
git config --list
```

---

## 🔑 Step 4: Generate SSH Keys

SSH keys allow secure communication between your local machine and GitHub without needing passwords.

### 🛠 Generate Key:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

Press **Enter** three times to accept default options.

### 📂 Locate the Key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the entire output.

---

## 🌐 Step 5: Connect Git with GitHub (SSH Method)

1. Go to your GitHub profile → ⚙️ **Settings** → **SSH and GPG keys**
2. Click **New SSH key**
3. Paste your public key and save.

### ✅ Test the Connection:

```bash
ssh -T git@github.com
```

**Expected Output:**

```
Hi username! You've successfully authenticated.
```

---

## 🧰 Step 6: Create Your First Repository

### On GitHub:

1. Go to [GitHub.com](https://github.com/) → Click **New Repository**
2. Enter a name (e.g., `github-guide`)
3. Choose **Public** → ✅ Check **Add a README file**
4. Click **Create repository**

---

## 🗂 Step 7: Clone the Repository

Download your GitHub repository to your local machine.

```bash
git clone git@github.com:username/github-guide.git
```

💡 *or use HTTPS if SSH isn’t set up:*

```bash
git clone https://github.com/username/github-guide.git
```

✅ **Expected Output:**

```
Cloning into 'github-guide'...
remote: Enumerating objects...
Receiving objects: 100% (x/y), done.
```

---

## 📁 Step 8: Basic Folder Structure Overview

After cloning, your folder might look like this:

```
github-guide/
├── README.md
└── .git/
```

🧠 **Explanation:**

* `README.md` → Description of your project
* `.git/` → Hidden folder that tracks all changes

---

## ⚙️ Step 9: Configure Editor (Optional but Helpful)

If you prefer a specific editor like VS Code:

```bash
git config --global core.editor "code --wait"
```

Now Git will open commit messages in VS Code by default.

---

## 💪 Step 10: Test Everything

Try a quick commit test:

```bash
echo "Hello Git!" > test.txt
git add test.txt
git commit -m "Initial test commit"
git push origin main
```

✅ **Result:**
Your first commit will appear on your GitHub repository page 🎉

---

## 🧠 Recap

| Step | Action                | Command Example                                 |
| ---- | --------------------- | ----------------------------------------------- |
| 1    | Install Git           | `sudo apt install git`                          |
| 2    | Verify version        | `git --version`                                 |
| 3    | Set user identity     | `git config --global user.name`                 |
| 4    | Generate SSH key      | `ssh-keygen -t ed25519`                         |
| 5    | Test SSH              | `ssh -T git@github.com`                         |
| 6    | Create repo on GitHub | *(via website)*                                 |
| 7    | Clone repo            | `git clone <repo-url>`                          |
| 8    | Check folder          | `ls -a`                                         |
| 9    | Set editor            | `git config --global core.editor "code --wait"` |
| 10   | Test commit           | `git add`, `git commit`, `git push`             |

---

## 🏁 You’re All Set!

🎉 Congratulations! You’ve successfully set up Git and connected it with GitHub.
Now you’re ready to start version-controlling your projects 🚀

➡️ **Next Step:** [Git Commands Explained](Git%20Commands%20Explained.md) to learn essential Git commands for daily use.
