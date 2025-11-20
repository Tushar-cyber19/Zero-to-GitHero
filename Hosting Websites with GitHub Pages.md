# 🌐 Hosting Websites with GitHub Pages 🚀

---

# 🌍 Hosting Websites with GitHub Pages 💫

GitHub Pages allows you to **host websites directly from your GitHub repository — for free!** 🎉
It’s perfect for portfolios, documentation, and project showcases.

Let’s explore how to set it up step by step 👇

---

## 💡 What is GitHub Pages?

GitHub Pages is a **static site hosting service** that takes HTML, CSS, and JavaScript files straight from your GitHub repository and serves them as a live website.

### 🌟 Examples:

* Personal portfolio
* Project documentation
* Small blogs
* Educational resources

Your website URL will usually look like this:

```
https://your-username.github.io/repo-name/
```

---

## ⚙️ Setting Up GitHub Pages

### 🪄 Step 1: Create a Repository

You can either:

* Create a **new repo** named `your-username.github.io` for a personal site, or
* Use an **existing project repo** to host your website.

---

### 🧱 Step 2: Add an index.html File

This file acts as your homepage.

Create a simple `index.html` in your repo:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Welcome to My GitHub Page</title>
</head>
<body>
  <h1>🎉 Hello, World!</h1>
  <p>This is my first GitHub Pages website.</p>
</body>
</html>
```

Then **commit** the file:

```bash
git add index.html
git commit -m "Add homepage"
git push origin main
```

---

### 🌐 Step 3: Enable GitHub Pages

1. Go to your repository on GitHub.
2. Click **Settings → Pages**.
3. Under **Source**, choose the branch you want to publish (usually `main` or `gh-pages`).
4. Click **Save**.

🎉 Your website will be live at:

```
https://your-username.github.io/repo-name/
```

---

## 🌿 Option 2: Use a `gh-pages` Branch

If you don’t want your main branch to host files, you can create a **gh-pages** branch.

```bash
git checkout -b gh-pages
git push origin gh-pages
```

Then, in **Settings → Pages**, select the `gh-pages` branch as the source.

💡 This keeps your code and web files separate.

---

## 📂 Folder Structure Example

```
my-website/
│
├── index.html
├── about.html
├── contact.html
├── assets/
│   ├── style.css
│   └── script.js
└── images/
    └── logo.png
```

Everything you push to your GitHub Pages branch will be published automatically.

---

## ⚙️ Bonus: Publish with GitHub Actions

You can **automate deployment** with GitHub Actions whenever you push new code.

Create a file: `.github/workflows/deploy.yml`

```yaml
name: 🚀 Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

Now your site updates automatically every time you push!

---

## 🔗 Setting a Custom Domain (Optional)

You can use your own domain instead of `github.io`.

1. Buy a domain (e.g., from Namecheap or GoDaddy).
2. In your repo’s root, create a file named `CNAME`:

```
www.yourdomain.com
```

3. In your DNS settings, add these **CNAME** records:

```
Type: CNAME
Host: www
Points to: your-username.github.io
```

Then wait for DNS propagation (can take up to 24 hours).

---

## 🧰 Common Issues and Fixes

| ❌ Issue                   | 💡 Solution                                     |
| ------------------------- | ----------------------------------------------- |
| Page not showing up       | Check that Pages is enabled in Settings → Pages |
| Wrong branch selected     | Use `main` or `gh-pages`                        |
| Missing index.html        | Ensure index.html exists at the repo root       |
| Custom domain not working | Re-add `CNAME` file and verify DNS records      |
| CSS/JS not loading        | Use **relative paths** (e.g., `./style.css`)    |

---

## ✨ Example — Publishing Your GitHub Guide Website

1. Go to your **GitHub Guide** repo.
2. Create a file `index.html` with intro and links to each topic file.
3. Enable GitHub Pages from Settings → Pages.
4. Your guide will be live at:
   👉 `https://your-username.github.io/github-guide/`

You can also add a professional look using templates like **Jekyll** or **Hugo** later on.

---

## 💬 Pro Tips

⭐ **Tip 1:** Use a clean `README.md` to describe your website’s purpose.
📁 **Tip 2:** Keep your folders organized (`assets`, `images`, `docs`).
🔄 **Tip 3:** If your site doesn’t update, clear browser cache or re-save Pages settings.

---

## 🎯 Summary

| Step | Description                     | Example                   |
| ---- | ------------------------------- | ------------------------- |
| 🪄 1 | Create a GitHub repository      | `your-username.github.io` |
| 🧱 2 | Add `index.html`                | Basic homepage            |
| 🌐 3 | Enable GitHub Pages             | From Settings → Pages     |
| 🌿 4 | Optional: use `gh-pages` branch | For separate hosting      |
| 🔗 5 | Add custom domain               | via CNAME file            |
| ⚙️ 6 | Automate with GitHub Actions    | Deploy workflow           |

---

## 💖 Final Thought

With GitHub Pages, your projects can go from code 💻 to live website 🌍 in minutes — all **for free**!
It’s a must-have skill for every developer 💪

---

➡️ **Next Step:** [Git Stash & Revert](Git%20Stash%20&%20Revert.md) to master temporary changes and undoing commits safely.

Continue to **Troubleshooting Git & GitHub Issues 🧩** 