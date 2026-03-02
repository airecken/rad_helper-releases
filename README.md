# RadHelper

**A workflow automation tool for diagnostic radiologists.** RadHelper runs quietly in the background, automating repetitive tasks across your radiology applications so you can focus on reading studies.

## What It Does

- **Window Management** — Automatically arranges your reading applications across monitors with customizable layouts
- **Keyboard Shortcuts** — Global and app-specific hotkeys to speed up common actions
- **Clario Integration** — Extracts patient and exam context from Clario via a Chrome extension
- **AI Prior Summaries** — Summarizes prior reports using a local LLM (Ollama) — no cloud, no PHI leaves your machine
- **Epic Integration** — Pulls relevant context from Epic Radiant/Hyperspace
- **Auto-Updates** — Checks for new versions automatically and applies them without reinstalling

All processing stays local. No data leaves your workstation.

---

## Download & Install

### 1. Download

Go to the [**Latest Release**](https://github.com/airecken/rad_helper-releases/releases/latest) and download **`RadHelper-v___-installer.zip`** (the zip file).

### 2. Install

1. **Extract** the zip to any folder (e.g., your Downloads folder)
2. **Double-click `Install-RadHelper.cmd`**
3. That's it — no admin rights required

The installer will:
- Install RadHelper to `%LocalAppData%\RadHelper` (~100 MB)
- Create a desktop shortcut
- Open the configuration dashboard in your browser

### 3. Open the Dashboard

After install, the dashboard opens automatically at **[http://127.0.0.1:5000](http://127.0.0.1:5000)**. Bookmark this URL for quick access. Use the dashboard to enable modules, configure window layouts, set up hotkeys, and manage settings.

---

## System Requirements

- Windows 10 or later
- No .NET install required (runtime is bundled)
- ~100 MB disk space
- For AI summaries: [Ollama](https://ollama.com/) installed separately

---

## Chrome Extension (for Clario integration)

If you use Clario, the installer places a Chrome extension at `%LocalAppData%\RadHelper\extension`. To load it:

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
| Need logs | Check `%LocalAppData%\RadHelper\logs\` |

---

## Release Files

Each release includes:

| File | Description |
|---|---|
| `RadHelper-v___-installer.zip` | **Download this.** Installer bundle with setup scripts. |
| `RadHelper.Agent.exe` | Standalone executable (for manual/portable installs) |
| `checksums.txt` | SHA-256 hashes for verifying downloads |
| `releases.json` | Signed update manifest (used by auto-updater) |
| `llama-models.json` | Recommended Ollama models for AI summaries |
