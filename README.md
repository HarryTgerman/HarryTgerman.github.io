# Harry Trippel — portfolio + resume site

Static site. No build step. No dependencies. Deploys to GitHub Pages in two minutes.

## What's here

```
site/
├── index.html         portfolio home (3 system cards + experience + competencies)
├── resume.html        printable resume (used to generate the PDF)
├── deflation.html     deflation.ai architecture deep-dive
├── miningalpha.html   MiningAlpha multi-agent system deep-dive
├── css/style.css      shared styling — dark minimalist, calibrated to tzafon.ai
└── README.md          this file
```

Design language: dark theme, sans-serif (Inter), generous whitespace, JetBrains Mono accents. Print stylesheet inverts to clean light-mode for the PDF export.

## Generating the PDF

1. Open `resume.html` in **Chrome** (Chrome's PDF renderer respects the print stylesheet best — Safari is OK, Firefox sometimes mis-renders).
2. `⌘P` (or `Ctrl+P`).
3. Destination → **Save as PDF**.
4. **Important settings:**
   - Layout: **Portrait**
   - Paper size: **A4**
   - Margins: **Default** (the print CSS sets `@page { margin: 14mm }`)
   - **Background graphics: ON** (toggle in "More settings")
   - Headers and footers: **OFF**
   - Scale: **Default** (100%)
5. Save as `Harry-Trippel-Resume.pdf` into the `site/` directory.
6. Commit + push. The PDF is then available at `https://harrytgerman.github.io/Harry-Trippel-Resume.pdf` and is linked from the site footer + `index.html`.

If anything looks off in the PDF, the most common fix is making sure "Background graphics" is on in the print dialog.

## Deploying to GitHub Pages

Two ways. Pick one.

### Option A — recommended: user-site repo for clean root URL

This serves your site at `https://harrytgerman.github.io/` (no `/Resume/` subpath, looks more senior).

1. Create a **new** GitHub repo named exactly `HarryTgerman.github.io` (the repo name must match your username).
2. From this directory:

   ```bash
   cd /Users/harrytrippel/resume/site
   git init
   git add .
   git commit -m "Initial portfolio + resume site"
   git branch -M main
   git remote add origin git@github.com:HarryTgerman/HarryTgerman.github.io.git
   git push -u origin main
   ```

3. In the repo settings on GitHub: **Settings → Pages → Source: Deploy from a branch → main / (root) → Save.**
4. Wait 1–2 min. Site is live at `https://harrytgerman.github.io/`.

### Option B — overwrite the existing `Resume` repo

If you want to keep the current URL (`https://harrytgerman.github.io/Resume/`), push these files into the existing `Resume` repo's main branch and update Pages settings to deploy from main.

The user-site repo (Option A) is the better URL. Recruiters will trust a root domain more than a `/Resume/` subpath.

## What to paste into applications

| Field | What to paste |
|---|---|
| Resume / CV upload | The generated `Harry-Trippel-Resume.pdf` |
| LinkedIn / portfolio / website | `https://harrytgerman.github.io/` |
| Any other relevant link | Same as above, OR a deep-dive page like `.../deflation.html` if the role is agent-platform-specific |
| GitHub | `https://github.com/HarryTgerman` |

## Updating content later

Everything lives in plain HTML. To update:

1. Edit the relevant `.html` file or `css/style.css`.
2. If it's the resume, re-run the "Generating the PDF" steps above.
3. `git add . && git commit -m "Update X" && git push`.
4. GitHub Pages redeploys within 1–2 min.

## Design tweaks

The whole visual language is in `css/style.css`. Color, typography, and spacing variables are at the top — adjust there to retune the aesthetic without touching content. Print rules are at the bottom in `@media print`.
