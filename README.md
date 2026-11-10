# tvdeck

Apple TV / tvOS look for SteamOS Game Mode – Steam Machine (16:9, 4K), Steam Deck and Big Picture.
A theme for CSS Loader (Decky Loader).

Based on [**tvOS Deck**](https://github.com/zoyekerako/tvos-deck) by **K€YOZ** (MIT).

[简体中文说明](README.zh-CN.md)

## Screenshots

![Home screen: labels above the recent-games row](screenshots/home-titles-above.png)
![Quick Access: quick settings panel](screenshots/qam-quick-settings.png)
![Game detail page](screenshots/game-detail.png)

## Install

[Decky Loader](https://decky.xyz) with the **CSS Loader** plugin is required either way.

### From the latest release (recommended)

1. Download the theme archive from the [latest release](../../releases/latest).
2. Extract it and copy the resulting folder to `~/homebrew/themes/tvdeck`, so that the theme manifest ends up at `~/homebrew/themes/tvdeck/theme.json`.
3. Quick Access (…) → CSS Loader → enable **tvdeck**.
4. Recommended: Steam *Settings → Customization → Home → Big Art Mode* for the Apple TV Top Shelf layout.

### Manually

1. Copy this folder to `~/homebrew/themes/tvdeck`.
2. Quick Access (…) → CSS Loader → enable **tvdeck**.
3. Recommended: Steam *Settings → Customization → Home → Big Art Mode* for the Apple TV Top Shelf layout.

The folder name must stay `tvdeck`: CSS Loader serves theme files by folder name. The release archive already unpacks to a folder with that name.

## Options

| Option | Values | Default |
| --- | --- | --- |
| Focus Effect | Apple TV (Parallax) · Subtle · Off | Apple TV (Parallax) |
| Background | Graphite · Black (OLED) · Aurora (tvOS 26) | Graphite |
| Footer | Steam Default · Minimal · Hidden | Steam Default |
| Keyboard Styling | Yes · No | Yes |
| Reduce Transparency | Yes · No | No |
| Tabular Numbers | Yes · No | Yes |
| Colors | Accent color, toggle color | `#0A84FF` / `#30D158` |
| Hide friends playing | Yes · No | Yes |
| Recent Games At Bottom | Yes · No | Yes |
| Titles Above Cards | Yes · No | Yes |

## Notes

- `Titles Above Cards` moves the focused game's label above the recent-games row and hides the "Recent Games" header;
  with `Recent Games At Bottom` the row stays docked at the bottom and the label follows it upwards.
- The Steam menu and Quick Access are separate overlay windows and cannot blur the game behind them, so they use
  opaque glass.
- The theme sets no font stacks; text keeps Steam's own fonts so font plugins stay in control.
- Unofficial fan theme, not affiliated with Apple or Valve.

## Credits

tvdeck is derived from [**tvOS Deck**](https://github.com/zoyekerako/tvos-deck) by **K€YOZ** (upstream version 1.1.0, MIT licence). The original
copyright line is retained in [LICENSE](LICENSE); modifications are by Honchane.

The tab-hiding rule follows [No Home Tabs by Sims](https://deckthemes.com/themes/view?themeId=1f13929d-cb5b-4ab9-985f-a69504e055fe) (v1.0, 2023).
This project also drew on [Switch Like Home by Sims](https://deckthemes.com/themes/view?themeId=9ac2bf60-66c5-4f50-aa6b-f897465ba328) (v1.4, 2024)
and [No Friend Playing Icon by Luna-Terra](https://deckthemes.com/themes/view?themeId=88363437-0fc3-44f7-9ae4-0ced63893aca) (2025).
All three are third-party DeckThemes themes not published by this repository's author.

## Deutsch

Ordner nach `~/homebrew/themes/tvdeck` kopieren, in CSS Loader einschalten und in Steam
*Einstellungen → Anpassung → Startseite → „Große Grafik“* aktivieren.
