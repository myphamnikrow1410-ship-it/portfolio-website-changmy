# Pham Hong Chang My — Business Analyst Portfolio

This is the **complete editable source project** for the approved two-page portfolio, with the final muted rose / lavender-white color system applied. The content, page structure, layout, spacing, typography, photos, interactions and external links are inherited from the approved version. No framework, remote font, backend, runtime package or API key is necessary.

## Website pages

- `/` — profile and contact, About Me, Background, three expandable projects (HiTalent, Sân Vui, Giúp việc nhanh), Skills.
- `/projects/hitalent/` — existing eight-section HiTalent case study and deliverable library.

## Start locally (simplest)

1. Extract the ZIP; open the folder containing this README and `index.html`.
2. Open `index.html` in Chrome or Edge. For correct local directory navigation, start a local server instead:

   ```bash
   python -m http.server 8000
   ```

3. Open `http://localhost:8000/` and `http://localhost:8000/projects/hitalent/`.

The site is already built. You do **not** need to install any JavaScript packages just to view it.

## File structure

```text
index.html                     Built homepage
projects/hitalent/index.html  Built case study
assets/styles.css             Shared light/dark themes and all layouts
assets/site.js                Theme toggle, menu, disclosure deep links, copy email
assets/theme-init.js          Restore theme before paint
assets/favicon.svg            Original MY favicon, recolored
assets/images/                Four supplied, optimized project/portrait images
src/content.json              Single editable factual content source
scripts/build.mjs             HTML generator for both pages
scripts/prepare-public.mjs    Packages only browser files into public/
public/                       Generated deployment output (not checked into Git)
package.json                  Build scripts; no third-party dependencies
vercel.json                   Static Vercel deployment settings
.gitignore, .nojekyll         Repository settings
QA-results.txt                Automated checks and remaining limitations
```

No fonts are bundled: the existing `Inter, system-ui` CSS font stack is unchanged.

## Color system (the only UI change from the previously approved website)

Update the variables at the beginning of `assets/styles.css` if you ever need to adjust the colors:

| Token | Light |
| --- | --- |
| Outer page `--page` | `#F5F4F8` |
| Main rail `--surface` | `#FCFCFC` |
| Primary text `--text` | `#302C35` |
| Secondary text `--muted` | `#716A72` |
| Accent/button `--accent` / `--button` | `#A45D78` |
| Primary button hover `--button-hover` | `#87465F` |
| Primary button text `--button-text` | `#FFFFFF` |
| Main dividers `--border` | `#E8E6EC` |
| Secondary button border `--control` | `#DCD6E3` |

Tags and email boxes use a subtle pale-rose tint (`--surface-alt`). Accent-colored small text uses the darker rose (`--accent-ink`) for contrast. A coherent separate dark palette is defined in `:root[data-theme=dark]`. The SVG favicon and browser `theme-color` metadata are updated too.

## Editing and rebuilding

The current `index.html` and case-study HTML are **generated** files. To edit text, links and projects, change `src/content.json`, not two different HTML files. To edit the theme, change the variables in `assets/styles.css`.

Node.js 18+ is required **only** for regeneration/deployment build, not for preview:

```bash
npm run build           # regenerates both HTML pages
npm run build:deploy    # regenerates and assembles public/ for Vercel
```

The original `npm run build:release` command still exists for an optional production variant that suppresses development-only pending-file messages. The **current approved version**, including those messages on the case study, is what `npm run build:deploy` preserves by default.

## Upload to GitHub

1. Create a new **empty repository** on [GitHub](https://github.com/new) (e.g. `chang-my-ba-portfolio`). Do not add a README on GitHub if you plan to push this existing folder.
2. Open Terminal/PowerShell/Git Bash in the extracted folder and run:

   ```bash
   git init -b main
   git add .
   git commit -m "Add Business Analyst portfolio"
   git remote add origin https://github.com/YOUR-USERNAME/chang-my-ba-portfolio.git
   git push -u origin main
   ```

   Replace `YOUR-USERNAME` with your actual GitHub username. Sign in when prompted. GitHub Desktop is also a suitable alternative if you prefer not to use the command line.

3. `public/` is ignored by Git because Vercel regenerates it on deployment. The committed repository contains all source files and assets.

## Deploy on Vercel from GitHub (recommended)

1. Log in at [Vercel](https://vercel.com/new) and select **Add New → Project**.
2. Connect your GitHub account and **Import** the repository just created.
3. The supplied `vercel.json` sets the build command to `npm run build:deploy`, output directory to `public`, and trailing slashes on. You do not need any environment variables. Use the default project root.
4. Click **Deploy**. After the build, Vercel will provide a real `*.vercel.app` deployment address. The two pages are `/` and `/projects/hitalent/`.
5. Check the domain in an incognito browser and confirm any **Deployment Protection** setting permits public access. Share the verified production URL.

Vercel automatically redeploys when you push future changes to the connected repository.

### Deploy without GitHub

Extract the source ZIP, install Node.js LTS, then run `npx vercel --prod` from the project root, sign into your Vercel account and follow the prompts. Vercel reads `vercel.json` and builds `public/` before deployment.

## Review before publishing publicly

- The profile portrait and phone/email/location are **already part of the website**, so check you are comfortable publishing them.
- Existing project URLs and seven certificate/language URLs were copied unchanged. Confirm they permit public read access.
- Screenshots are project UI mockups. The previous approved package masked the screenshot password-like field and mock login phone number; no new image editing was performed in this palette update.
- Individual downloadable HiTalent artifacts remain **unavailable**; the case study intentionally lists some as `File pending`. A downloadable CV PDF is not included; no fake CV link was added.
- No Vercel deployment or shareable URL is created by this ZIP alone; you must deploy to your own account.

## Verification

See `QA-results.txt` for the color, geometry, accessibility spot checks and interaction results. No screenshots, colors or decoration are generated by a separate image model; the screenshots/previews reflect the actual HTML/CSS/JS.
