# Packaging tvdeck

This file describes how to build and check the release archive. It does not describe publishing; nothing here pushes to Git or creates a repository.

## Archive layout

The zip must contain a single top-level folder named `tvdeck`, not loose files:

```
tvdeck-1.1.9.zip
└── tvdeck/
    ├── theme.json
    ├── LICENSE
    └── css/
        ├── tokens.css
        ├── controls.css
        ├── toasts.css
        ├── shell.css
        ├── home.css
        ├── no-home-tabs.css
        ├── game.css
        ├── settings.css
        ├── mainmenu.css
        ├── qam.css
        ├── keyboard.css
        └── options/
            ├── footer-minimal.css
            ├── footer-hidden.css
            ├── friend-playing.css
            ├── recent-at-bottom.css
            ├── reduce-transparency.css
            ├── titles-above-cards.css
            ├── home-card-lift.css
            ├── play-caret-focus.css
            └── tabular-nums.css
```

`theme.json` lists every CSS file that is injected, so the archive must contain all files referenced under `inject` and `patches`. Do not rename or flatten `css/options/`.

## Repository layout (GitHub only)

```
tvdeck/
├── theme.json
├── LICENSE
├── README.md
├── README.zh-CN.md
├── screenshots/            (1920×1080 PNG, README only)
├── css/ …
└── dist-release/           (this file, release notes, the built zip)
```

`README.zh-CN.md` is the Simplified Chinese translation of `README.md` and is cross-linked from it; like `README.md` and `screenshots/`, it stays in the repository and is excluded from the zip.

## File name

`tvdeck-1.1.9.zip` — theme name plus the `version` value from `theme.json`.

## Must be included

- `theme.json` (manifest, patches, id, author, version).
- `LICENSE` carrying the upstream MIT text and copyright notice (MIT requires the licence text to travel with the distributed files). The modification statement is documented in the README, not inside `LICENSE`.
- Every file under `css/` and `css/options/` referenced by `theme.json`.
- No font assets and no `font-family` declarations: typography is left to Steam and to Decky's font plugin.

This yields exactly 22 files: `theme.json` + `LICENSE` + 20 CSS files. The archive is an install-only package for CSS Loader.

## Must be excluded

- `config_USER.json` — per-user CSS Loader settings, machine-specific.
- `README.md` — repository documentation; the zip is an install-only package.
- `README.zh-CN.md` — Simplified Chinese documentation, same rule as `README.md`.
- `screenshots/` — images for the repository README only, never in the zip.
- `dist-release/` — build notes, drafts and this file.
- Any `.git/`, `.gitignore`, `.github/` working data, editor folders (`.vscode/`, `.idea/`).
- OS clutter: `.DS_Store`, `Thumbs.db`, `desktop.ini`.
- Temporary or backup files: `*.tmp`, `*.bak`, `*~`, `*.swp`, `*.log`.
- The sibling upstream theme folder (`tvOS Deck/`) — it is a separate project and must never be bundled.
- Old archives (`*.zip`) from previous builds.

Screenshots live in `screenshots/` and are used by `README.md` in the repository; the GitHub README references them with relative paths. Neither `README.md` nor `screenshots/` goes into the zip — the archive only carries what CSS Loader needs to load the theme, so unzipping into `~/homebrew/themes/` works as-is.

## Creating the archive

Run from the parent directory of the theme, so the zip root is the folder itself:

```
cd "$HOME/homebrew/themes"      # <themes-dir>: the parent folder of tvdeck/
zip -r tvdeck-1.1.9.zip tvdeck \
  -x "tvdeck/config_USER.json" \
  -x "tvdeck/README.md" \
  -x "tvdeck/README.zh-CN.md" \
  -x "tvdeck/screenshots/*" \
  -x "tvdeck/dist-release/*" \
  -x "tvdeck/.git/*" \
  -x "tvdeck/.gitignore" \
  -x "tvdeck/.DS_Store" \
  -x "tvdeck/**/*.tmp" \
  -x "tvdeck/**/*.bak"
```

Then verify the contents before release:

```
unzip -l tvdeck-1.1.9.zip
```

The first path component of every entry must be `tvdeck/`.

## Install path and folder-name requirement

CSS Loader installs themes under `~/homebrew/themes/<folder>`. Unzipping the archive therefore yields `~/homebrew/themes/tvdeck/theme.json`.

- Keep the folder name `tvdeck`; it must match the theme's identity for CSS Loader asset URLs.
- Do not zip the contents without the wrapping folder, or CSS Loader will see a broken theme.
- Do not rename the folder after install; reinstall instead.

## Pre-release checklist (manual)

- [ ] `theme.json` parses as JSON; `name` is `tvdeck`, `version` is `1.1.9`, `manifest_version` is `9`, `author` is `Honchane`, and `id` is unchanged.
- [ ] Every path in `inject` and every patch value path exists inside the zip.
- [ ] `config_USER.json` is absent from the zip.
- [ ] Zip has a single top-level `tvdeck/` folder and no sibling theme folder.
- [ ] Fresh install into `~/homebrew/themes/tvdeck` on a real device; enable in CSS Loader.
- [ ] Check Home, Library, game details, Main Menu, Quick Access, toasts, keyboard and Settings screens.
- [ ] Toggle every option and confirm the expected CSS is applied and reverted.
- [ ] Check `Recent Games At Bottom` on the target resolution: row reachable by focus, labels not clipped, artwork acceptable.
- [ ] Check `Titles Above Cards` on and off: header hidden, label above the card, first row not covered; then check it combined with `Recent Games At Bottom` (label sits above the docked row, nothing clipped).
- [ ] Check `Hide friends playing` on and off on portrait cards.
- [ ] Confirm default options match the README table.
- [ ] Font check: `grep -rn font-family css/` returns nothing; no font file is present in the zip, so Decky's font plugin keeps control.
- [ ] `Home Card Lift` defaults to `Yes` and injects `css/options/home-card-lift.css`; with `No` the cards fall back to Steam's square corners.
- [ ] `Play Caret Focus` defaults to `Yes` and injects `css/options/play-caret-focus.css`; with `No` the Play button's dropdown arrow falls back to tvdeck's white focus background.
- [ ] `Tabular Numbers` defaults to `Yes` and injects `css/options/tabular-nums.css`; with `No` the clock, battery and download numbers keep proportional digits.
- [ ] Check against the current Steam client on the test device; do not claim a specific Steam version in the README.
- [ ] Zip holds exactly 22 files (theme.json + LICENSE + 20 CSS) and only the folders `tvdeck/`, `tvdeck/css/`, `tvdeck/css/options/`.
- [ ] Zip contains no `README.md` and no `screenshots/` entry (install-only package).
- [ ] Screenshots in the repository are current; they are referenced by the repo README only.
- [ ] Confirm the MIT licence text and the upstream copyright notice (`Copyright (c) 2026 tvOS Deck contributors`) are present in the zip.
- [ ] Confirm README credits K€YOZ and tvOS Deck, and contains the Valve/Apple disclaimer.
- [ ] Confirm no Valve, Steam, Apple or tvOS logos or trademark assets are bundled.
- [ ] Review `repo-description.txt`: first line ≤120 characters, topics lowercase and hyphenated.
