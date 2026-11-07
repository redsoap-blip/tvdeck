# tvdeck 1.1.2 — Release Notes

Release date: 2026-11-07

tvdeck 1.1.2 is an English-language fork of [**tvOS Deck**](https://github.com/zoyekerako/tvos-deck) 1.1.0 by K€YOZ. This release does not change the theme's CSS or its options; it corrects the licence text and the documentation that ships with it.

## Changes in 1.1.2

- **Licence text matches the package.** The `LICENSE` no longer mentions the Inter font (`tvOS-Deck/fonts/InterVariable.woff2`) that was removed from the theme. It now states that no font files are bundled, that text is rendered with the system font stack (`system-ui, sans-serif`) or Steam's own stack, and that the upstream MIT licence and copyright apply.
- **Upstream attribution everywhere.** Both READMEs now state at the top and in their Credits sections that tvdeck is based on [tvOS Deck](https://github.com/zoyekerako/tvos-deck) by K€YOZ, with a working link; the same attribution is in the repository description, the packaging notes and these notes.
- **Documentation consistency.** `dist-release/LICENSE` is now byte-identical to the root `LICENSE` (the 1.1.1 draft copy had drifted), the packaging instructions use portable paths instead of a machine-specific absolute path, and every download reference points at `tvdeck-1.1.2.zip`.

## Fixes

- **Stale licence in the 1.1.1 archive.** `tvdeck-1.1.1.zip` shipped a `LICENSE` that still described the removed Inter font. The 1.1.2 archive carries the corrected licence, so the file inside the zip now matches the repository.

## Known issues

- **Recent Games At Bottom is a layout trade-off.** Because the section is fixed to the bottom while its background image still spans the window, the artwork crop and label placement may not match the default home layout on every resolution.
- **Hashed Steam class names.** Steam client updates can rename the selectors this theme relies on, which may break individual rules until the theme is updated. No specific Steam client version is guaranteed.
- **No font files are bundled.** `System font` resolves through `system-ui, sans-serif`; `Steam (Motiva Sans)` keeps Steam's own stack.
- **Main Menu and Quick Access.** These are separate overlay windows and cannot blur the game behind them; they use opaque glass.

## Upgrade notes

- Existing user configurations are stored outside the theme package in `config_USER.json`; that file is intentionally excluded from release archives and survives an upgrade.
- Replacing the folder with the 1.1.2 archive changes nothing in the rendered UI. If you are coming from 1.1.0 or earlier, re-select the `Font` option once so the system-font stack is applied.

## Credits

Derived from [tvOS Deck](https://github.com/zoyekerako/tvos-deck) by K€YOZ (MIT). Original copyright line retained; modifications by Honchane. See `LICENSE`.
