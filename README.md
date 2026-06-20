# Glow Community

Community made themes for [Glow](https://glow.moe) profiles, plus the Sandbox
design format. Everything here is plain data (JSON), no code, so anyone can add
one with a pull request.

This repo only holds the contribution files. None of the Glow app code lives here.

## What's in here

```
example-theme.json     copy this to make a theme
example-design.json    a full design exported from the Sandbox
themes/                community themes go here  (your-slug.json)
designs/               how Sandbox export / import works + the widget list
schema-theme.json      validates theme files
```

## Two things you can use

1. **Themes.** A small JSON file with colors, a glow level, a font, and an
   optional corner frame. You make one and open a pull request, and once it's
   merged everyone can pick it in Glow.
2. **Designs.** A whole profile saved to one file straight from the Sandbox: the
   colors and background plus every widget and where you placed it. You export it
   from your own profile and import it back, or share it. See
   [`designs/README.md`](designs/README.md).

## How to make a theme

1. Copy `example-theme.json` into `themes/your-slug.json`. Pick a short
   lowercase-with-dashes slug, and use that same slug as the file name.
2. Fill in the fields (see below). Keep the `$schema` line at the top so your
   editor checks your file as you type.
3. Open a pull request. A maintainer looks it over, and once it's merged the
   theme shows up in Glow for everyone.

### Theme fields

A theme is colors, a glow level, a font, and an optional corner frame.

| Field | What it is |
| --- | --- |
| `name` (required) | 3 to 40 characters |
| `slug` (required) | lowercase with dashes, unique, one file per slug |
| `description` | up to 200 characters |
| `tags` | up to 6, each up to 20 characters |
| `theme.accent`, `theme.accent2`, `theme.accent3` (required) | hex colors like `#ff66b3` |
| `theme.bg` (required) | page background hex, dark works best |
| `theme.glow` | 0 is flat, 1 is default, 1.6 is intense |
| `theme.font` | `sans`, `display`, or `mono` |
| `theme.frame` | `none`, `sparkles`, `roses`, `thorns`, `blades`, or `hearts` |

## How to use a design

A design is your whole profile in one file. In Glow, open the dashboard, go to
**Style**, pick **Sandbox**, then use the panel next to "Edit style":

1. **Export** downloads `glow-design.json` and copies it to your clipboard.
2. **Import** loads a `glow-design.json` back in. Hit **Save** to apply it.

Full details (the file shape, the theme block, the widget list, and the canvas
coordinates) are in [`designs/README.md`](designs/README.md). Start from
[`example-design.json`](example-design.json).

Thanks for making Glow prettier.
