# Glow Community

Community made themes for [Glow](https://glow.moe) profiles, plus the Sandbox
design format. It's all plain data, no code, so anyone can add one with a pull
request.

This repo only holds the contribution files. None of the Glow app code lives here.

## What's in here

```
example-theme.json     copy this to make a theme
example-design.json    a full design exported from the Sandbox
themes/                community themes go here  (your-slug.json)
designs/               how Sandbox export / import works + the widget list
schema-theme.json      validates theme files
```

## How to add one

1. Copy `example-theme.json` into `themes/your-slug.json`.
2. Edit the fields. Keep the `$schema` line so your editor checks it while you type.
3. Open a pull request. A maintainer looks it over, and once it's merged it gets
   added to Glow.

## Theme fields

A theme is just colors, a glow level, a font, and an optional corner frame.

- `name` (required): 3 to 40 characters
- `slug` (required): lowercase-with-dashes, unique, one file per slug
- `description`: up to 200 characters
- `tags`: up to 6, each up to 20 characters
- `theme.accent`, `theme.accent2`, `theme.accent3` (required): hex colors like `#ff66b3`
- `theme.bg` (required): page background hex, dark works best
- `theme.glow`: 0 is flat, 1.6 is intense, default is 1
- `theme.font`: `sans`, `display`, or `mono`
- `theme.frame`: `none`, `sparkles`, `roses`, `thorns`, `blades`, or `hearts`

## Designs (Sandbox export / import)

A design is your **whole profile in one file** - the colors and background plus
every widget and exactly where you placed it on the Sandbox canvas. It's what the
Sandbox **Export** button gives you, and **Import** loads back. Use it to back up
or share your exact look.

See [`designs/README.md`](designs/README.md) for how export / import works, the
file shape, and the full list of widgets you can place. Start from
[`example-design.json`](example-design.json).

Thanks for making Glow prettier.
