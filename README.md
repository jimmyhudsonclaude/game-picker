# Game Picker

Pulls a random game from Jimmy's BoardGameGeek collection. Filters are optional: player count, time limit, and weight (Light under 2, Medium 2 to 3, Heavy over 3). The page takes on the color of whichever game it pulls. Tap the card to flip it.

**Live site:** https://jimmyhudsonclaude.github.io/game-picker/

## How it works
- `index.html` is the whole page.
- `games.js` holds the game list. It's built by `~/Claude/bgg-game-cards/tools/export_site.py` from the same data as the printed cards.
- Cover images load directly from BoardGameGeek. No cover files are stored here.

## Add new games
Ask Sam to "add my new games." That updates the printed cards and this site. By hand:

```bash
cd ~/Claude/bgg-game-cards && .venv/bin/python tools/fetch_collection.py jimmyhudson
```

Write card text for any new games in `data/games.json`, then:

```bash
.venv/bin/python tools/export_site.py && cd ~/Claude/game-picker && git commit -am "Update games" && git push
```

The site updates about a minute after the push.

## Fixing problems
- **A cover doesn't show:** BGG may be slow or the image moved. The card shows the game name instead. Re-running the export picks up new image links.
- **Filters seem stuck:** the page remembers your last filters on each device. Tap a selected filter again to clear it.
