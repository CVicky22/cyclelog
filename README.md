# CycleLog — Indoor Cycling Tracker

CycleLog is a lightweight, mobile-friendly web app for tracking cumulative readings from an indoor cycle meter. It is built with plain HTML, CSS, and JavaScript, so it does not require a build step, package manager, API key, or backend server.

> **Data and privacy:** CycleLog stores entries in the browser's `localStorage`. It does not sync to Google Drive or a cloud database. Do not enter personal information into a public demo, and export backups regularly.

## Features

- Log the date and optional body weight.
- Enter cumulative ride time using hour, minute, and second selectors.
- Enter cumulative distance in kilometres and calories in the meter's displayed unit (`cal`).
- Automatically calculate differences from the last saved cumulative meter reading.
- View dashboard totals, daily activity, weight-goal progress, and a rough activity estimate.
- Review saved readings and export them as CSV for Excel.
- Download a JSON backup file for safekeeping.
- Installable Progressive Web App (PWA) support and a basic service worker for offline access after the app has loaded.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | App interface and application logic |
| `manifest.webmanifest` | PWA name, display mode, and theme settings |
| `sw.js` | Service worker and static-file cache |
| `.nojekyll` | Tells GitHub Pages not to run Jekyll processing on the static site |
| `.gitignore` | Excludes common local and personal backup files from Git |
| `LICENSE` | MIT license for this repository |

## Run locally

1. Download or clone this repository.
2. Open `index.html` in a modern browser to try the app.
3. For service-worker and installable-PWA behavior, serve the files over `localhost` or HTTPS. Opening the HTML file directly does not enable service workers.

## Publish with GitHub Pages

1. Create a GitHub repository named `cyclelog` (or another name you prefer).
2. Upload the **contents of this folder** to the repository root. Make sure `index.html` is at the top level, not hidden inside another folder.
3. Open the repository's **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main` and folder `/(root)`, then save.
6. Wait for the deployment to finish. The published address will appear in the Pages settings and usually looks like `https://YOUR-USERNAME.github.io/cyclelog/`.
7. Open that address in Chrome on your phone. Use Chrome's menu and choose **Install app** or **Add to Home screen**, if offered.

See the [official GitHub Pages quickstart](https://docs.github.com/en/pages/quickstart) for current screenshots and instructions.

## First-time setup

A fresh installation starts with **zero meter readings, an empty history, and no latest body-weight reading**. The target weight is preset to 69 kg and can be changed in Settings. To enter your existing historical records, start with the earliest date and work forward in chronological order:

1. Open CycleLog and go to **Settings & data**.
2. If you are starting from a cycle meter that already has accumulated readings, enter its current cumulative time, distance, and calorie readings as the baseline. If you want to manually reconstruct historical days from zero, leave the baseline at zero and enter readings from oldest date to newest date.
3. Set your target weight if you want to use the weight-progress feature (the initial target is 69 kg).
4. Save settings, then log the next cumulative reading after a ride.

The app calculates the difference between the new meter reading and the last saved reading. The date field defaults to today but allows earlier dates. The cycle meter should continue counting upward; if a reading is lower than the previous saved value, check it before saving.

## Backups and limitations

- Use **History → Export CSV** for a spreadsheet-friendly export of newly logged readings.
- Use **Settings & data → Download backup JSON** to keep a copy of the app state. The app does not currently have a JSON-import/restore button, so keep the file safe for reference.
- Data is tied to the browser, device, and website origin. Moving from a local file or another host to GitHub Pages creates a different storage location; old browser data will not automatically appear there.
- Clearing browser/site data can erase saved entries. Keep backups somewhere safe.
- The CSV export is not a full copy of the original workbook and this app does not edit `.xlsx` files or update Google Drive.
- Weight and activity predictions are approximate and should not be treated as medical advice or a promise of weight change.

## Cost

The app itself is static and has no paid API dependency. GitHub Pages is available for public repositories on GitHub Free. Public repository contents and the published site can be viewed by anyone, so do not commit personal records, exported CSVs, JSON backups, credentials, or private files.

## Contributing

For personal experimentation, you can create a branch, make a change, and commit it. If you later want to share improvements, open a pull request describing what changed and how you tested it.
