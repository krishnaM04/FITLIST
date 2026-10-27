# My Workout — Personal Planner

A responsive, installable workout planner for Windows and phone. It uses no external libraries and stores your workout data locally in the browser.

## What it includes
- Six-day beginner bodyweight plan plus Sunday rest
- Exercise checklists and illustrated movement guides
- 30/60/90-second rest timer
- Weekly completion chart and progress snapshot
- Local settings and JSON export/import backup
- Installable PWA with offline caching

## Important about local-only data
Data is stored separately in each browser/device. It does not sync automatically between your Windows PC and phone. Use **Export data** and **Import backup** to move a backup between devices.

## Recommended setup: publish privately in practice, but do not upload personal data
The app itself contains no personal account or workout history; history stays in local browser storage. To install it on both Windows and phone, the app must be served from an HTTPS address. A static host such as GitHub Pages can serve these files; anyone who knows the URL may be able to open the app, so do not treat the URL as an access-control password. Your saved progress still stays in each device's browser. If you need the app page itself to be access-restricted, choose a hosting service with access control.

### Windows setup (test locally)
1. Install Python 3 if you do not already have it.
2. Extract the ZIP to a folder.
3. Open that folder in File Explorer.
4. Click the address bar, type `powershell`, and press Enter.
5. Run: `py -m http.server 8000`
6. Open `http://localhost:8000` in Chrome or Edge.
7. For an installable app, use the browser's Install icon/menu when available. Localhost is treated as a secure origin, so the PWA can install and cache offline.
8. Keep the server window open while using the localhost version. Closing it stops the local server.

### Use it on both Windows and phone
To access the same app on both devices without running a server on your PC all the time:
1. Upload the app folder contents to a static HTTPS host you trust (for example, GitHub Pages).
2. Open the HTTPS URL in Chrome/Edge on Windows and install it from the browser menu.
3. Open that same HTTPS URL on your phone and choose **Add to Home Screen** / **Install app** from the browser menu.
4. Open the app once while online so the offline cache can be installed.
5. Keep in mind the workout progress is still device-local. To move it, tap **Export data** on one device, transfer the JSON backup to the other device, then use **? → Import backup**.

### Files
- `index.html` — app interface and logic
- `manifest.webmanifest` — install metadata
- `sw.js` — offline cache
- `icon.svg`, `icon-192.png`, `icon-512.png` — app icons

## Updating the app
Replace the hosted files and increment the cache name in `sw.js` (for example, `my-workout-v2`) to ensure the browser fetches the new version.
