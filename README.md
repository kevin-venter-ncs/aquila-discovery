# Aquila — Discovery Questionnaire (public page)

A static, backend-free questionnaire page for the **Aquila** accounting practice (NC South's first
customer for the Aquila bookkeeping/tax-prep tool). It collects the practice's discovery answers and
points them at a **private upload link** for any sample client files.

> The project spec lives separately in the (private) `nc-south` repo under `Aquila/`. This repo is
> **only** the public-facing page — it deliberately contains no client or project-confidential material.

## How it works

- `index.html` is fully self-contained (no build step, no dependencies).
- Respondents type answers directly; progress auto-saves in **their** browser (`localStorage`).
- **Nothing is transmitted by the page.** Answers stay local until the user clicks
  *Download my answers* (a `.txt` file) or *Print / Save as PDF*.
- A *Securely send your files* button links to a **private, access-controlled upload location** you
  set — so real client financial files never pass through a public form service.

## Before you publish — set the upload link

Edit the one config line near the bottom of [`index.html`](index.html):

```js
const UPLOAD_LINK = "REPLACE_WITH_YOUR_PRIVATE_UPLOAD_LINK";
```

Use an access-controlled location, e.g.:
- **Google Drive** — a folder shared with the practice, or a Google Form set to *file upload* (Drive backs it).
- **OneDrive / SharePoint** — a *file request* link.
- **Dropbox** — a *file request* link.

Until it's set, the button shows a friendly "email us for a link" prompt and the page still works.

## Deploy to GitHub Pages

`gh` CLI isn't installed locally, so create the repo + enable Pages in the web UI (or install `gh`).

1. Create a new repo on GitHub named e.g. `aquila-discovery` (public).
2. From this folder:
   ```bash
   git remote add origin https://github.com/kevin-venter-ncs/aquila-discovery.git
   git branch -M main
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Source: Deploy from a branch → `main` / `root` → Save**.
4. The page goes live at `https://kevin-venter-ncs.github.io/aquila-discovery/` within a minute or two.

The page sets `noindex`, so it won't show up in search engines.

## Files

| File | Purpose |
|---|---|
| `index.html` | The questionnaire page (self-contained). |
| `README.md` | This file. |