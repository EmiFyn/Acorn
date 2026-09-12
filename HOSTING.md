# Putting Acorn on a phone

This folder is the whole app. It makes **no external requests at all** — no CDN,
no font server, no lookup download — so once installed it behaves identically
with no signal.

## What it needs

One HTTPS address. That is the only requirement, and it is not negotiable:
browsers refuse to install an app or run a service worker over plain HTTP. The
one exception is `http://localhost`, which is treated as secure — useful for a
quick look on the PC, no use on a phone.

## The quickest host: GitHub Pages (free, about five minutes)

1. Create a repository — it can be private; Pages still serves it on a paid
   plan, or make it public if the forms carry nothing sensitive. **These files
   carry no crew or customer data**, only the blank forms and the network
   lookup.
2. Upload the contents of this folder to the root of the repository — the files
   themselves, not the folder.
3. **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)` → Save.**
4. Wait a minute. The address appears on that page, in the form
   `https://<you>.github.io/<repo>/`.

Anything else that serves static files over HTTPS works just as well —
Cloudflare Pages, Netlify, an IIS folder on the company server. There is no
server-side code, no database and no build step.

## Installing on Android

1. Open the address in **Chrome** on the phone.
2. Wait for it to finish loading once — that is when it takes its copy.
   The app is 8 MB, so do this on wifi.
3. **⋮ → Add to Home screen** (Chrome may offer "Install app" itself).
4. Open it from the home screen, not from Chrome. It runs full screen with no
   address bar, and it is now offline-capable.

To prove it: turn on aeroplane mode and open it again. Everything works —
every form, the 3,152-CMR lookup, and PDF generation.

## Installing on Windows

Same address in Chrome or Edge → the install icon at the right of the address
bar → Install. It gets a Start-menu entry and its own window.

## Updating it

Replace the files and the crews pick it up next time they open the app with a
signal. They are told, not interrupted: a sheet in progress is never reloaded
underneath them, and the new version is used on the next launch.

## What is not in this build

- **Sending email.** There is no transport yet, so sync writes to a store in the
  browser rather than sending anything. Everything up to that point — building
  the PDFs, filing them, composing the subject and body — is real.
- **Filing PDFs into folders** works in Chrome on Android 132+ and on Chrome or
  Edge on Windows. Where the browser has no folder access the Save button on the
  finish screen still works and the settings screen says so.
