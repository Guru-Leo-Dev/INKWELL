# Inkwell — deploying to Vercel

## Deploy
1. Unzip this folder.
2. Easiest path: go to vercel.com → **Add New → Project** → drag this folder in (or push it to a GitHub repo first and import that repo). No build command, no framework — it's static files, so leave those settings blank/default.
3. Deploy. Vercel serves it over HTTPS automatically, which is what installability needs.

## Install it on your phone
Open the deployed URL in **Chrome** (Android) or **Safari** (iOS) — not inside another app's built-in browser/webview, since the install option only appears in a real browser tab.
- **Android Chrome:** menu (⋮) → "Install app" (or you may get an automatic install banner).
- **iOS Safari:** Share icon → "Add to Home Screen."

## What's included
- `index.html` — the app
- `manifest.json` — real file this time (not embedded as a data URI, which isn't a reliably-supported pattern)
- `sw.js` — service worker, caches the app shell for offline loads
- `icons/` — app icons at the required sizes

## Storage
Entries save to the browser's own `localStorage` on whatever device you open it on. That means:
- Persistence is per-device/per-browser, not synced across devices.
- Clearing site data/browser storage for this site will erase entries — export a backup from inside the app periodically (Backup section → Export backup) if that matters to you.
- If you ever open this same file through Claude instead, it automatically uses Claude's own storage there — no changes needed.

## Verified before sending
- Chrome DevTools Protocol installability check: 0 errors
- Manifest fetches and parses cleanly (name, icons, `display: standalone`)
- Service worker registers and reaches `activated` state over `http://localhost`
- A saved entry and a theme change both survive a real page reload
