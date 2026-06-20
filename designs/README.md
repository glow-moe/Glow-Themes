# Designs (Sandbox export / import)

A **design** is your whole profile saved as one file: the colors and background
plus every widget and exactly where you placed it on the Sandbox canvas. It's the
file the Sandbox **Export** button gives you. Share it, back it up, or hand it to
a friend so they can load your exact look.

This is different from a [theme](../themes) (just colors) or a
[layout](../layouts) (which sections show): a design is **theme + widget
placement together**, the full picture.

## Export and import (in Glow)

In the dashboard, open **Style → Sandbox** (the free-form canvas), then use the
panel next to "Edit style":

- **Export** downloads `glow-design.json` and also copies it to your clipboard.
- **Import** loads a `glow-design.json` back in. Hit **Save** to apply it.

Everything is re-checked on import, so a hand-edited or shared file can never
inject anything unsafe. Bad values are clamped or dropped, never trusted as-is.

## File shape

Copy [`../example-design.json`](../example-design.json) to start.

```jsonc
{
  "glow": "glow-design",   // required tag - marks the file as a Glow design
  "version": 1,
  "profileType": "SHOWCASE",
  "layoutMode": "canvas",  // "canvas" = Sandbox, "grid" = the snapping board
  "minimal": false,
  "theme": { ... },         // your colors, background, font, glow, frame
  "canvasLayout": { ... }   // where each widget sits (desktop + mobile)
}
```

### theme

The same theme object the editor uses. Colors and the basics are the important
part (see [`../schema-theme.json`](../schema-theme.json) for the color fields):

- `accent`, `accent2`, `accent3`: hex neon colors
- `bg`: page background hex (dark works best)
- `glow`: 0 flat, 1 default, up to 1.6 intense
- `font`: `sans`, `display`, or `mono`
- `frame`: `none`, `sparkles`, `roses`, `thorns`, `blades`, or `hearts`
- `background` (optional): `{ type, color | gradient | imageUrl | videoUrl,
  dim, scrim, blur }` - `type` is `none`, `color`, `gradient`, `image`, or
  `video`. `dim`/`scrim`/`blur` darken and soften it for readability.

Some theme fields (custom cursor, audio, animated avatar ring, background
effects) only show for **Glow+** owners. They stay in the file but do nothing
without Glow+.

### canvasLayout

Two separate arrangements so phones get their own clean stack:

```jsonc
"canvasLayout": {
  "desktop": [
    { "type": "header", "x": 0, "y": 0, "w": 1000, "h": 320, "z": 1, "settings": {} }
  ],
  "mobile": [
    { "type": "header", "order": 0, "width": "full", "height": 320 }
  ]
}
```

**desktop** widgets are placed on a fixed 1600px-wide design space (it scales
down on smaller screens, never up):

- `type`: which widget (see the list below)
- `x`, `y`: top-left position in design pixels (`x` 0 to 1440, `y` 0+)
- `w`, `h`: size in pixels (`w` 160 to 1600, `h` 64 to 2400)
- `z`: stacking order, 0 to 999 (higher is on top)
- `settings` (optional): per-widget options, e.g. `{ "detail": "detailed" }`

**mobile** widgets are a single-column stack:

- `type`: same widget types
- `order`: top-to-bottom position (0 first)
- `width`: `full` or `half`
- `height`: pixels

One instance per widget type (the `type` is its id). A widget hides itself when
its data isn't connected (for example `steam` with no Steam account).

## Widgets you can place

| `type`         | What it is                                  |
| -------------- | ------------------------------------------- |
| `header`       | Profile header (avatar, name, links, badges)|
| `stats`        | Combined stats summary                      |
| `discord`      | Discord presence / now-playing              |
| `links`        | Your links                                  |
| `favorites`    | Favorite games (cover grid)                 |
| `games`        | Full game library                           |
| `characters`   | Favorite anime characters                   |
| `anime`        | Anime list                                  |
| `manga`        | Manga list                                  |
| `steam`        | Steam games + achievements                  |
| `psn`          | PlayStation games + trophies                |
| `psn-trophies` | PSN trophy case (platinum/gold/silver/bronze)|
| `retro`        | RetroAchievements                           |
| `genres`       | Genre radar                                 |
| `platforms`    | All platforms in one tabbed card            |

A widget only renders when the owner has that source connected and has data, so
it's safe to include any of them - unused ones just don't show.
