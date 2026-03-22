# Changelog

## 1.2.3

### Linux (Wayland) — Initial Release
- Full port of KayZeer to Linux with Wayland-first architecture
- Screen capture via wlr-screencopy (Sway, Hyprland) and PipeWire portal (KDE, GNOME)
- GPU-accelerated detection pipeline (wgpu compute shaders)
- Layer-shell overlay with hint badges, status bar, and mouse mode
- Keyboard grab via evdev with modifier-safe grab/ungrab lifecycle
- System tray via StatusNotifierItem (D-Bus/ksni)
- Configuration persisted to ~/.config/kayzeer/config.toml
- Hotkey recorder UI with live reload to evdev monitor
- All macOS features ported except OCR text detection

### macOS
- Modifier key hints now displayed above status bar badges for quick reference

### Stability (macOS)
- Fixed stream recovery when waking from sleep on external monitors
- Fixed streaming lifecycle issues when toggling disable, waking from sleep, or changing displays

## 1.2.2

### Hint Labels
- New **Overlap Handling** setting — choose between truncating overlapping labels or leaving them as-is
- Truncate mode shows shortened labels (2 chars + peek) when hints overlap, making dense areas more readable
- Fixed duplicate hint labels appearing across different screens

### Other
- Default detection pipeline changed to Basic for faster out-of-box performance

## 1.2.1
- Move search/status bar to middle of screen, it was being obscured by the macbook notch.

## 1.2.0

### OCR Text Detection
- New **Enhanced (with OCR)** detection pipeline that recognizes on-screen text alongside UI elements
- OCR elements display their detected text directly on the overlay
- Duplicate or prefix-ambiguous OCR texts are automatically numbered for disambiguation (e.g. "Save1", "Save2")

> **Note:** OCR text detection is still experimental. It is slower than the legacy pipeline and I had to resort to running a service in the background for preprocessing, so battery life may be affected.

### Unified Search
- Type to filter both hint labels and OCR text simultaneously. If ocr hint labels conflict with non-ocr labels use **/** to toggle OCR-only mode (see below).
- Fuzzy matching finds close OCR text matches as you type
- Press **/** to toggle OCR-only mode — hides non-OCR labels and searches only text elements
- Use **arrow keys** to cycle through OCR matches and **Enter** to select
- Backspace always works — typing past all matches no longer dismisses the overlay
- Exact hint label matches auto-execute immediately, even when OCR matches exist

### Status Bar
- Always-visible status bar at the top of the overlay
- **OCR** badge — highlights when OCR-only mode is active (toggled with `/`)
- **LEFT** / **DBL** (double-click) / **RIGHT** / **MOVE** badges — show the current click action
- Modifier keys now **toggle** click actions instead of requiring hold:
  - Control toggles single ↔ double click
  - Option cycles left click → right click → move cursor
- Search query and match count displayed inline when filtering

### Mouse Mode
- New **Mouse Mode** (`⇧⌘;`) — full keyboard-driven mouse control
- **h/j/k/l** — move cursor (vim-style), hold **Shift** for fast movement
- **u** — left click (press twice quickly for double-click, hold + move to drag/select)
- **i** — middle click
- **o** — right click (hold + move to drag)
- **y/n** — scroll up/down
- **Esc** — exit mouse mode
- Hotkey is configurable in the Shortcuts section

### Detection Pipelines
- Renamed pipelines: **Basic** (fast, no OCR) and **Enhanced (with OCR)**
- Background OCR is skipped entirely when using the Basic pipeline for improved performance
- OCR display options: "Hint labels" (blue-colored labels) or "Show detected text" (overlay text on elements)

### Configuration
- Reset to Defaults button added to the Detection section
- Default OCR display mode is now "Show detected text"
- Debug sliders for all Enhanced pipeline parameters (blur, canny, tiling, merge, filter)
- Action modifiers simplified: Control toggles single/double click, Option cycles left/right/move

## 1.1.1
- Fix manual points not being saved.

## 1.1.0

### Vim-like actions
- Repeat last action (`.` during hints, or configurable hotkey ⇧⌘.)
- Command history overlay (`,` during hints, or configurable hotkey ⇧⌘,) — shows recent targets as labelled hints without re-running detection
- Multiple click types via modifier keys: double-click (⇧), right-click (⌃), move cursor (⌥)
- All modifier-to-action mappings are configurable

### Manual point management
- Drag to reposition manual points in the overlay
- Delete button on point markers now works correctly
- Points display as a list in the configuration window
- Points saved via any path now appear consistently in all views

### Configuration
- Option to include manual points in history overlay (default: on)

### Performance
- Greatly reduced latency by using screen capture streaming instead of a full-screen capture.

## 1.0.1

- Fix and simplify point distribution.
- Improve element detection.
- Add minimum distance between points filter.

## 1.0.0

Initial release.

- Keyboard-driven UI element detection and click navigation
- Configurable activation shortcut, character set, and hint style
- Multiple label distribution modes (Linear, Random, Hilbert, Grid, etc.)
- Multi-monitor support with monitor prefixes
- Manual click points for persistent targets
- Menu bar app with no Dock icon
