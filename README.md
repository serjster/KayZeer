# KayZeer

Keyboard-driven screen navigation for macOS and Linux. Click anything (almost) without touching the mouse.

KayZeer detects interactive UI elements on your screen and overlays hint labels on each one. Type the letters to click — like Vimium, but for your entire desktop.

## Download

Get the latest release from the [Releases page](https://github.com/serjster/KayZeer/releases).

### macOS
1. Download the `.dmg` file
2. Open it and drag **KayZeer** to Applications
3. Launch KayZeer — it lives in your menu bar (no Dock icon)
4. Grant **Accessibility** and **Screen Recording** permissions when prompted

### Linux (Wayland)

> **Note:** Only tested on Arch Linux with KDE Plasma 6. Other distributions and compositors may work but are not officially supported.

#### Arch Linux (AUR)
```bash
yay -S kayzeer-bin
systemctl --user enable --now kayzeer.service
```

The AUR package installs the binary, a systemd user service, and a udev rule. If you use [keyd](https://github.com/rvaiya/keyd), the service automatically stops it while KayZeer is running and restarts it on exit.

#### Manual install
1. Download the `.tar.gz` file
2. Extract: `tar xzf KayZeer-*-linux-x86_64.tar.gz`
3. Add your user to the `input` group: `sudo usermod -aG input $USER` (log out and back in)
4. Run: `./kayzeer` — it appears in your system tray
5. On first launch, a screen sharing dialog appears — **select "Entire Workspace"** (not individual displays). Subsequent launches skip the dialog automatically.

**Runtime dependencies (Arch):**
```bash
sudo pacman -S --needed gstreamer gst-plugins-base-libs mesa dbus
```

These are typically already installed on a KDE desktop.

## Platform Feature Comparison

| Feature | macOS | Linux |
|---------|:-----:|:-----:|
| UI element detection | Yes | Yes (GPU-accelerated) |
| OCR text search | Yes | — |
| Multi-monitor prefixes | Yes | Yes |
| Label distribution (X/Y/XY/Concentric) | Yes | Yes |
| Hint style (Shrink / Gray out) | Yes | Yes |
| Overlap truncation (2 chars + peek) | Yes | Yes |
| Click action toggles (single/double/right/move) | Yes | Yes |
| Mouse mode (hjkl + clicks + scroll) | Yes | Yes |
| Repeat last action | Yes | Yes |
| Click history | Yes | Yes |
| Manual click points | Yes | Yes |
| Configurable shortcuts | Yes | Yes |
| Configuration persistence | Yes | Yes |

## How to Use

1. Press the activation hotkey to activate
2. Hint labels appear on every detected UI element
3. Type the hint letters to click that element
4. Press `Escape` to cancel, `Backspace` to correct

[![Activation](assets/activation.gif)](https://github.com/user-attachments/assets/b85b8bef-beb5-4f2a-ae1d-f55f03e2ead3)

### OCR Text Search (macOS only)

With the **Enhanced** pipeline, KayZeer detects on-screen text and overlays it directly on elements. Press **/** to toggle OCR-only mode, use arrow keys to cycle matches, Enter to select.

### Status Bar

A status bar shows the current state:
- **DBL** / **LEFT** / **RIGHT** / **MOVE** — current click action
- Modifier hints (Ctrl, Alt) above each badge
- Typed characters shown when filtering

### Vim-like Actions

- **Repeat last action** — re-click the last target without re-detecting
- **Command history** — show recent targets as labelled hints
- **Click type toggles:**
  - Ctrl — toggle single / double click
  - Alt (Option on macOS) — cycle left / right / move

### Mouse Mode

Full keyboard-driven mouse control:

| Key | Action |
|-----|--------|
| `h` `j` `k` `l` | Move cursor (left, down, up, right) |
| `Shift` + move | Fast movement (4x speed) |
| `u` | Left click |
| `i` | Middle click |
| `o` | Right click |
| `y` / `n` | Scroll up / down |
| `Esc` | Exit mouse mode |

### Configuration

Click the tray/menu bar icon and select **Configure...** to customize shortcuts, label settings, distribution modes, hint styles, and more. All settings persist across restarts.

## Requirements

### macOS
- macOS 14 (Sonoma) or later
- Accessibility + Screen Recording permissions

### Linux
- Arch Linux with KDE Plasma 6 (tested), other Wayland compositors may work
- Wayland compositor with wlr-layer-shell support
- User in `input` group (for evdev keyboard/mouse access)
- `gstreamer`, `gst-plugins-base-libs`, `mesa`, `dbus`

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for release history.

## License

KayZeer is free to use. See [LICENSE](LICENSE) for details.

## Contact

- Blog: [serjster.com](https://www.serjster.com)
- GitHub Issues: [Report a bug or request a feature](https://github.com/serjster/KayZeer/issues)
