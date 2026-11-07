# tvdeck 1.1.1 — Release Notes

Release date: 2026-11-07

tvdeck 1.1.1 is an English-language fork of **tvOS Deck** 1.1.0 by K€YOZ. It keeps the upstream visual design and adds a few layout and default changes.

## Changes in 1.1.1

- **English option labels.** All CSS Loader patch names and values are now in English, including the system-font and friend-avatar switches.
- **System font by default.** The `Font` patch now defaults to `System font` (`system-ui, sans-serif`). `Steam (Motiva Sans)` remains selectable; no font files are bundled.
- **Steam Default footer by default.** The `Footer` patch now defaults to `Steam Default`; `Minimal` and `Hidden` are unchanged.
- **New Recent Games At Bottom option.** When enabled, the recent-games row and its labels are docked to the bottom edge while the artwork background remains full-height. Default: `Yes`.
- **New Titles Above Cards option.** Moves the focused game's label above the card row and hides the "Recent Games" header. Works together with `Recent Games At Bottom` (label follows the docked row; the label zone is reserved by padding). Default: `Yes`.
- **Hide friends playing toggle.** Hides the friend-avatar bar on portrait game cards. Default: `Yes`. (The same toggle exists upstream under a Chinese label.)
- **Single-row home screen.** The tabbed content area below the hero artwork is hidden via `css/no-home-tabs.css`, as in upstream.
- **Label spacing adjustment.** Added an extra vertical offset between recent-game cards and their labels to support the bottom-docked mode.
- **Quick Access page title.** The title keeps tvdeck's typography but no longer paints a background or halo; the left padding is back at Steam's native `16px`, so the row's left/right insets are symmetric (`16/16`) and the back button keeps its native ~40px width.
- **Decky pages in Quick Access.** Decky renders its own title inside Steam's scroll container. tvdeck now restyles that container only on Decky's tab (`#quickaccess_content_999`) into a flex column, so the title stays fixed at the top and the list scrolls below it — the same layout native Steam tabs already have.

## Fixes

- No functional bugs from upstream were specifically targeted in this release. The changes above are additions and default changes.

## Known issues

- **Recent Games At Bottom is a layout trade-off.** Because the section is fixed to the bottom while its background image still spans the window, the artwork crop and label placement may not match the default home layout on every resolution.
- **Hashed Steam class names.** Steam client updates can rename the selectors this theme relies on, which may break individual rules until the theme is updated. No specific Steam client version is guaranteed.
- **Quick Access title background.** On native tabs the transparent title layer is harmless, but Decky draws its title inside Steam's scroll area; the theme compensates with the flex layout only on `#quickaccess_content_999`. If Decky changes its markup or tab id, the Decky title falls back to Steam's native layout.
- **No font files are bundled.** `System font` resolves through `system-ui, sans-serif`; `Steam (Motiva Sans)` keeps Steam's own stack.
- **Main Menu and Quick Access.** These are separate overlay windows and cannot blur the game behind them; they use opaque glass.
- Screenshots are not included in this release package. Add them to the repository separately.

## Upgrade notes

- Existing user configurations are stored outside the theme package in `config_USER.json`. That file is intentionally excluded from release archives.
- The `Font` patch no longer references a bundled font: `System font` injects `css/font.css` + `css/options/font-system.css`, `Steam (Motiva Sans)` injects nothing. Re-select the option once after upgrading if the UI still shows an old font.

## Credits

Derived from tvOS Deck by K€YOZ (MIT). Original copyright line retained; modifications by Honchane. See `LICENSE`.
