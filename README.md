# Timer App

Elegant countdown timer with voice announcements, system volume ducking, and background music.  
Runs as an **Electron desktop app** or as a **standalone `timer.html`** in any modern browser.

---

## Quick Start

### 1. Install dependencies

```bash
cd timer-app
npm install
```

> **Windows note:** The `loudness` package compiles a native addon.  
> You need [node-gyp prerequisites](https://github.com/nodejs/node-gyp#on-windows):  
> `npm install --global windows-build-tools` (run as Administrator), or install  
> "Desktop development with C++" via Visual Studio Installer.

### 2. Run in development

```bash
npm start
```

### 3. Build a distributable

```bash
npm run build
```

Outputs to `dist/`:
- **macOS** → `Timer-1.0.0.dmg` (universal: arm64 + x64)
- **Windows** → `Timer Setup 1.0.0.exe` (NSIS installer, x64)

---

## Browser-only mode

Open `timer.html` directly in Chrome or Edge — no install needed.  
System volume ducking requires Electron; everything else works in-browser.

---

## App icon

Place your icon files in the `timer-app/` folder before building:

| File         | Size    | Used for              |
|--------------|---------|-----------------------|
| `icon.icns`  | 1024px  | macOS DMG + dock      |
| `icon.ico`   | 256px   | Windows installer     |
| `icon.png`   | 512px   | Linux / tray fallback |

A placeholder tray icon is generated automatically if `icon.png` is missing.

---

## Features

- **HH:MM:SS duration** — click any field to edit; Tab moves between fields
- **Progress ring** — gold → amber (≤ 2 min) → red (≤ 30 sec)
- **4 reminder checkpoints** — fully editable MM:SS times, toggle each on/off
- **Voice announcements** — Web Speech API with voice selector
- **Final alarm** — soft sine-tone beep at 0:00 (no audio file needed)
- **Background music** — drag & drop any audio file; loops while timer runs
- **Volume ducking** — music fades to 30% during announcements, restores after
  - In-app audio: Web Audio API GainNode
  - System audio: `loudness` package (Mac + Windows, Electron only)
- **Keep on top** — float the window above all other apps (Electron only)
- **Persistence** — all settings auto-saved to `localStorage`
- **Minimize to tray** — closing the window hides it; quit via tray right-click

---

## Platform notes

| Feature               | Browser | Electron (Mac) | Electron (Win) |
|-----------------------|---------|----------------|----------------|
| Voice announcements   | ✅      | ✅             | ✅             |
| In-app audio ducking  | ✅      | ✅             | ✅             |
| System volume ducking | ❌      | ✅             | ✅             |
| Keep on top           | ❌      | ✅             | ✅             |
| Minimize to tray      | ❌      | ✅             | ✅             |
