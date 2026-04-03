# How to Host Vigil West on GitHub Pages

GitHub Pages is free and serves your `index.html` as a live public website automatically.

---

## Prerequisites

- A free [GitHub account](https://github.com)
- Git installed on your machine — check by running `git --version`

---

## Step 1 — Create a GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Fill in:
   - **Repository name:** `vigilwest` (or any name you like)
   - **Visibility:** Public *(GitHub Pages is free only for public repos on the free plan)*
3. Leave everything else as default
4. Click **Create repository**

---

## Step 2 — Push Your Files to GitHub

Open your terminal, navigate to your project folder, and run these commands:

```bash
# Go into your project folder
cd /path/to/vigilVest

# Initialize git (skip if already a git repo)
git init

# Add all files
git add index.html

# Commit
git commit -m "Initial commit — Vigil West landing page"

# Connect to your GitHub repo (replace YOUR_USERNAME and YOUR_REPO_NAME)
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git

# Push to GitHub
git push -u origin main
```

> **Note:** If your default branch is called `master` instead of `main`, replace `main` with `master` in the last command.

---

## Step 3 — Enable GitHub Pages

1. On GitHub, open your repository
2. Click the **Settings** tab (top of the repo page)
3. In the left sidebar, click **Pages**
4. Under **Build and deployment → Source**, select **Deploy from a branch**
5. Under **Branch**, select `main` and set the folder to `/ (root)`
6. Click **Save**

---

## Step 4 — Get Your Live URL

After saving, GitHub will show your live URL at the top of the Pages settings. It will look like:

```
https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/
```

It may take **1–2 minutes** to go live on the first deploy.

---

## Step 5 — Updating the Site Later

Every time you make a change to `index.html`, just run:

```bash
git add index.html
git commit -m "Update landing page"
git push
```

GitHub Pages will automatically redeploy within about 60 seconds. You can watch the progress under **Actions** tab in your repo.

---

## Optional — Use a Custom Domain

If you own a domain (e.g. `vigilwest.com`), you can point it to GitHub Pages:

1. In **Settings → Pages**, enter your domain in the **Custom domain** field and click **Save**
2. At your domain registrar, add a CNAME record:
   - **Name:** `www`
   - **Value:** `YOUR_USERNAME.github.io`
3. For a root/apex domain, add these A records instead:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
4. Wait up to 24 hours for DNS to propagate
5. Check **Enforce HTTPS** in GitHub Pages settings once the domain is verified

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Site shows 404 | Make sure your file is named exactly `index.html` (lowercase) and is in the root of the repo |
| Changes not showing | Wait 60 seconds and hard-refresh (`Cmd+Shift+R` / `Ctrl+Shift+R`) |
| Push rejected | Run `git pull origin main --rebase` first, then push again |
| Fonts not loading | The page uses Google Fonts via CDN — requires an internet connection to render correctly |
