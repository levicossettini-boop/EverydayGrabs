# Shopify Auto-Deploy Setup

This repository contains a Shopify Dawn theme in `Shopify theme.md` and a GitHub Actions workflow at `.github/workflows/shopify-deploy.yml`.

## What has been done

- Initialized local Git repository
- Added `.gitignore`
- Added GitHub Actions workflow to push the theme folder to Shopify on `push` to `main`

## What you still need to do

### 1. Create a GitHub repository

Create a repo on GitHub and push this local directory to it.

Example commands:

```bash
cd '/Users/levicossettini/landing page'
git remote add origin https://github.com/USERNAME/REPO_NAME.git
git branch -M main
git push -u origin main
```

Replace `USERNAME` and `REPO_NAME` with your GitHub account and repository name.

### 2. Add GitHub repository secrets

In your GitHub repo settings, add these secrets:

- `SHOPIFY_STORE_URL` — your store URL, e.g. `your-store.myshopify.com`
- `SHOPIFY_API_TOKEN` — Shopify API or CLI token with theme push permissions
- `SHOPIFY_THEME_ID` — the target theme ID to deploy

### 3. Verify theme folder path

The workflow deploys from the `Shopify theme.md` folder path. Do not rename or move that folder unless you also update `.github/workflows/shopify-deploy.yml`.

### 4. Optional: Install Shopify CLI locally

If you want to test locally before pushing:

```bash
npm install -g @shopify/cli
cd '/Users/levicossettini/landing page/Shopify theme.md'
shopify theme push --path=. --themeid="THEME_ID" --allow-live
```

## How the workflow works

The workflow uses `actions/checkout` and `@shopify/cli` to deploy the theme when changes are pushed to the `main` branch.

If you want, I can also add a second workflow that only deploys when a pull request is merged or when a tag is created.
