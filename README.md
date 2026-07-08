# Security & Compliance Hub

Central link hub for the S&C team. Single self-contained `index.html`
(vanilla JS, no build step). Public portal + password-gated admin console (`#admin`).

## Deploy to GitHub Pages

### 1. Push to GitHub
    git init
    git add .
    git commit -m "Security & Compliance hub"
    git branch -M main
    git remote add origin https://github.com/<your-org>/sc-hub.git
    git push -u origin main

### 2. Enable GitHub Pages
1. Go to **Settings → Pages** in your repository.
2. Source: **GitHub Actions**.
3. The workflow in `.github/workflows/deploy.yml` deploys on every push to `main`.

## Admin
Change the default password immediately after first login via **Settings → Password**.
Note: this is a client-side soft gate — do not rely on it for sensitive data.

## Data
Stored per-browser via localStorage. Use Settings → Export JSON to back up or move
between machines. For shared multi-user data, move to Supabase / SharePoint.
