# Changelog

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
