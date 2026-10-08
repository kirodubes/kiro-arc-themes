# Changelog

## 2026.10.08

### What Changed
- GTK4 apps no longer turn see-through or blank with an Arc theme on GTK 4.24. Since gtk4 4.24.1, an app that
  changes the theme or dark mode while running lost the whole Arc stylesheet (ATT showed text over the wallpaper,
  Font Manager an empty white window). The GTK4 part of all 220 themes now ships as plain CSS files, which GTK always
  loads. Same fix as kiro-arc-dawn the same day.

### Technical Details
- Each theme's `gtk-4.0/gtk.css` and `gtk-dark.css` were a one-line `@import` from `gtk.gresource`, which GTK 4.24.1
  does not register on a runtime reload. Converted with the generator's new `gtk4-plain-css.sh`: the imported CSS
  replaces the one-liners, the 168 images move to `gtk-4.0/assets/` (the CSS already uses relative
  `url("assets/…")`), and `gtk.gresource` is removed. GTK3 and the other theme parts are unchanged.
- Verified: no gresource or `resource://` reference left in any theme, 168 assets in each; runtime switches to
  Arc-Aqua-Dark, Arc-Blood-Darker, Arc-Botticelli and Arc-Archlinux-blue-Lighter load without parser errors, while
  the original Arc-Aqua-Dark reproduces the error.
- Size on disk grows from 435 MB to 561 MB (many small files instead of one compressed gresource per theme).

### Files Modified
- usr/share/themes/*/gtk-4.0/ (gtk.css, gtk-dark.css, assets/ added, gtk.gresource removed — all 220 themes)

## 2026.06.05

### What Changed
- Populated the data repo with the full Arc theme collection: 55 colours × 4
  tones (`base`/`-Dark`/`-Darker`/`-Lighter`) = 220 theme folders under
  `usr/share/themes/`, built from the patched arc-theme fork via
  `kiro-arc-themes-generator`.
- Moved the theme folders from the repo root into `usr/share/themes/` to match
  the `kiro-arc-dawn` layout and the path the generator's `3-make-pkgbuild.sh`
  reads.
- Removed the `Arc-Dawn*` folders — Dawn ships from its own `kiro-arc-dawn`
  repo/package and is skipped by the generator (`SKIP="dawn"`), so a copy here
  was dead data.
- Added the required markdown scaffold (`README.md`, `CHANGELOG.md`,
  `CLAUDE.md`) per the ecosystem MD-scaffold rule
  ([HQ/CLAUDE.md](/home/erik/Insync/Kiro/Kiro-HQ/CLAUDE.md#required-markdown-scaffold-every-repo)),
  plus `LICENSE` (GPL-3.0, matching upstream arc-theme) and the `kiro.jpg`
  README header image.

### Technical Details
- gtk3/gtk4 accent is set via the meson `accent` option; xfwm/unity/metacity/
  cinnamon assets are recoloured by `sed`. Themes cover Cinnamon, GTK 3/4,
  Metacity, Plank, Unity, and Xfwm4 (gtk2 / gnome-shell excluded).
- Repo holds built output only; the build source is `kiro-arc-themes-generator`.

### Files Modified
- README.md (created)
- CHANGELOG.md (created)
- CLAUDE.md (created)
- kiro.jpg (added)
- usr/share/themes/ (220 theme folders relocated here; Arc-Dawn* removed)
