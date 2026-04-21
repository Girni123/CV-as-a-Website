# David Girnstein — CV Website

Personal landing page built for GitHub Pages. Shared via QR code / NFC tag at job fairs.

## Deploy

1. Push this folder to a GitHub repo
2. `Settings → Pages → Source: Deploy from a branch` (root of `main`)
3. Done. The `.nojekyll` file is already included so Pages won't re-process anything.

Works locally too: open `index.html` in a browser, or run `python3 -m http.server` and visit `http://localhost:8000`.

## Files

```
index.html                     → Single-file site (HTML + CSS + JS)
.nojekyll                      → Tells GitHub Pages to serve as-is
assets/
  profile.jpg                  → Hero photo
  DavidGirnstein_CV.pdf        → CV download (linked from the primary button)
  DavidGirnstein.vcf           → vCard — opens Contacts on iOS/macOS/Android/Windows
  favicon.svg                  → Tab icon
README.md                      → This file
```

## Updating content

Everything lives in `index.html`. Search for the section you want to edit (`PRODUCT & TECH EXPERIENCE`, `SKILLS`, `EDUCATION`, etc.) — each is commented at the top.

To replace the CV PDF, just overwrite `assets/DavidGirnstein_CV.pdf`. Same for the profile image (`assets/profile.jpg`).

## Enabling multiple CV versions later

The switcher at the top is built in but hidden. To turn it on:

1. Open `index.html`, find `<div class="version-switcher" id="versionSwitcher" …>`
2. Change the class from `version-switcher` to `version-switcher is-enabled`
3. Add more pills below the existing one:

   ```html
   <button class="version-pill" data-version="creative">Creative</button>
   <button class="version-pill" data-version="management">Management</button>
   ```

4. In the bottom `<script>` there's a placeholder handler (`console.log('Switch CV version to:', target)`). Replace it with whatever routing you prefer — e.g. `fetch('/versions/' + target + '.html')` and inject into `<main>`, or just navigate to a separate HTML file per version.

Until then, only the current `Product / Tech` version loads by default.

## Design

- Dark theme with lime-green accent `#CDFF00` (matches the personal-branding palette)
- Inter font via Google Fonts
- Responsive grid — tested on mobile (< 600 px), tablet, desktop
- Smooth reveal-on-scroll, expandable experience cards, animated hero
- Fully static — no build step, no dependencies beyond the Google Font
