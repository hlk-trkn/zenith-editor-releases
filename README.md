# Zenith Editor

Zenith Editor is a local-first desktop subtitle editor for short-form video.

This repository is release-only (binaries, docs, and release notes). Zenith Editor source code is currently private.

## Download

- Latest release page (macOS + Windows):
  - macOS: https://github.com/hlk-trkn/zenith-editor-releases/releases/latest
  - Windows: https://github.com/hlk-trkn/zenith-editor-releases/releases/latest
- On that page, download:
  - macOS build: `Zenith.Editor_*_aarch64.dmg`
  - Windows build: `Zenith Desktop_*_x64_en-US.msi`
- Install:
  - macOS: open DMG, drag `Zenith Desktop.app` to Applications.
  - Windows: run MSI, then launch from Start Menu.

If Windows shows SmartScreen warning on first run, click `More info` -> `Run anyway`.

## FFmpeg Dependency (Required)

Zenith needs both `ffmpeg` and `ffprobe` on both macOS and Windows.

### macOS (Homebrew)

Quick install (recommended):

```bash
if ! command -v brew >/dev/null 2>&1; then
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
fi
brew install ffmpeg
```

If Terminal says `brew: command not found` after install, run:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
brew install ffmpeg
```

### Windows (choose one package manager)

Winget (recommended):

```powershell
winget install --id Gyan.FFmpeg -e
```

Chocolatey:

```powershell
choco install ffmpeg -y
```

Scoop:

```powershell
scoop install ffmpeg
```

### Verify install

Run in terminal (macOS/Linux) or PowerShell (Windows):

```bash
ffmpeg -version
ffprobe -version
```

Then fully close and reopen Zenith Editor.

Note: Homebrew is for macOS. On Windows use Winget/Chocolatey/Scoop or install FFmpeg manually and add it to `PATH`.

## Screenshots
Click any screenshot to open full resolution.

<table>
  <tr>
    <td align="center">
      <a href="docs/screenshots/editor-overview.png">
        <img src="docs/screenshots/editor-overview.png" alt="Editor Overview" width="360" />
      </a>
      <br />
      <sub>Editor Overview</sub>
    </td>
    <td align="center">
      <a href="docs/screenshots/timeline.png">
        <img src="docs/screenshots/timeline.png" alt="Timeline" width="360" />
      </a>
      <br />
      <sub>Timeline</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <a href="docs/screenshots/subtitles-panel.png">
        <img src="docs/screenshots/subtitles-panel.png" alt="Subtitles Panel" width="360" />
      </a>
      <br />
      <sub>Subtitles Panel</sub>
    </td>
    <td align="center">
      <a href="docs/screenshots/export-result.png">
        <img src="docs/screenshots/export-result.png" alt="Export Result" width="360" />
      </a>
      <br />
      <sub>Export Result</sub>
    </td>
  </tr>
</table>

## Quick How To Use

1. Import media in **Project Assets** (`+` button or drag-drop).
2. Place clips on timeline tracks.
3. Select a video clip and click **Generate Local Subtitles**.
4. Style subtitles in **Subtitles** tab (font, size, text color, background, vertical alignment).
5. Click **EXPORT** to render MP4.

## Whisper Models

Supported models:

- `whisper-tiny` (~75 MB)
- `whisper-small` (~466 MB)
- `whisper-medium` (~1.53 GB, default)
- `whisper-large-v3-turbo` (~1.60 GB)

Speed vs accuracy guide:

- **Tiny**: fastest, lowest accuracy. Best for quick drafts.
- **Small**: fast with better quality than tiny. Good for iteration.
- **Medium**: best overall balance for most users.
- **Large V3 Turbo**: strongest accuracy on difficult/noisy audio, heaviest runtime.

### Model download

- Open **Inspector -> Subtitles**.
- Select the model.
- Click **Download Model**.
- Missing models can auto-download when generation starts.


### Open-Source Dependencies
Zenith Editor relies on open-source components:
- FFmpeg / ffprobe (media decode/encode/render pipeline)  
  Project license: LGPL-2.1-or-later, with optional GPL components depending on build.
- whisper.cpp (local ASR runtime)  
  License: MIT
- OpenAI Whisper models/code (speech-to-text model family)  
  License: MIT
- whisper-rs (Rust bindings used by Zenith backend)  
  License: Unlicense

For full attribution and license references, see `THIRD_PARTY_NOTICES.md`.

Note: Zenith currently expects FFmpeg to be installed on the user system and does not bundle FFmpeg binaries in the app package.
Custom/community Whisper models may use different licenses; check each model page before use.
