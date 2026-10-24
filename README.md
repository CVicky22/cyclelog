# CycleLog — GitHub Pages release v2.9

A lightweight, mobile-friendly indoor cycling tracker built with plain HTML, CSS, and JavaScript. No build step, API key, package manager, or backend is required.

## Fresh starting values

This release starts with:
- Cumulative ride time: **0**
- Cumulative distance: **0 km**
- Cumulative calories: **0 cal**
- Completed ride history: **empty**
- Pending start readings: **empty**
- Latest body weight: **none**
- Target weight: **69 kg** (intentional goal default; change it in Settings)
- Weekly distance goal: **50 km** (intentional goal default; change it in Settings)

For a clean start, this release uses new local-storage keys (`cyclelog-v3` and `cyclelog-pending-v2`). Data previously stored under the older CycleLog keys is not shown by this release, but is not automatically deleted from the browser. This avoids destructive data deletion while starting fresh. Browser storage is local to each site origin and device.

## Files in this folder

- `index.html` — app interface and application logic; required at the repository root.
- `sw.js` — service worker for offline caching; cache version incremented for this release.
- `manifest.webmanifest` — installable PWA metadata.
- `.nojekyll` — disables Jekyll processing for GitHub Pages.
- `.gitignore` — excludes local/editor files and personal exports/backups.
- `README.md` — project and publishing instructions.
- `LICENSE` — MIT license.

## Upload to GitHub

1. Extract `CycleLog-GitHub-Upload-v2.9.zip`.
2. Open your GitHub repository (the `cyclelog` repository if you are using the existing project).
3. Upload the **contents** of the extracted folder to the repository root. Do not upload the ZIP itself as a substitute for the files. Ensure `index.html`, `sw.js`, and `manifest.webmanifest` are directly at the root, not inside another folder.
4. Commit the changes to your main branch.
5. In GitHub, open **Settings → Pages** and confirm publishing from the `main` branch and `/(root)`.
6. After deployment, open the published site and test the welcome page, saving a sample ride, history, theme switching, backup download, reset confirmation, and offline behaviour.

## Offline behaviour

The app can work offline after the page and service worker have loaded successfully. Service workers require HTTPS or localhost; opening `index.html` directly with `file://` is not a valid offline/PWA test.

## Data and backups

CycleLog stores ride records in browser `localStorage`; it does not sync to a cloud database. Download a JSON backup regularly. The app currently provides backup export but not a JSON restore/import function. Never commit personal CSV exports or JSON backups to a public repository.

## Current limitations

- Data does not automatically sync between browsers or devices.
- Existing data saved under older storage keys is not displayed by v2.9. It is left in browser storage and can be recovered by using the prior app version, unless browser/site data is cleared.
- Predictions are estimates, not promises of weight change.
