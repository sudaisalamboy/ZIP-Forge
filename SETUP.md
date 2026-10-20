# ZIP-Forge — Setup Guide

**⚡ ZIPForge — The Ultimate ZIP Editor.** Edit the contents of ZIP archives in one shot,
right from your phone — no extracting, manually editing, and re-compressing. ZIPForge is a
mobile-first, browser-based tool whose headline feature is **bulk replace**: swap text
across hundreds of files inside a ZIP instantly.

**Made by Sudais Alam**

---

## Table of Contents

- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running Locally](#running-locally)
- [Project Structure](#project-structure)
- [Troubleshooting](#troubleshooting)
- [Credit](#credit)

---

## Project Overview

ZIPForge is a **mobile-first ZIP editor**. Instead of the usual extract → edit → re-zip
loop, it lets you perform in-place edits on a ZIP archive in a single pass — most notably
**bulk find-and-replace** across every file inside the archive at once. It is designed to
run in the browser (and as an installable PWA on your phone), so there is nothing to install
on your device beyond opening the page.

Headline capability:

- **📂 Bulk Replace** — swap text across hundreds of files inside a ZIP instantly, then
  re-download the updated archive.
- **📱 Phone-first UI** — large touch targets, mobile layout, works offline once installed.
- **⚡ One-shot workflow** — pick a ZIP, define replacements, get a new ZIP back.

ZIPForge is built with love as a browser-based tool — the only thing you need is a modern
web browser on your phone or desktop.

---

## Prerequisites

| Tool | Version | Notes |
|------|---------|-------|
| **A modern web browser** | Chrome, Edge, Firefox, Safari (current) | Mobile or desktop |
| **ZIP files to edit** | any `.zip` | The archives you want to bulk-edit |
| **(Optional) A local static server** | any | Only if you self-host the app |

No Node.js, npm, or build tools are required for end users — ZIPForge runs in the browser.
(If you intend to build/develop ZIPForge itself, see the *Running Locally* section.)

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/sudaisalamboy/ZIP-Forge.git
cd ZIP-Forge
```

### 2. (End users) Just open the app

If you are only using ZIPForge, you do not need to clone anything — open the hosted app in
your phone's browser and, if your browser supports it, **Add to Home Screen** to install it
as a PWA for offline use.

### 3. (Self-hosting) Serve the files

To run your own copy, serve the repository over HTTP with any static server:

```bash
# Python 3
python3 -m http.server 8000

# Node.js (http-server)
npx http-server -p 8000
```

Then open <http://localhost:8000/> (or your machine's IP on your phone) in a browser.

---

## Running Locally

### Option A — Open directly

Open the app's entry HTML file in your browser, or visit the hosted URL.

### Option B — Serve over HTTP (recommended for full PWA features)

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/  (or http://<your-ip>:8000/ on your phone)
```

### Using the app

1. **Pick a ZIP** — choose a `.zip` file from your device.
2. **Define replacements** — enter the find/replace pairs you want applied across all files
   in the archive.
3. **Run bulk replace** — ZIPForge applies every replacement to every matching file inside
   the ZIP in one shot.
4. **Download** — save the updated `.zip` back to your device.

### Install as a PWA (phone)

Open the app in Chrome/Safari on your phone → browser menu → **Add to Home Screen**. ZIPForge
will then launch full-screen and work offline.

---

## Project Structure

```
ZIP-Forge/
├── README.md        # Project overview + feature highlights
├── SETUP.md         # This file
├── LICENSE          # License
└── preview/
    └── preview.png   # Dark-theme preview banner (1200x750)
```

> Note: the runnable app source is described by the README as a mobile-first ZIP editor. The
> files in this repository are the project's documentation and preview assets. See the
> README for the feature list and the live/hosted app for usage.

---

## Troubleshooting

**The ZIP won't open / "unsupported format"**
- ZIPForge works with standard `.zip` archives. Re-save the archive as a plain ZIP if it is
  a `.rar`, `.7z`, or other format.
- Very large archives may be limited by your device's memory when opened in-browser.

**Bulk replace did not change some files**
- The match is text-based. Binary files (images, compiled binaries) are skipped or untouched.
- Check that your find string is an exact match (case-sensitive where applicable).

**Re-downloaded ZIP is corrupted**
- Make sure the download completed fully before opening.
- Try a different unzip tool — some older tools are stricter about ZIP metadata.

**PWA install option missing**
- Use Chrome or Edge on Android, or Safari on iOS. Firefox on desktop does not show the
  install prompt.
- You must serve the app over HTTPS (or `localhost`) for the install prompt to appear.

**App won't load over `file://`**
- Some browser features are restricted on `file://`. Serve over `http://localhost` using
  `python3 -m http.server` as shown above.

---

## Credit

**Made by Sudais Alam** — <https://github.com/sudaisalamboy>
