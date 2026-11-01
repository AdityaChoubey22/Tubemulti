# TubeMulti 📺👥

> **Free, open-source multi-account YouTube desktop client specifically built for Fedora Linux.**

TubeMulti allows you to run multiple YouTube accounts simultaneously in a single, lightweight desktop interface. Powered by **Electron** and **Electron Session Partitioning**, every account profile operates in total isolation (`persist:account_<id>`), ensuring that your YouTube/Google login tokens, cookies, browsing history, and localStorage remain independent and persist across app restarts.

---

## ⚡ One-Click Fedora Laptop Quick Start

### Option 1: System Application Launcher (Recommended)
We have automatically installed a system shortcut into your Fedora Application Menu.

1. Press Super/Windows key or click **Activities** in Fedora.
2. Search for **TubeMulti**.
3. Click the icon to launch!

Or run the installer script anytime:
```bash
./install-launcher.sh
```

### Option 2: Double-Click Executable Script
You can also launch TubeMulti instantly from your file manager or terminal:
```bash
./run.sh
```

---

## Features ✨

- 🔒 **Independent Account Partitioning**: Cookies, session storage, and auth tokens are completely isolated per profile (`persist:account_<id>`).
- 🎨 **Discord/Slack-Style Sidebar**: Vertical account switcher (~72px) with circular avatar bubbles, active profile indicators, smooth hover animations, and account accent colors.
- ⚡ **Zero-Flicker View Switching**: Dynamically mounts modern `WebContentsView` (with fallback to `BrowserView` for legacy Electron runtimes) to switch accounts instantly without reloading pages.
- 🌙 **Native Dark Theme**: Designed around YouTube's dark theme aesthetic (`#0f0f0f` background, `#212121` surface cards, `#ff0000` accents).
- 🧭 **Built-In Top Navigation**: Integrated Back, Forward, Refresh, and Home buttons with live title updates and active account badge.
- 🛡️ **Hardened Security**: Built with `contextIsolation: true`, `nodeIntegration: false`, and `sandbox: true`. External links automatically open safely in your default web browser.
- 🌐 **Offline & Error Resilience**: Network connectivity detection and load failure error handling with retry support.
- 📦 **Fedora `.rpm` Packaging**: Ready to build native Fedora Linux packages using `electron-builder`.

---

## File & Folder Structure 📁

```
tube-multi/
├── run.sh               # One-click launcher script
├── install-launcher.sh  # Desktop menu shortcut installer
├── package.json          # Node dependencies and electron-builder RPM build setup
├── main.js              # Electron main process (WebContentsView adapter, session storage)
├── preload.js           # Secure contextBridge IPC bridge
├── src/
│   ├── index.html       # Sidebar shell, navigation bar, and account modal
│   ├── styles.css       # YouTube dark theme design system
│   └── renderer.js      # Sidebar DOM controller, modal management, and network listeners
├── assets/
│   ├── icon.svg         # Vector app icon
│   └── icon.png         # High-resolution 512x512 PNG app icon
└── README.md            # Documentation and build guide
```

---

## Packaging as `.rpm` for Fedora Linux 📦

To build a native `.rpm` package for Fedora Linux:

```bash
npm run build:rpm
```

The output RPM package will be generated inside the `dist/` directory:

```
dist/
├── TubeMulti-1.0.0.x86_64.rpm
└── TubeMulti-1.0.0.AppImage
```

### Installing the Generated `.rpm` Package

Install the app on your Fedora system via `dnf`:

```bash
sudo dnf install ./dist/TubeMulti-1.0.0.x86_64.rpm
```

---

## License 📜

Distributed under the **MIT License**. Free and open-source forever.
