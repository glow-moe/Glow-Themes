# Community layouts

Add your layout here as `your-slug.json`. Your editor will check it against
[`../schema-layout.json`](../schema-layout.json) as you go. No code, just data.
Open a pull request and a maintainer will take a look. Once it's merged it gets
added to Glow.

There are two kinds of layout.

## Section layout

Copy [`../example-layout.json`](../example-layout.json). It picks a base layout
(`SIMPLE`, `ADVANCED`, `SHOWCASE`, or `LINKS`) and arranges the sections (order,
visibility, detail).

## Grid layout (build from scratch)

Copy [`../example-grid-layout.json`](../example-grid-layout.json). Set `base` to
`GRID` and place widgets anywhere on a 12-column grid. Each widget has:

- `widget`: one of `header`, `identity`, `links`, `badges`, `stats`, `games`,
  `steam`, `psn`, `retro`, `anime`, `genres`, `discord`
- `x`: column start, 0 to 11
- `y`: row, controls order and the stacking order on phones
- `w`: column span, 1 to 12 (kept within the grid, so `x + w` stays under 12)
- `h` (optional): row span
- `detail` (optional): `compact` or `detailed`, for widgets that support it

A widget hides itself when its data isn't connected (for example `steam` with no
Steam account), and the rest flow up to fill the space. On phones everything
stacks into one column in `y` then `x` order.
