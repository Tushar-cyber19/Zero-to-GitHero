# 🌐 Hosting Websites with GitHub Pages

## 🎯 Topic: Free Static Site Hosting, Custom Domains & Automated Deployment

GitHub Pages allows you to host websites directly from your GitHub repository — **free of charge**. It is one of the most popular ways to publish documentation, portfolios, open-source project demos, and static web applications.

---

## 🌟 What You’ll Learn

By the end of this guide, you’ll master:
- ✅ What GitHub Pages can and cannot host (Static vs SSR realities)
- ✅ User/Organization sites (`<username>.github.io`) vs Project sites
- ✅ Deployment Method 1: Deploying directly from a Git branch (`main` or `gh-pages`)
- ✅ Deployment Method 2: Modern automated deployment via **GitHub Actions**
- ✅ Static export configurations for React, Vue, Vite, and Next.js
- ✅ Configuring Custom Domains, DNS records (`A` / `CNAME`), and enforcing HTTPS
- ✅ Single-Page Application (SPA) client-side routing and 404 solutions
- ✅ Troubleshooting common deployment errors

---

## 💡 1. What is GitHub Pages (and What Can It Host?)

GitHub Pages is a **static web server**. It serves static HTML, CSS, JavaScript, images, and client-side web assets directly from your repository.

### ✅ What GitHub Pages Can Host:
- Static portfolios, blogs, and marketing pages.
- Client-side Single Page Applications (built with Vite, React, Vue, Svelte, or vanilla JS).
- Static documentation built with Jekyll, Docusaurus, MkDocs, or Hugo.
- Static exports from frameworks (e.g. Next.js with `output: 'export'`).

### ❌ What GitHub Pages CANNOT Host:
> [!IMPORTANT]
> **GitHub Pages does NOT have a server-side runtime.**
> - It **cannot** run Node.js, Python, Ruby, PHP, or Java backend servers.
> - It **cannot** execute Server-Side Rendering (SSR), Next.js Server Actions, API routes, or dynamic database queries.
> - If your project requires dynamic database storage or server code, you must host your backend on platforms like Render, Railway, Fly.io, or AWS, and connect your static frontend via API calls.

---

## 📍 2. Understanding GitHub Pages URLs & Site Types

| Type | Repository Name | Live URL | Deployment Root |
|---|---|---|---|
| **User / Org Site** | `<username>.github.io` | `https://<username>.github.io` | Root `/` of repo |
| **Project Site** | `any-project-name` | `https://<username>.github.io/<project-name>/` | Subpath `/<project-name>/` |

> [!WARNING]
> **Subpath Asset Traps in Project Sites:**
> For project sites, your assets live at `/<project-name>/`. If you use absolute paths like `<link href="/style.css">`, the browser will look at `https://<username>.github.io/style.css` (404 Not Found!).
> Always use relative paths (`./style.css`) or configure your build tool's base URL (e.g. `base: '/<project-name>/'` in `vite.config.js`).

---

## ⚙️ 3. Deployment Method 1: Deploy from a Branch

This is the fastest method for vanilla HTML/CSS/JS projects.

### Step 1: Push your code
Ensure your project contains an `index.html` at the root (or in a `/docs` folder):

```bash
git add .
git commit -m "feat: initial static site"
git push origin main
```

### Step 2: Enable in Repository Settings
1. On GitHub, navigate to your repository.
2. Click **Settings ⚙️** → **Pages** (in the left sidebar).
3. Under **Build and deployment → Source**, select **Deploy from a branch**.
4. Choose Branch: `main` and Folder: `/ (root)`.
5. Click **Save**.
6. Within 1-2 minutes, GitHub will display your live site URL!

---

## 🚀 4. Deployment Method 2: Automated Deploy with GitHub Actions

For modern framework projects (Vite, React, Vue, Next.js static export), the recommended approach is building and deploying automatically through **GitHub Actions**.

### Step 1: Configure Pages for GitHub Actions
In **Settings → Pages**, set **Source** to **GitHub Actions**.

