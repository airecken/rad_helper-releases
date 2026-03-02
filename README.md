# RadHelper

**A workflow automation tool for diagnostic radiologists.** RadHelper runs quietly in the background, automating repetitive tasks across your radiology applications so you can focus on reading studies.

## [![Download](https://img.shields.io/badge/Download_Installer-blue?style=for-the-badge&logo=windows)](https://github.com/airecken/rad_helper-releases/releases/latest/download/RadHelper-installer.zip)

---

## What It Does

- **Window Management** — Automatically arranges your reading applications across monitors with customizable layouts
- **Keyboard Shortcuts** — Global and app-specific hotkeys to speed up common actions
- **Clario Integration** — Extracts patient and exam context from Clario via a Chrome extension
- **AI Prior Summaries** — Summarizes prior reports using a local LLM (llama.cpp, bundled) — no cloud, no PHI leaves your machine
- **Epic Integration** — Pulls relevant context from Epic Radiant/Hyperspace
- **Auto-Updates** — Checks for new versions automatically and applies them without reinstalling

All processing stays local. No data leaves your workstation.

---

## Install

1. **Click the download button above** (or go to [Releases](https://github.com/airecken/rad_helper-releases/releases/latest))
2. **Extract** the zip to any folder
3. **Double-click `Install-RadHelper.cmd`** — no admin rights required

The installer will:
- Install RadHelper to `%LocalAppData%\RadHelper` (~100 MB)
- Create a desktop shortcut
- Open the configuration dashboard in your browser

### First-Run Setup

On first launch, a **setup wizard** walks you through configuration:

1. **Credentials** — Enter your Clario/Sectra credentials (optional, stored locally)
2. **AI Summary** — Install the llama.cpp runtime and download a recommended model with one click
3. **Chrome Extension** — Load the Clario integration extension

The wizard can be skipped and revisited later from **Settings > Run Setup Wizard**.

### Dashboard

The dashboard is at **[http://127.0.0.1:5000](http://127.0.0.1:5000)**. Use it to enable modules, configure window layouts, set up hotkeys, and manage settings.

---

## System Requirements

- Windows 10 or later
- No .NET install required (runtime is bundled)
- ~100 MB disk space (plus ~4 GB for an AI model, if using AI summaries)

---

## AI Summaries Setup

RadHelper bundles **llama.cpp** to run a local LLM for summarizing prior reports. No separate software install is needed — the setup wizard handles everything:

1. Open the setup wizard (auto-triggers on first launch, or **Settings > Run Setup Wizard**)
2. On the AI Summary step, click **Install Runtime** to download `llama-server`
3. Pick a model from the curated catalog and click **Download**

The LLM server runs on `127.0.0.1:18080`, managed automatically by RadHelper. Models are stored in `%LocalAppData%\RadHelper\models`.

---

## Chrome Extension (for Clario Integration)

The installer places a Chrome extension at `%LocalAppData%\RadHelper\extension`. To load it:

1. Open Chrome → `chrome://extensions`
2. Enable **Developer mode** (top right toggle)
3. Click **Load unpacked** → select the `%LocalAppData%\RadHelper\extension` folder

The extension connects RadHelper to Clario for automatic patient context extraction.

---

## Updating

RadHelper checks for updates automatically. When a new version is available, it appears on the dashboard Status page. Updates download and apply without reinstalling.

---

## Uninstalling

1. Open the folder where you extracted the installer
2. Double-click **`Uninstall-RadHelper.cmd`**

This stops RadHelper, removes the app files, and deletes the desktop shortcut. Your settings and logs are preserved. To remove everything, run `Uninstall-RadHelper.cmd purge` from a command prompt.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Dashboard not loading | Check if `RadHelper.Agent` is running in Task Manager. If not, use the desktop shortcut or run `Install-RadHelper.cmd` again. |
| Port conflict | Edit `%LocalAppData%\RadHelper\settings.json`, change `"port"` under `"server"`, restart RadHelper. |
| AI summaries not working | Open the setup wizard and verify the runtime is installed and a model is downloaded. Check the AI Summary module status on the dashboard. |
| Need logs | Check `%LocalAppData%\RadHelper\logs\` |
