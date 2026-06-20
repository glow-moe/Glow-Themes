# Widget reference

Every widget you can place on the Sandbox canvas, what it shows, and its limits.
A widget only appears when the owner has its data connected, so it is safe to
place any of them. Unused ones just stay hidden.

Each one is referenced by its `type` (the string you use in a `glow-design.json`).

## Profile and links

### `header`

- Shows the profile card: avatar, name, username, pronouns, location, bio, badges,
  and connection chips (Steam, PSN, MyAnimeList, AniList). An optional stats row
  shows playtime, trophies, games and completion.
- Limits: the bio is clamped to two lines. The stats row always shows four metrics.
- Needs: just the profile. Connections fill in the stats and chips.
- Size: full width works best. The avatar and stat grid scale down on phones.

### `links`

- Shows your links and socials as pills, each with the real platform logo.
- Limits: no cap. Every link shows and the row wraps onto more lines. No scroll.
- Needs: at least one link on your profile.
- Size: flexible. Pills size to their text, so a wider box fits more per row.

## Stats and summaries

### `stats`

- A compact grid of headline numbers: games, completed, playtime, achievements or
  trophies, anime or episodes.
- Limits: up to six cards depending on what you have connected. No scroll.
- Needs: at least one of Steam, PSN, MyAnimeList, or AniList.
- Size: 2 columns on phones, 3 on desktop.

### `genres`

- A radar (spider) chart of your most played genres.
- Limits: needs at least three genres or it stays hidden. All genres in your data
  appear on the chart.
- Needs: a game library with genre data (Steam or PSN).
- Size: the chart caps around 300px wide and centers, so a square-ish box suits it.

### `discord`

- Your Discord avatar, status, and custom status. In detailed mode it also shows
  what you are playing or listening to, with the activity art.
- Limits: one activity at a time. Compact mode hides the activity card.
- Needs: Discord connected.
- Size: a small card. It grows taller when an activity is showing.

## Games

### `favorites` (Favorite games)

- A grid of game cover art.
- Limits: 3 to 9 covers, default 6 (set it in the widget's own settings). Favorites
  come first, then recent. No scroll, every cover shows.
- Needs: games from a connected Steam or PSN account.
- Size: a 3 column grid.

### `games` (Game library)

- A grid of game cards with cover, name, playtime and completion.
- Limits: compact mode shows the first 6, detailed mode the first 24. No scroll or
  paging beyond that.
- Needs: games from Steam or PSN.
- Size: 2 columns on phones, 3 on desktop.

### `steam`

- The full Steam panel: a header with completion, rank, hours, achievements, game
  count and perfect count; a featured recently played game; and a searchable,
  sortable game list.
- Limits: the game list pages 10 at a time. The featured game shows up to 6
  achievement icons. The side list shows 10 rarest or recent achievements.
- Needs: Steam connected.
- Size: this is a big widget. Give it a wide, tall box so the list and sidebar fit.

### `psn`

- The PlayStation version of the Steam panel: header with completion, trophies,
  games, hours and points; trophy tier counts; a featured game; and a searchable,
  sortable list.
- Limits: the list pages 10 at a time. The side list shows 10 rarest achievements.
  Trophy tiers always show.
- Needs: PSN connected.
- Size: wide and tall, same as Steam.

### `psn-trophies`

- A trophy case. Compact mode shows the total. Detailed mode shows a four part grid
  of Platinum, Gold, Silver and Bronze with metallic cups and counts.
- Limits: shows every trophy count. Hidden when the total is zero.
- Needs: PSN connected with trophies earned.
- Size: small. The detailed grid wants room for four columns.

### `retro` (RetroAchievements)

- Your RetroAchievements name and points. Detailed mode adds recent achievements
  and completed games.
- Limits: up to 10 recent achievements and up to 6 completed games.
- Needs: RetroAchievements connected.
- Size: flexible, taller in detailed mode.

## Anime

### `characters` (Favorite characters)

- A grid of character portraits with a small game or anime badge.
- Limits: no display cap. You add and reorder them yourself, visitors see them all.
- Needs: AniList favorites are mirrored in automatically, and you can add more from
  MyAnimeList.
- Size: a 3 column grid of tall portraits.

### `anime`

- A grid of title covers with a status label and score.
- Limits: compact mode shows 6, detailed mode shows 12. Titles you hide stay hidden
  from visitors.
- Needs: MyAnimeList or AniList connected.
- Size: 3 columns on phones, 4 on desktop. Toggle compact or detailed in settings.

### `manga`

- The same grid as anime, for manga.
- Limits: shows the first 12. Hidden titles stay hidden from visitors.
- Needs: MyAnimeList or AniList with manga.
- Size: 3 to 4 column grid.

## Everything in one

### `platforms` (tabbed)

- A single tabbed card with Steam, PlayStation, RetroAchievements, Anime and Manga
  tabs. Each tab holds that platform's full view.
- Limits: a tab only appears when its data exists. One tab shows at a time, and the
  Steam and PSN tabs page their lists internally.
- Needs: at least one connection.
- Size: a wide, tall box, since each tab is a full widget.