### Step 2: Add Workflow File (`.github/workflows/deploy.yml`)

```yaml
name: Deploy Static Site to GitHub Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build-and-deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: "npm"

      - name: Install Dependencies
        run: npm ci

      - name: Build Project
        run: npm run build

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Upload Artifact
        uses: actions/upload-pages-artifact@v3
        with:
          # Change to 'out' for Next.js static export, or 'build' for Create-React-App
          path: "./dist"

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

Whenever you push to `main`, GitHub Actions automatically builds your project and publishes the compiled assets!

---

## ⚡ 5. Framework Setup Notes (Vite & Next.js)

### Vite Configuration (`vite.config.js`)
Set the `base` property to your repository name:
```javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  base: '/my-project-repo/', // Set this to match your repository name!
})
```

### Next.js Static Export (`next.config.js`)
Enable static HTML export:
```javascript
/** @type {import('next').NextConfig} */
const nextConfig = {
  output: 'export', // Produces static HTML/CSS/JS in the /out folder
  basePath: '/my-project-repo',
  images: {
    unoptimized: true, // GitHub Pages does not support Next.js on-demand image optimization
  },
};

module.exports = nextConfig;
```

---

## 🌍 6. Custom Domains & HTTPS

You can connect your own custom domain (e.g. `www.mycoolapp.com` or `portfolio.dev`):

### Step 1: Configure DNS Records at your Registrar (Namecheap, GoDaddy, Cloudflare)
- **For an Apex Domain (`mycoolapp.com`):** Add `A` records pointing to GitHub's IPs:
  ```text
  185.199.108.153
  185.199.109.153
  185.199.110.153
  185.199.111.153
  ```
- **For a Subdomain (`www.mycoolapp.com`):** Add a `CNAME` record:
  ```text
  Name/Host: www
  Target: <username>.github.io
  ```

### Step 2: Configure on GitHub
1. In **Settings → Pages → Custom domain**, enter `www.mycoolapp.com` and click **Save**.
2. GitHub automatically creates a `CNAME` file in your repository.
3. Check the box **Enforce HTTPS** (GitHub will provision a free Let's Encrypt SSL certificate within a few hours).

---

## 🧰 7. Troubleshooting Common Issues

### 1. 404 Page Not Found:
- Ensure the repository is **Public** (Free GitHub accounts cannot host Pages from private repos unless using GitHub Pro/Enterprise).
- Confirm your homepage file is named exactly `index.html` (all lowercase).
- Verify the build output directory in Actions matches your tool (`dist` vs `build` vs `out`).

### 2. Broken Styles & Images (CSS/JS 404):
- Open your browser's DevTools Network tab. If requests look like `https://username.github.io/assets/main.css`, you forgot to set the subpath base in your bundler configuration.

### 3. SPA Client-Side Routing (React Router / Vue Router 404 on refresh):
- Because GitHub Pages is a static server, refreshing on `/about` causes GitHub to look for a physical file `/about/index.html`.
- **Solution:** Add a `404.html` that redirects to `index.html`, or use HashRouter (`/#/about`).

---

## 📚 Summary Reference

| Feature | Branch Deployment | Actions Deployment |
|---|---|---|
| **Setup Complexity** | Very Low | Low |
| **Best For** | Pure HTML/CSS/JS | Frameworks (Vite, React, Vue, Next.js) |
| **Build Artifacts** | Stored in Git branch | Stored in ephemeral GitHub artifacts |
| **HTTPS Support** | ✅ Free automatic SSL | ✅ Free automatic SSL |
| **Custom Domain** | ✅ Yes | ✅ Yes |

---

## 🏆 Recap & Next Steps

You now possess complete knowledge to host, automate, and configure custom production domains on GitHub Pages!

➡️ **Next Guide:** [Working with GitHub Issues & Pull Requests](Working%20with%20GitHub%20Issues%20&%20Pull%20Requests.md) — Master professional issue tracking, PR templates, and collaborative code review.
