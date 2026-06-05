<p align="center">
  <img src="kiro.jpg" alt="Kiro" width="220" />
</p>

# kiro-arc-themes

The full **Arc** GTK theme collection — **55 colours**, each in **4 tones**
(`base`, `-Dark`, `-Darker`, `-Lighter`) for **220 ready-to-use themes**. Built
from source from a patched [Arc theme](https://github.com/horst3180/arc-theme)
fork, packaged for easy installation on Arch / Kiro.

The single-colour **Arc Dawn** family lives in its own repo
([kiro-arc-dawn](https://github.com/kirodubes/kiro-arc-dawn)) and is intentionally
not duplicated here.

## What's in this repo

The 220 theme folders ship under `usr/share/themes/`. Each colour comes in four
tones:

| Tone        | Window chrome | Use when                          |
|-------------|---------------|-----------------------------------|
| *(base)*    | Light         | Daytime use, bright workspaces    |
| `-Dark`     | Dark chrome, light app body | Mixed-mode preference |
| `-Darker`   | Fully dark    | Low-light / OLED setups           |
| `-Lighter`  | Extra-light   | Maximum brightness                |

Every variant covers **Cinnamon, GTK 3, GTK 4, Metacity, Plank, Unity, and
Xfwm4**.

The 55 colours: Aqua, Archlinux-blue, Arcolinux-blue, Azul, Azure,
Azure-dodger-blue, Blood, Blueberry, Blue-sky, Botticelli, Bright-lilac,
Carnation, Carolina-blue, Casablanca, Cornflower-blue, Crimson, Darkish,
Dodger-blue, Dracul, Emerald, Evopop, Fern, Fire, Froly, Havelock, Hibiscus,
Light-blue-grey, Light-blue-surfn, Light-salmon, Mandy, Mantis, Medium-blue,
Niagara, Nice-blue, Numix, Orchid, Pale-grey, Paper, Pink, Polo, Punch, Purpley,
Red-orange, Red-violet, Rusty-orange, Sky-blue, Slate-grey, Smoke, Soft-blue,
Tacao, Tangerine, Tory, Twilight, Vampire, Warm-pink.

## Installation

### From `nemesis_repo` (recommended)

```ini
[nemesis_repo]
SigLevel = Never
Server = https://erikdubois.github.io/$repo/$arch
```

Each colour is its own package, named `kiro-arc-<colour>` (lowercase). List them
all and install the ones you want:

```bash
sudo pacman -Syu
pacman -Ss kiro-arc            # list every colour package
sudo pacman -S kiro-arc-crimson kiro-arc-emerald   # install a few
```

Each package installs its four tone folders under `/usr/share/themes/`, which
become selectable in any GTK-based theme switcher.

### Manual

```bash
git clone https://github.com/kirodubes/kiro-arc-themes.git
cd kiro-arc-themes
sudo cp -r usr/share/themes/. /usr/share/themes/
```

### Activate

GTK 3 / 4:

```bash
gsettings set org.gnome.desktop.interface gtk-theme "Arc-Crimson-Dark"
```

Or set via your DE's theme settings (Tweaks, XFCE Settings → Appearance, etc.).

## How these are built

The themes are generated from source by
[kiro-arc-themes-generator](https://github.com/kirodubes/kiro-arc-themes-generator),
which passes each colour's accent through the meson `accent` option (gtk3/gtk4)
and recolours the xfwm/unity/metacity/cinnamon assets. This repo holds the
**built output** only.

## Websites

Information : https://kiroproject.be

## Social Media

Youtube : https://www.youtube.com/erikdubois

<!-- KIRO-FUNDING-FOOTER:START — managed by Kiro-HQ/cascade-readme-footer.sh -->
## Help fund Kiro

Everything I build here stays free and open — always. If Kiro or any of these
tools have ever saved you time or taught you something, a small monthly
contribution helps keep the work going. Donations target break-even, nothing
more — the core always stays free for everyone.

- GitHub Sponsors: https://github.com/sponsors/erikdubois
- Patreon: https://www.patreon.com/c/kiroproject
- YouTube memberships: https://www.youtube.com/@ErikDubois/join
- Ko-fi: https://ko-fi.com/erikdubois
- PayPal: https://www.paypal.me/erikdubois
<!-- KIRO-FUNDING-FOOTER:END -->

## License

See [LICENSE](./LICENSE).
