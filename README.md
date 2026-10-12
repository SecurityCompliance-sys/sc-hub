# Security & Compliance Hub

Central link hub for the S&C team. Single self-contained `index.html`
(vanilla JS, no build step). Public portal + password-gated admin console (`#admin`).

## Front end

The portal is one HTML file containing a small design system: design tokens → primitives →
components → layout. Nothing is fetched at runtime apart from the web fonts.

**Structure**

| Area | What it does |
| --- | --- |
| Utility bar | Portal status, language switch (EN/TH), search and console shortcuts |
| Navigation | Sticky, with functions mega-menu, search affordance, theme toggle, console CTA and a mobile drawer |
| Hero | Headline, two CTAs and a live panel with directory metrics plus quick-launch links |
| Browse by function | Overview cards for every function with live item counts |
| Most used | Ranked strip driven by the usage analytics recorded in the browser |
| Directory | Filter chips by type, live text filter, sort control, grid **or** table view, sticky function rail with scroll-spy, empty states and per-section deep links |
| Command palette | `⌘K` / `/` — resources, functions, actions and recent items in one search |
| Resource actions | Launch chooser, QR code (print or download as PNG), copy link, open in new tab |
| Footer | Function sitemap, platform and support shortcuts, locale switch, legal note, back to top |
| Admin console | Resources, functions, analytics and settings — restyled to match, same data model |

**Theming** — light and dark tokens, dark follows the operating system until the visitor
picks a theme (resolved before first paint, so there is no flash). A print stylesheet
turns the directory into a clean two-column document.

**Accessibility** — skip link, semantic landmarks, focus-visible rings, focus trapping in
dialogs, `aria-live` toasts, `aria-pressed`/`aria-expanded` state, keyboard support for
every surface, `prefers-reduced-motion` and `prefers-contrast` handling.

### Keyboard shortcuts

| Keys | Action |
| --- | --- |
| `⌘K` / `Ctrl K` / `/` | Open search |
| `↑` `↓` | Move through results |
| `↵` | Open the selected result |
| `Esc` | Close any dialog, menu or drawer |
| `?` | Show the shortcut sheet |
| `⌘P` / `Ctrl P` | Print the directory |

### Files

* `index.html` — the entire portal (markup, design system, application logic)
* `manifest.webmanifest`, `favicon.svg`, `apple-touch-icon.png` — installable app metadata
* `.github/workflows/deploy.yml` — GitHub Pages deployment

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
Change the default password immediately after first login via **Settings → Access**.
Default password: `scadmin2026`.
Note: this is a client-side soft gate — do not rely on it for sensitive data.

## Data
Stored per-browser via localStorage. Use Settings → Export JSON to back up or move
between machines. For shared multi-user data, move to Supabase / SharePoint.
