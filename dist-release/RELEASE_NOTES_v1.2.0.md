# tvdeck 1.1.8

Covers everything since the last published build, theme `1.1.4` → `1.1.8`.

## Fonts are gone

`css/font.css` and `css/options/font-system.css` are removed, along with the
`Font` patch and the `--tvdeck-font` token. The theme now sets no font stacks at
all, so Steam keeps its own typography and font plugins (Decky's font plugin and
similar) are the single place to change it. `grep -rn font-family css/` is empty.

## New: Tabular Numbers (default Yes)

`css/options/tabular-nums.css` gives the clock, battery percentage, slider values
and the Quick Access battery label `font-variant-numeric: tabular-nums`, so the
numbers stop shifting width while they change. It only touches digit spacing, not
the font family.

## New: Home Card Lift (default Yes)

`css/options/home-card-lift.css` brings the standalone **home card lift 1.0.2**
recipe into tvdeck: 12px radius, `overflow: hidden` so the artwork is actually
clipped, a glass base behind loading artwork, a 1px top highlight, a 1px inner
contour and soft resting/focused shadows. It is driven by the existing
`--tvdeck-card-*` tokens, so it matches tvdeck's own card geometry.

Because of that, `css/home.css` no longer declares card radius, clipping, outline,
background or shadow — those live only in the new option file. `home.css` keeps
only tvdeck's own dynamics: resting transform, focus scaling and parallax. No
second place writes `border-radius` on the same container any more.

## Removed: Fullscreen Recent Games Background

`css/options/recent-bg-fullscreen.css` and its patch are gone; the switch was
redundant with `Recent Games At Bottom` and only made the artwork taller. The
leftover comments in `recent-at-bottom.css` that referenced it were removed.

## Other fixes in this build

- The Home separator line (`FeaturedSeparator`) now follows the focused wide tile
  by the same offset as the row, so the widened tile no longer uncovers it.
- The Main Menu uses a short, edge-safe shadow token
  (`--tvdeck-panel-shadow-mainmenu`) instead of the large panel shadow, which was
  being clipped against the 241px overlay window and left a visible seam.
- `css/mainmenu.css` comments now explain why `overflow: clip` does not swallow
  the menu's own shadow.
- README (both languages), `dist-release/README.md` and `PACKAGING.md` updated for
  the removed font option, the two new switches and the 21-file archive.

## Archive

`tvdeck-1.1.8.zip` — 21 files: `theme.json`, `LICENSE`, 19 CSS files
(`css/` 11, `css/options/` 8). Install-only: no README, no screenshots, no
`config_USER.json`.
