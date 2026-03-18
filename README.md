# KayZeer

Keyboard-driven screen navigation for macOS. Click anything (almost) without touching the mouse.

KayZeer detects interactive UI elements on your screen and overlays hint labels on each one. Type the letters to click — like Vimium, but for your entire desktop. With the Enhanced pipeline, KayZeer also recognizes on-screen text via OCR, so you can type what you see to navigate.

## Download

Get the latest release from the [Releases page](https://github.com/serjster/KayZeer/releases).

1. Download the `.dmg` file
2. Open it and drag **KayZeer** to Applications
3. Launch KayZeer — it lives in your menu bar (no Dock icon)
4. Grant **Accessibility** and **Screen Recording** permissions when prompted

## How to Use

1. Press `Ctrl + Shift + Space` to activate
2. Hint labels appear on every detected UI element
3. Type the hint letters to click that element
4. Press `Escape` to cancel, `Backspace` to correct

[![Activation](assets/activation.gif)](https://github.com/user-attachments/assets/b85b8bef-beb5-4f2a-ae1d-f55f03e2ead3)

### OCR Text Search

With the **Enhanced** pipeline, KayZeer detects on-screen text and overlays it directly on elements. You can navigate by typing what you see:

1. Activate hints as usual
2. Start typing any text visible on screen — a search bar appears showing matches
3. Press **/** to toggle **OCR-only mode** — hides non-OCR labels for a cleaner search
4. Use **↑/↓ arrow keys** to cycle through matching OCR elements
5. Press **Enter** to click the selected match
6. **Backspace** to correct — the overlay stays active even with no matches

OCR matches are shown alongside regular hint labels. If multiple elements share the same text, they are automatically numbered (e.g. "Save1", "Save2") so each is uniquely identifiable. Exact hint label matches always auto-execute immediately.

### Status Bar

A status bar is always visible at the top of the overlay, showing:

- **OCR** — highlights when OCR-only mode is active (toggle with `/`)
- **LEFT** / **DBL** / **RIGHT** / **MOVE** — shows the current click action

### Vim-like Actions

KayZeer supports vim-inspired shortcuts during hint mode:

- **Repeat last action** — press `.` during hints (or `⇧⌘.` anytime) to re-click the last target
- **Command history** — press `,` during hints (or `⇧⌘,` anytime) to show recent targets as labelled hints without re-running detection
- **Click type toggles** — press a modifier key once to toggle (no need to hold):
  - `⌃` (Control) — toggle between single click and double click
  - `⌥` (Option) — cycle through left click → right click → move cursor

All modifier-to-action mappings are configurable.

### Mouse Mode

Press `⇧⌘;` to enter **Mouse Mode** — full keyboard-driven mouse control without needing to detect UI elements first.

| Key               | Action                                   |
|-------------------|------------------------------------------|
| `h` `j` `k` `l`   | Move cursor (left, down, up, right)      |
| `Shift` + move    | Fast movement (4x speed)                 |
| `u`               | Left click (double-tap for double-click) |
| `u` + hold + move | Drag / select text                       |
| `i`               | Middle click                             |
| `o`               | Right click (hold + move to drag)        |
| `y` / `n`         | Scroll up / down                         |
| `Esc`             | Exit mouse mode                          |

A floating key legend is displayed while mouse mode is active. The hotkey is configurable.

### Configuration

Click the menu bar icon and select **Configure...** to customize:

| Setting              | Description                                                             | Default             |
|----------------------|-------------------------------------------------------------------------|---------------------|
| Activation shortcut  | Key combo to trigger hints                                              | `Ctrl+Shift+Space`  |
| Character set        | Characters used for hint labels                                         | `asdfjkl;`          |
| Distribution         | How labels are spatially assigned (Linear, Random, Hilbert, Grid, etc.) | Linear              |
| Monitor Prefixes     | First character selects a monitor, rest select within it                | On                  |
| Hint Style           | Shrink (hide typed chars) or Gray out (dim typed chars)                 | Shrink              |
| Repeat Hotkey        | Shortcut to repeat last action                                          | `⇧⌘.`               |
| History Hotkey       | Shortcut to open command history                                        | `⇧⌘,`               |
| Mouse Mode Hotkey    | Shortcut to toggle mouse mode                                           | `⇧⌘;`               |
| Single/Double toggle | Modifier to toggle between single and double click                      | `⌃` (Control)       |
| Right/Move cycle     | Modifier to cycle through left click, right click, and move cursor      | `⌥` (Option)        |
| History incl. manual | Include manual points in the history overlay                            | On                  |
| Detection Pipeline   | Basic (fast, no OCR) or Enhanced (with OCR text detection)              | Enhanced (with OCR) |
| OCR elements         | How OCR elements are displayed: Hint labels or Show detected text       | Show detected text  |

![Configuration](./assets/config.png)

### Manual Click Points

Add persistent click points via **Manage Points** in the configuration window. These are always available alongside auto-detected elements and use the last character in your character set as a prefix.

- **Drag** point markers to reposition them
- **Delete** points with the ✕ button on each marker
- Points are listed in the configuration window for easy management

## Requirements

- macOS 14 (Sonoma) or later
- Accessibility permission (for keyboard monitoring and click simulation)
- Screen Recording permission (for UI element detection)

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for release history.

## License

KayZeer is free to use. See [LICENSE](LICENSE) for details.

## Contact

- Blog: [serjster.com](https://www.serjster.com)
- GitHub Issues: [Report a bug or request a feature](https://github.com/serjster/KayZeer/issues)
