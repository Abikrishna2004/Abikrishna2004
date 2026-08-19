# Setup Guide

This repo powers the special GitHub **profile README** shown on
`github.com/Abikrishna2004`. Follow these steps once, after uploading.

## 1. Create the special repository
GitHub only renders a profile README when the repo name **exactly matches
your username**:

```
Repository name: Abikrishna2004
Visibility:      Public
Initialize with: nothing (you already have README.md)
```

## 2. Upload this folder structure as-is
Push everything below to the `main` branch, preserving paths:

```
git init
git remote add origin https://github.com/Abikrishna2004/Abikrishna2004.git
git add .
git commit -m "Initial profile README with automation"
git branch -M main
git push -u origin main
```

## 3. Enable the Snake animation workflow
No secrets needed — it uses the built-in `GITHUB_TOKEN`.
- Go to **Settings → Actions → General → Workflow permissions**
- Select **Read and write permissions** → Save
- Go to the **Actions** tab → run `Generate Snake Animation` manually once
  (or wait for the daily cron) — it will create an `output` branch holding
  the generated SVGs that the README already links to.

## 4. Enable the Metrics dashboard workflow (optional, richer stats)
This one needs a Personal Access Token because it reads more of your account
than the default token allows:
- Create a **classic PAT** at github.com/settings/tokens with scope `repo`
  (and `read:user`, `read:org` if you want org stats)
- In this repo: **Settings → Secrets and variables → Actions → New repository
  secret**
  - Name: `METRICS_TOKEN`
  - Value: the token you generated
- Run the `Generate Profile Metrics` workflow once from the **Actions** tab.

## 5. Confirm the logo renders
`assets/compile-journey-logo.png` is already referenced by relative path in
`README.md`, so no extra config is needed — it will render automatically
once pushed.

## 6. Everything else (stats cards, streak stats, activity graph, typing SVG,
capsule-render banners) is powered by public hosted services (Vercel/Heroku
endpoints) and needs zero setup — they pull live from your GitHub username
on every page load.
