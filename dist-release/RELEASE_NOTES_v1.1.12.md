# Release Notes — v1.1.12

## Changes

### Fixed

- **FontPicker font card focus state**: focused font cards now use a `:has(.fp-font-row)` rule with a white 22px-radius background and a dark text color ramp, replacing the incorrect white ellipse that appeared when a font card was focused.
- **Unfocused card corner radius unified**: all unfocused cards now use the same 22px radius for visual consistency.

### Notes

- A 6px row spacing change was briefly introduced and then reverted in this release; the breathing-room adjustment has moved to the plugin side instead.

## Files changed

- `css/controls.css`
- `theme.json` (version bump to 1.1.12)

## Package

- `tvdeck-1.1.12.zip` — install-only package per `PACKAGING.md`: single top-level `tvdeck/` folder, 22 files (`theme.json` + `LICENSE` + 20 CSS), no README, no screenshots, no font assets.
