# Designs (Sandbox export / import)

A **design** is your whole profile saved as one file: the colors and background
plus every widget and exactly where you placed it on the Sandbox canvas. It's the
file the Sandbox **Export** button gives you. Share it, back it up, or hand it to
a friend so they can load your exact look.

This is different from a [theme](../themes), which is just the colors: a design
is the **theme plus your widget placement**, the full picture.

## Export and import (in Glow)

In the dashboard, open **Style → Sandbox** (the free-form canvas), then use the
panel next to "Edit style":

- **Export** downloads `glow-design.json` and also copies it to your clipboard.
- **Import** loads a `glow-design.json` back in. Hit **Save** to apply it.

Everything is re-checked on import, so a hand-edited or shared file can never
inject anything unsafe. Bad values are clamped or dropped, never trusted as-is.

## File shape

Copy [`../example-design.json`](../example-design.json) for a minimal start, or
grab a fuller ready-made design to drop in and tweak:
[`sakura.json`](sakura.json) (soft sakura theme, glowing shapes, neon boxes) or
[`sunset.json`](sunset.json) (sunset gradient, tilted headings and divider lines).

```jsonc
{
  "glow": "glow-design",   // required tag, marks the file as a Glow design
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
  dim, scrim, blur }`. `type` is `none`, `color`, `gradient`, `image`, or
  `video`. `dim`, `scrim` and `blur` darken and soften it for readability.

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

One widget of each type at most. Free **elements** (text, image, shape) can be
added as many times as you like. A widget hides itself when its data isn't
connected (for example `steam` with no Steam account).

## Free elements (text, image, shape)

Besides the data widgets you can drop in your own pieces. Each is a canvas item
just like a widget, with its own `settings`:

- **Text** (`"type": "text"`): `text`, `color`, `size` (10 to 160), `font`
  (`display`, `sans`, `mono`, `serif`, `rounded`, `script`), `align`, `weight`,
  `italic`, `lineHeight`, `letterSpacing`, `shadow`, `stroke` plus `strokeColor`.
- **Image** (`"type": "image"`): `url` (your upload), `fit` (`cover` or
  `contain`), `radius`, `opacity`.
- **Shape** (`"type": "shape"`): `shape` (`rect`, `circle`, `line`), `color`,
  `gradient` plus `color2`, `radius`, `opacity`.

Any element can also carry a `link` (a URL or `/name`) to make it clickable on
the public profile.

In a hand-edited file give each element a unique type suffix, like
`"type": "text:a1"`, so two text blocks do not collide.

## Styling any item (box, rotation, animation)

Every item, widget or element, can carry these in its `settings`:

- `_rot`: rotation in degrees, from -180 to 180.
- `_anim`: a looping animation, one of `float`, `pulse`, `fade`, `spin` (leave it
  out for none). Turned off automatically for reduced-motion visitors.
- `_box`: an optional panel behind the item,
  `{ bg, bgOpacity, gradient, bg2, border, borderWidth, radius, blur, pad,
  shadow, glow }`. `bg`, `bg2`, `border` and `glow` are hex colors, the rest are
  numbers. `glow` adds a neon halo, `shadow` a soft drop shadow, `blur` a glass
  backdrop.

## Widgets you can place

The full list of widgets, what each one shows, and its limits (item counts,
scrolling, what it needs connected) is in [`widgets.md`](widgets.md).

In short: `header`, `links`, `stats`, `genres`, `discord`, `favorites`, `games`,
`steam`, `psn`, `psn-trophies`, `xbox`, `retro`, `minecraft`, `characters`,
`anime`, `manga`, `letterboxd`, `platforms`. A widget only renders when its data
is connected, so any of them is safe to include. Unused ones stay hidden.
