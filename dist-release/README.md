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
- Optional **Home Card Lift** mode, on by default, that rounds, clips and lifts the Home/Library cards.
- Optional **Play Caret Focus** mode, on by default, that gives the Play button's dropdown arrow a solid dark block while focused, so the two halves of the button stay distinguishable.
- Optional switch to hide friend avatars on game cards ("Hide friends playing").
- Optional switch for tabular figures, so clock, battery and download numbers stop shifting.
- Custom styling for the Main Menu, Quick Access, notifications/toasts, keyboard and settings screens.
- Selectable background (Graphite, OLED black, Aurora gradient) and footer style.
- Accent and toggle colours can be changed from CSS Loader.
- Text keeps Steam's own fonts: the theme sets no font stacks, so font plugins stay in control.

## Requirements

- A Steam client running Game Mode / Big Picture (Steam Deck, Steam Machine or a desktop Big Picture session).
- [Decky Loader](https://decky.xyz) with the **CSS Loader** plugin installed.
- No fixed Steam client version is claimed. Class names in Steam's UI change between updates, so verify the theme on your own device.

## Installation

1. Install **Decky Loader** and then the **CSS Loader** plugin from Decky's plugin store.
2. Download the release archive (`tvdeck-1.1.9.zip`) and extract it so that the folder is named `tvdeck`.
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
| Footer | Steam Default · Minimal · Hidden | Steam Default | `Minimal` applies the compact footer styling; `Hidden` additionally hides the footer. |
| Keyboard Styling | Yes · No | Yes | Applies the themed on-screen keyboard when enabled. |
| Reduce Transparency | Yes · No | No | Replaces translucent surfaces with more opaque ones. |
| Tabular Numbers | Yes · No | Yes | Gives clock, battery and download numbers equal-width digits so they stop shifting. |
| Colors | Accent Color · Toggle Color (colour pickers) | `#0A84FF` / `#30D158` | Sets the accent colour and the switch/toggle colour via CSS variables. |
| Hide friends playing | Yes · No | Yes | Hides the friend-avatar bar on portrait game cards (recent games, library grid, game details and similar). |
| Recent Games At Bottom | Yes · No | Yes | Pins the recent-games row and its labels to the bottom edge; the section background still covers the full window height. |
| Titles Above Cards | Yes · No | Yes | Hides the "Recent Games" header and moves the focused game's label (name, 2-week playtime, friends playing) above the card row; the label is anchored to the card's top edge, so no fixed offset is used. Combined with `Recent Games At Bottom` the row stays docked at the bottom and the label sits above it; the label zone above the row is reserved by padding, so the first row is not covered. With `No`, labels stay below the cards, as in vanilla Steam. |
| Home Card Lift | Yes · No | Yes | Rounds the Home/Library cards to 12px, clips the artwork so the corners are really cut, adds a top highlight and a 1px inner contour, and lifts the card with a soft shadow. With `No`, cards keep Steam's square corners. |
| Play Caret Focus | Yes · No | Yes | On the game detail page, turns the dropdown arrow segment of the "Play" button into a solid `#0e141b` block with a white triangle while it is focused, so it reads as clearly different from focusing the Play label. With `No`, the arrow segment stays on tvdeck's white focus background and is hard to tell apart from the label. |

## Differences from tvOS Deck

tvdeck is derived from [**tvOS Deck**](https://github.com/zoyekerako/tvos-deck) by **K€YOZ** (upstream version 1.1.0). The main differences in this build:

| Area | tvOS Deck (upstream) | tvdeck 1.1.9 |
| --- | --- | --- |
| Option labels | Partly Chinese (`跟随系统字体`, `隐藏好友正在游玩`) | All labels in English |
| Font control | Bundled SF Pro / Inter | No font stacks; text keeps Steam's fonts |
| Footer default | Minimal | Steam Default |
| Recent Games At Bottom | Not available | New optional bottom-docked mode |
| Titles Above Cards | Not available | New optional above-card label mode |
| Home Card Lift | Not available | New optional rounding/clipping mode, on by default |
| Play Caret Focus | Not available | New optional play-caret highlight, on by default |
| Fullscreen recent background | Optional switch | Removed |
| Tabular figures | Not available | New optional switch, on by default |
| Home layout | Tabbed content hidden via `no-home-tabs.css` | Same rule, kept intentionally |
| Friend avatar toggle | Present under a Chinese label, default Yes | Present as "Hide friends playing", default Yes |
| Label spacing | — | Extra offset between card and game label, used by the bottom-docked mode |
| Version / author | 1.1.0, K€YOZ | 1.1.9, Honchane |

The rest of the styling, including most CSS rules and token values, comes from upstream. See the licence section below.

## Known limitations

- **Recent Games At Bottom is a trade-off.** The recent-games row is fixed to the bottom of the viewport, while its background layer is stretched over the whole window. On some layouts the artwork crop or the label area may look different from the default home screen; check it on your own display.
- **Steam UI updates can break selectors.** The theme targets hashed Steam class names. A Steam client update may rename them and cause parts of the theme to stop applying until the theme is updated. No specific Steam version is guaranteed.
- **Main Menu and Quick Access are separate overlay windows.** They cannot blur the game behind them, so they use opaque glass instead of a true backdrop blur.
- **No font stacks are set.** The theme deliberately leaves typography to Steam and to font plugins such as Decky's font plugin; nothing here overrides `font-family`.
- **Unofficial theme.** It is not endorsed by Valve, Apple or the tvOS Deck maintainers.

## Credits and licence

Derived from [**tvOS Deck**](https://github.com/zoyekerako/tvos-deck) by **K€YOZ**, originally released under the MIT licence.

```
Copyright (c) 2026 tvOS Deck contributors
```

The full MIT text is in [LICENSE](LICENSE), which retains the upstream copyright notice shown above. Modifications are by **Honchane**; that modification statement is documented here, not inside `LICENSE`.

The tab-hiding rule follows [No Home Tabs by Sims](https://deckthemes.com/themes/view?themeId=1f13929d-cb5b-4ab9-985f-a69504e055fe) (v1.0, 2023). This project also drew on [Switch Like Home by Sims](https://deckthemes.com/themes/view?themeId=9ac2bf60-66c5-4f50-aa6b-f897465ba328) (v1.4, 2024) and [No Friend Playing Icon by Luna-Terra](https://deckthemes.com/themes/view?themeId=88363437-0fc3-44f7-9ae4-0ced63893aca) (2025). All three are third-party DeckThemes themes not published by this repository's author.

## Disclaimer

This is an unofficial fan project. It is not affiliated with, endorsed by or sponsored by Valve Corporation, Steam, Apple Inc. or tvOS. "Steam", "Steam Deck", "SteamOS" and "Valve" are trademarks of Valve Corporation. "Apple TV" and "tvOS" are trademarks of Apple Inc. All trademarks belong to their respective owners.
