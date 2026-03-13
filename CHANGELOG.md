# Changelog

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
