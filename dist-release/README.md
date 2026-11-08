# tvdeck

An Apple TV / tvOS-inspired look for SteamOS Game Mode — Steam Deck, Big Picture and other 16:9 setups.

tvdeck is a fan-made theme for **CSS Loader** (Decky Loader). It keeps Steam's layout and behaviour and restyles it with tvOS-like spacing, glass surfaces, focus motion and a small set of optional layout tweaks.

All CSS Loader option labels in this build are in English.

For game detail pages it pairs well with the **Clean Gameview** CSS Loader theme: Clean Gameview keeps those pages clean, while tvdeck handles the Home and Library look. The two do not conflict.

## Screenshots

![Home screen: labels above the recent-games row](screenshots/home-titles-above.png)

![Quick Access: quick settings panel](screenshots/qam-quick-settings.png)

![Game detail page](screenshots/game-detail.png)

Shots taken at 3840×2160 with default options on a 16:9 setup. They live in the repository only and are not part of the release zip.

## Features

- tvOS-style card sizing, focus scaling and parallax focus effect.
- Glass/blur styling for Game Mode surfaces, with an option to reduce transparency.
- Home screen reduced to a single Top Shelf-like row: the tabbed content area under the hero artwork is hidden (`css/no-home-tabs.css`).
- Optional **Recent Games At Bottom** mode that docks the recent-games row to the bottom edge of the screen while keeping the artwork full-bleed.
- Optional **Titles Above Cards** mode that moves the focused game's label above the card row and hides the "Recent Games" header.
- Optional switch to hide friend avatars on game cards ("Hide friends playing").
- Custom styling for the Main Menu, Quick Access, notifications/toasts, keyboard and settings screens.
- Selectable background (Graphite, OLED black, Aurora gradient), font and footer style.
- Accent and toggle colours can be changed from CSS Loader.

## Requirements

