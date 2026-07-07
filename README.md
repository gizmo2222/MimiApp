# Mimi's 3D Print Shop

A single-page, kid-friendly "pretend store" for browsing 3D-printable items, picking a filament color, and sending a print order to Mimi.

No backend, no accounts, no localStorage — everything lives in memory for the session.

## How it works

1. Pick an item from the catalog (dragon, T-Rex, race car, etc.)
2. Pick a filament color
3. Add it to the print list (repeat for more items)
4. Optionally add a note
5. Tap **Send Order to Mimi** — this uses the device share sheet (`navigator.share`) if available, falls back to a pre-filled text message or email if configured below, and falls back to copying the order to the clipboard as a last resort.

## Configuring

Edit the config block at the top of the `<script>` in [index.html](index.html):

```js
const MIMI = { name: "Mimi", phone: "", email: "" };
```

- Leave `phone` and `email` blank to always use the device's native share sheet.
- Fill in `phone` (e.g. `+15551234567`) to fall back to a pre-filled SMS.
- Fill in `email` to fall back to a pre-filled email instead.

The `CATALOG` (printable items) and `COLORS` (filament colors) arrays are also editable in the same file.

**Note:** this is a public static page — anything in `index.html`, including a hardcoded phone/email, is visible in page source to anyone who opens it. Leave those fields blank if you don't want that info public.

## Deploying

This is a static site with no build step. It's deployed via GitHub Pages, serving directly from the repo root on the `main` branch.

To update: edit `index.html`, commit, push — live in about a minute.
