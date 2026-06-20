# Glow Community

Community made themes and layouts for [Glow](https://glow.moe) profiles. It's all
plain data, no code, so anyone can add one with a pull request.

This repo only holds the contribution files. None of the Glow app code lives here.

## What's in here

```
example-theme.json     copy this to make a theme
example-layout.json    copy this to make a layout
example-design.json    a full design exported from the Sandbox
themes/                community themes go here  (your-slug.json)
layouts/               community layouts go here (your-slug.json)
designs/               how Sandbox export / import works + the widget list
schema-theme.json      validates theme files
schema-layout.json     validates layout files
```

## How to add one

1. Copy `example-theme.json` into `themes/your-slug.json`, or `example-layout.json`
   into `layouts/your-slug.json`.
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

## Layout fields

A layout picks a base layout and arranges the sections.

- `name`, `slug`, `description`, `tags`: same rules as themes (name and slug required)
- `layout.base` (required): `SIMPLE`, `ADVANCED`, `SHOWCASE`, or `LINKS`
- `layout.sections`: a list, each with `key`, `visible`, `detailLevel`
  (`compact` or `detailed`), and `order`
- section `key` can be: `stats`, `games`, `steam`, `psn`, `retro`, `anime`,
  `music`, `lol`, `valorant`, `minecraft`, `genres`, `discord`

## Designs (Sandbox export / import)

A design is your **whole profile in one file** - the colors and background plus
every widget and exactly where you placed it on the Sandbox canvas. It's what the
Sandbox **Export** button gives you, and **Import** loads back. Use it to back up
or share your exact look.

See [`designs/README.md`](designs/README.md) for how export / import works, the
file shape, and the full list of widgets you can place. Start from
[`example-design.json`](example-design.json).

Thanks for making Glow prettier.