- A Steam client running Game Mode / Big Picture (Steam Deck, Steam Machine or a desktop Big Picture session).
- [Decky Loader](https://decky.xyz) with the **CSS Loader** plugin installed.
- No fixed Steam client version is claimed. Class names in Steam's UI change between updates, so verify the theme on your own device.

## Installation

1. Install **Decky Loader** and then the **CSS Loader** plugin from Decky's plugin store.
2. Download the release archive (`tvdeck-1.1.3.zip`) and extract it so that the folder is named `tvdeck`.
   The archive is an install-only package (`theme.json`, `LICENSE`, `css/`); it contains no README or screenshots.
3. Copy that folder to `~/homebrew/themes/tvdeck`.
   The final path should be `~/homebrew/themes/tvdeck/theme.json`.
4. Open Quick Access (`…`) → **CSS Loader** → **Themes** → enable **tvdeck**.
5. Optional but recommended: in Steam, open **Settings → Customization → Home** and select **Big Art Mode** for the Top Shelf-style hero layout.

Keep the extracted folder named `tvdeck`, because theme assets are served by folder name and renaming it is not supported.

## Options

| Patch name | Values | Default | Effect |
| --- | --- | --- | --- |
| Focus Effect | Apple TV (Parallax) · Subtle · Off | Apple TV (Parallax) | Controls card/focus scaling and parallax. `Subtle` reduces the scale and removes parallax; `Off` disables scaling, parallax and gloss. |
| Background | Graphite · Black (OLED) · Aurora (tvOS 26) | Graphite | `Black (OLED)` uses pure black; `Aurora` adds layered blue/green radial gradients over a near-black base. |
| Font | Steam (Motiva Sans) · System font | System font | `Steam (Motiva Sans)` keeps Steam's own font stack; `System font` uses `system-ui, sans-serif` and follows the system font settings. |
| Footer | Steam Default · Minimal · Hidden | Steam Default | `Minimal` applies the compact footer styling; `Hidden` additionally hides the footer. |
| Keyboard Styling | Yes · No | Yes | Applies the themed on-screen keyboard when enabled. |
| Reduce Transparency | Yes · No | No | Replaces translucent surfaces with more opaque ones. |
| Colors | Accent Color · Toggle Color (colour pickers) | `#0A84FF` / `#30D158` | Sets the accent colour and the switch/toggle colour via CSS variables. |
| Hide friends playing | Yes · No | Yes | Hides the friend-avatar bar on portrait game cards (recent games, library grid, game details and similar). |
| Recent Games At Bottom | Yes · No | Yes | Pins the recent-games row and its labels to the bottom edge; the section background still covers the full window height. |
| Fullscreen Recent Games Background | Yes · No | No | Lets the recent-games artwork cover the full window height when the bottom-docked mode is used. |
| Titles Above Cards | Yes · No | Yes | Hides the "Recent Games" header and moves the focused game's label (name, 2-week playtime, friends playing) above the card row; the label is anchored to the card's top edge, so no fixed offset is used. Combined with `Recent Games At Bottom` the row stays docked at the bottom and the label sits above it; the label zone above the row is reserved by padding, so the first row is not covered. With `No`, labels stay below the cards, as in vanilla Steam. |

## Differences from tvOS Deck

tvdeck is derived from [**tvOS Deck**](https://github.com/zoyekerako/tvos-deck) by **K€YOZ** (upstream version 1.1.0). The main differences in this build:

| Area | tvOS Deck (upstream) | tvdeck 1.1.3 |
| --- | --- | --- |
| Option labels | Partly Chinese (`跟随系统字体`, `隐藏好友正在游玩`) | All labels in English |
| Font default | SF Pro / Inter (bundled upstream) | System font (no font files bundled) |
| Footer default | Minimal | Steam Default |
| Recent Games At Bottom | Not available | New optional bottom-docked mode |
| Titles Above Cards | Not available | New optional above-card label mode |
| Home layout | Tabbed content hidden via `no-home-tabs.css` | Same rule, kept intentionally |
| Friend avatar toggle | Present under a Chinese label, default Yes | Present as "Hide friends playing", default Yes |
| Label spacing | — | Extra offset between card and game label, used by the bottom-docked mode |
| Version / author | 1.1.0, K€YOZ | 1.1.3, Honchane |

The rest of the styling, including most CSS rules and token values, comes from upstream. See the licence section below.

## Known limitations

- **Recent Games At Bottom is a trade-off.** The recent-games row is fixed to the bottom of the viewport, while its background layer is stretched over the whole window. On some layouts the artwork crop or the label area may look different from the default home screen; check it on your own display.
- **Steam UI updates can break selectors.** The theme targets hashed Steam class names. A Steam client update may rename them and cause parts of the theme to stop applying until the theme is updated. No specific Steam version is guaranteed.
- **Main Menu and Quick Access are separate overlay windows.** They cannot blur the game behind them, so they use opaque glass instead of a true backdrop blur.
- **No fonts are bundled.** `System font` relies on `system-ui, sans-serif`, so the rendered font is whatever the OS font stack resolves to; `Steam (Motiva Sans)` keeps Steam's own stack.
- **Unofficial theme.** It is not endorsed by Valve, Apple or the tvOS Deck maintainers.

## Credits and licence

Derived from [**tvOS Deck**](https://github.com/zoyekerako/tvos-deck) by **K€YOZ**, originally released under the MIT licence.

```
Copyright (c) 2026 tvOS Deck contributors
Modifications Copyright (c) 2026 Honchane
```

The full MIT text is in [LICENSE](LICENSE). The original copyright line is retained, and the modification notice is added above it.

The tab-hiding rule follows [No Home Tabs by Sims](https://deckthemes.com/themes/view?themeId=1f13929d-cb5b-4ab9-985f-a69504e055fe) (v1.0, 2023). This project also drew on [Switch Like Home by Sims](https://deckthemes.com/themes/view?themeId=9ac2bf60-66c5-4f50-aa6b-f897465ba328) (v1.4, 2024) and [No Friend Playing Icon by Luna-Terra](https://deckthemes.com/themes/view?themeId=88363437-0fc3-44f7-9ae4-0ced63893aca) (2025). All three are third-party DeckThemes themes not published by this repository's author.

## Disclaimer

This is an unofficial fan project. It is not affiliated with, endorsed by or sponsored by Valve Corporation, Steam, Apple Inc. or tvOS. "Steam", "Steam Deck", "SteamOS" and "Valve" are trademarks of Valve Corporation. "Apple TV" and "tvOS" are trademarks of Apple Inc. All trademarks belong to their respective owners.
