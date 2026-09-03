# Ghar Khata — Offline PWA

A local-first household ledger. This build has **no backend** — every entry,
staff record, and bill lives only in this browser's `localStorage`, on this
device.

## How to use it

**Option A — just open the file.** Double-click `index.html`. It works
immediately; the only limitation is that "Install app" / offline caching via
the service worker needs the file to be served over `http(s)`, not opened as
a bare `file://` path (browsers block service worker registration on
`file://`). Everything else (data entry, saving, all tabs) works fine either
way.

**Option B — serve it locally, so you can install it as an app.**
From this folder, run any static file server, e.g.:

```
python3 -m http.server 8080
```

then open `http://localhost:8080` in Chrome/Edge/Safari and use the
browser's "Install app" / "Add to Home Screen" option. Once installed, it
keeps working with the device fully offline.

**Option C — host it anywhere** (GitHub Pages, Netlify, a spare web server,
your home NAS, etc.) by uploading this whole folder as-is.

## Data & backups

- All data is stored under `localStorage` keys prefixed `ghar_` on whichever
  browser + device this is opened in. It does **not** sync between devices
  or browsers — each install has its own independent data.
- Clearing site data / browser storage for this page will erase the ledger.
  There's no built-in export yet (see the project's "Not built" list).
- If you ever move to a new device or browser profile, there's currently no
  transfer path other than manually copying `localStorage` — flagging this
  as a known gap, not a hidden one.

## Files

- `index.html` — the whole app (HTML + CSS + JS in one file)
- `manifest.json` — PWA metadata (name, icons, theme colors)
- `sw.js` — service worker, caches the app shell for offline use
- `icons/` — app icons used by the install prompt / home screen
