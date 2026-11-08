# tvdeck 1.1.3 — Release Notes

Release date: 2026-11-08

tvdeck 1.1.3 is an English-language fork of [**tvOS Deck**](https://github.com/zoyekerako/tvos-deck) 1.1.0 by K€YOZ. This release is a CSS fix pass for the gamepad context menu, the in-game Main Menu and Quick Access. It adds, removes and changes no options, and every default stays the same.

## Changes in 1.1.3

- **Gamepad context menu shadow and spacing.** The exterior shadow no longer sits on the panel itself: a dedicated `::before` layer on the container carries it, while the panel keeps only the inset glass highlight. This removes the hard-edged dark blocks that appeared inside the rounded corners. The title now has an 18 px gap above the panel, and the panel padding grows from 10 px to 18 px, so the focused capsule no longer nearly touches the rounded edge.
- **In-game Main Menu width and running-game row.** The placeholder and the menu now share one width variable, so the menu stays 20 px inside the 240 px slot and its right edge is no longer clipped. The row container is left-aligned (`flex-start`), row height grows with its content instead of being fixed at 46 px, and long names are truncated with an ellipsis. The collapsed running-game row becomes a 34×34 rounded container with a symmetric transition in both states, and the icon wrapper is transparent so the dark corner notches are gone.
- **Quick Access top and bottom inset via layout.** The 8 px top and bottom inset is now produced by `height` and `margin`; `clip-path` keeps only the left and right cut. The content box therefore matches the visible card again, so the clock header, the Decky list and the "A Select" bar are no longer clipped. Decky pages keep their flex layout.

## Fixes

- **Dark rectangles in the gamepad context menu corners.** Caused by the exterior shadow being drawn on the rounded panel; it now lives on a separate layer behind the panel.
- **Clipped Quick Access header and footer.** Caused by the visible card being 8 px shorter than its content box; the inset is now part of the layout instead of a visual crop.
- **Running-game icon jump and clipped row background.** Caused by the centred row growing faster than its item while the background filled the whole shifted row; the row is now left-aligned, the icon wrapper is transparent, and the collapsed state uses a bounded 34×34 tile.

## Known issues

- **Recent Games At Bottom is a layout trade-off.** Because the section is fixed to the bottom while its background image still spans the window, the artwork crop and label placement may not match the default home layout on every resolution.
- **Hashed Steam class names.** Steam client updates can rename the selectors this theme relies on, which may break individual rules until the theme is updated. No specific Steam client version is guaranteed.
- **No font files are bundled.** `System font` resolves through `system-ui, sans-serif`; `Steam (Motiva Sans)` keeps Steam's own stack.
- **Main Menu and Quick Access.** These are separate overlay windows and cannot blur the game behind them; they use opaque glass.

## Upgrade notes

- Existing user configurations are stored outside the theme package in `config_USER.json`; that file is intentionally excluded from release archives and survives an upgrade.
- Replacing the folder with the 1.1.3 archive keeps all options and defaults unchanged. If you are coming from 1.1.0 or earlier, re-select the `Font` option once so the system-font stack is applied.

## Credits

Derived from [tvOS Deck](https://github.com/zoyekerako/tvos-deck) by K€YOZ (MIT). Original copyright line retained; modifications by Honchane. See `LICENSE`.

The tab-hiding rule follows [No Home Tabs by Sims](https://deckthemes.com/themes/view?themeId=1f13929d-cb5b-4ab9-985f-a69504e055fe) (v1.0, 2023). This project also drew on [Switch Like Home by Sims](https://deckthemes.com/themes/view?themeId=9ac2bf60-66c5-4f50-aa6b-f897465ba328) (v1.4, 2024) and [No Friend Playing Icon by Luna-Terra](https://deckthemes.com/themes/view?themeId=88363437-0fc3-44f7-9ae4-0ced63893aca) (2025). All three are third-party DeckThemes themes not published by this repository's author.
