# Zen OLED Accents

A pure-black theme for [Zen Browser](https://zen-browser.app) where **each space's color shows up in small doses**, so you always know which space you're in without giving up OLED-friendly black.

- **Pure `#000` everywhere** — sidebar, toolbars, panels, window background. Zen's space gradient is blacked out too, including the crossfade when switching spaces (no flash of the previous space's color).
- **Space color, sparingly:**
  - URL bar tinted with the space color (stronger + accent border when focused),
  - space name in the sidebar header: larger, bold, in the space color with a soft glow,
  - active space icon in the switcher: same color and glow,
  - active tab: subtle tint; hovered tabs: the faintest tint,
  - pinned/normal divider: a solid accent line,
  - Essentials: hairline accent rings,
  - toolbar button hover: subtle tint.
- **Flat and minimal** — no gradient lines, rings around the page or accent bars.
- Works with [Zen Tree Tabs](https://github.com/tworekj/zen-tree-tabs): its indent guides take the space color.

All accents derive from Zen's `--zen-primary-color`, so switching spaces recolors everything at once.

## Install

1. Make sure userChrome styling is enabled: in `about:config`, `toolkit.legacyUserProfileCustomizations.stylesheets` = `true`.
2. Find your profile folder: `about:support` → **Profile Folder** → *Open Folder*. Create a `chrome` folder in it if there isn't one.
3. Put `zen-oled-accents.css` into `chrome/`, then either
   - **no existing `userChrome.css`:** create `chrome/userChrome.css` containing
     ```css
     @import "zen-oled-accents.css";
     ```
   - **existing `userChrome.css`:** add that same `@import` line as the **very first line** (CSS ignores `@import` anywhere else).
4. Restart Zen.

Or clone the repo and symlink the file into `chrome/` to get updates with `git pull`.

## Tips for the space colors

The theme only uses each space's color as an accent, so the colors you pick in Zen's space theme picker are what you'll see:

- **Keep them similar in lightness and saturation** — the accents look like one coherent scheme instead of one space shouting and another whispering. Mid-lightness, moderately saturated colors (e.g. `#e28d4f`, `#62bb78`, `#6aa7f4`, `#b191ea`) work well on black.
- **A neutral space** works nicely as a light grey (e.g. `#c4c4c4`).
- **Keep the space opacity at about 50% or lower.** With bright colors at high opacity Zen switches that space to light mode and alters the accent (and may darken toolbar text).
- With **dark** toolbar theme (`browser.theme.toolbar-theme` = `0`) Zen uses the space color as-is for the accent.

## Customizing

The accent strengths are variables at the top of the *Space accents* section:

| Variable | Used for | Default |
|---|---|---|
| `--oled-accent-text` | space name, active space icon | 60% accent + white |
| `--oled-accent-fill` | tab hover tint | 14% accent on black |
| `--oled-accent-line` | divider, glow | 55% accent |
| `--oled-accent-faint` | Essentials rings, name glow | 22% accent |

The URL bar and active-tab tints are in their own blocks above.

## Compatibility

Made for Zen **1.22.3b** (Firefox 156 base) on Linux. It targets Zen's internal element names and variables, so a Zen update can change things; open an issue if something breaks.

## License

[MIT](LICENSE)
