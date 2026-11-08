# tvdeck 1.1.4 — Release Notes

Release date: 2026-11-08

tvdeck 1.1.4 is an English-language fork of [**tvOS Deck**](https://github.com/zoyekerako/tvos-deck) 1.1.0 by K€YOZ. This release is a one-rule CSS fix for the top bar user avatar. It adds, removes and changes no options, and every default stays the same.

## Changes in 1.1.4

- **Top bar avatar focus capsule.** `.header_CurrentUserAvatar img` now sets `margin-right: 0`, which drops the 10 px that Steam's native layout reserves on the avatar shell for the voice-status bar and its overflow area. The item is sized by its content (32 px avatar plus 10 px padding on each side), so the capsule goes from 62 px to 52 px and is symmetric again, matching the globe and clock capsules on the same bar. The voice-status bar and the online dot still sit 5 px outside the avatar's bottom-right corner and are not clipped.

The other two CSS changes from the same working pass — the gamepad context-menu corner-shadow layer with its title gap and panel padding, and the Main Menu and Quick Access layout fixes — shipped in 1.1.3 and are not repeated here.

## Known issues

- **Recent Games At Bottom is a layout trade-off.** Because the section is fixed to the bottom while its background image still spans the window, the artwork crop and label placement may not match the default home layout on every resolution.
- **Hashed Steam class names.** Steam client updates can rename the selectors this theme relies on, which may break individual rules until the theme is updated. No specific Steam client version is guaranteed.
- **No font files are bundled.** `System font` resolves through `system-ui, sans-serif`; `Steam (Motiva Sans)` keeps Steam's own stack.
- **Main Menu and Quick Access.** These are separate overlay windows and cannot blur the game behind them; they use opaque glass.

## Upgrade notes

- Existing user configurations are stored outside the theme package in `config_USER.json`; that file is intentionally excluded from release archives and survives an upgrade.
- Replacing the folder with the 1.1.4 archive keeps all options and defaults unchanged. If you are coming from 1.1.0 or earlier, re-select the `Font` option once so the system-font stack is applied.

## Credits

Derived from [tvOS Deck](https://github.com/zoyekerako/tvos-deck) by K€YOZ (MIT). Original copyright line retained; modifications by Honchane. See `LICENSE`.

The tab-hiding rule follows [No Home Tabs by Sims](https://deckthemes.com/themes/view?themeId=1f13929d-cb5b-4ab9-985f-a69504e055fe) (v1.0, 2023). This project also drew on [Switch Like Home by Sims](https://deckthemes.com/themes/view?themeId=9ac2bf60-66c5-4f50-aa6b-f897465ba328) (v1.4, 2024) and [No Friend Playing Icon by Luna-Terra](https://deckthemes.com/themes/view?themeId=88363437-0fc3-44f7-9ae4-0ced63893aca) (2025). All three are third-party DeckThemes themes not published by this repository's author.
