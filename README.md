# Opfikon Rams · 75 Shootout

Standings for the Rams' 75 Shootout. After every game the top three score points: 1st gets 3, 2nd gets 2 and 3rd gets 1. The app is a single `index.html` file with no build step.

Live app: https://haruku08.github.io/opfikon-rams/

## What it does

- **Table:** season standings (seasons run August to July) or all-time. Shows the leader, the number of games, the last winner, and each player's move since the previous game.
- **Race:** cumulative points over the season, with the top five in colour.
- **Players:** totals, points per season, the last 12 games, and longest and current podium streaks.
- **Games:** every game's podium. Admins can edit and delete games here.
- **Add:** record a game (admins only). The date defaults to today, and tapping recent players fills 1st, 2nd and 3rd in order.
- **Home screen:** phones show an "Add to home screen" banner with steps for iPhone, Android, Samsung Internet and in-app browsers. Android Chrome gets a one-tap Install button.
- **Updates:** the app checks `version.json` when it opens and whenever it comes back to the foreground. If there's a new version it reloads by itself. If you're halfway through entering a game, it shows an Update button instead. Results also refresh every two minutes.

## Data

All results are in `data/games.json`, one game per line:

```json
{"d":"2026-11-10","p":["Kim","Mirko","Renni"]}
```

Viewers read the file from GitHub. Saving a game commits it straight to `main`.

### Recording games (admin)

1. Create a fine-grained token at GitHub → Settings → Developer settings → Fine-grained tokens. Limit it to this repository only, with **Contents: Read and write**.
2. In the app, open **Settings**, paste the token, and tap **Unlock recording**.

The token is stored only in that browser. Never share it.

## Releasing an update

Bump the version in two places, then push to `main`:

1. `APP_VERSION` in `index.html`
2. `version.json`

`.github/workflows/pages.yml` deploys every push to GitHub Pages.

Powered by Haruku.
