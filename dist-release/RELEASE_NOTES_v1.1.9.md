# tvdeck 1.1.9

Covers the change since the last published build, theme `1.1.8` → `1.1.9`.

## New: Play Caret Focus (default Yes)

`css/options/play-caret-focus.css` fixes the game detail page's "Play" button,
where the dropdown-arrow segment was impossible to tell apart from the label when
focused.

The cause is tvdeck's own focus styling: `css/game.css` paints the whole capsule
and both button segments `#fff` with a dark foreground, so focusing the arrow
segment produced white-on-white, and the native `::after` sheen is already
disabled by `display: none !important`. The only remaining cue was the 12px glyph
itself.

The new option turns the focused arrow segment into a solid `#0e141b` block with a
white triangle — the only solid dark block on the white capsule — while the label
segment keeps tvdeck's white block with dark text. The two focus targets are now
unmistakable.

Details worth keeping in mind:

- **The colour is hard-coded `#0e141b`, not `var(--tvdeck-tint)`.** tvdeck's tint
  defaults to blue (`#0a84ff`), so following it would produce a blue block and
  change the look. `#0e141b` is also the colour Steam's native focused arrow uses.
- **The file keeps exactly two `!important` declarations.** They are not
  redundant: `css/game.css` lines 76–84 set `background` and `color` with
  `!important`, so a normal declaration would never win. Removing them disables
  the option.
- The right-end rounding is not declared here: the capsule's
  `border-radius: var(--tvdeck-r-pill)` plus `overflow: hidden` already clip the
  block into a rounded right edge.

`No` injects nothing and leaves Steam/tvdeck's original arrow focus appearance.

This replaces the standalone `tvdeck-play-caret-accent` test theme; the recipe is
now part of tvdeck and on by default, so enabling tvdeck alone gives the same
result as that theme used to.

## Archive

`tvdeck-1.1.9.zip` — 22 files: `theme.json`, `LICENSE`, 20 CSS files
(`css/` 11, `css/options/` 9). Install-only: no README, no screenshots, no
`config_USER.json`.

## Docs

- `README.md` / `README.zh-CN.md`: option tables now list `Play Caret Focus`
  (and the previously missing `Home Card Lift` row).
- `dist-release/README.md`: new feature bullet, options-table row, differences
  row and version bumped to `1.1.9`.
- `dist-release/PACKAGING.md`: archive tree, zip name, 22-file count and a
  pre-release check for the new option.
