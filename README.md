# 🌙 Game Launcher

A game-launcher website (static site — deploys free on Vercel from GitHub).

## Features

- ⏱ Playtime tracker (per game + total), live counter on the player bar
- 🆕 NEW! tag — new games show a pulsing badge and sort to the top
- 🕘 Recently played section (top of homepage)
- ⭐ Favorites section + a "⭐ Favorites" filter chip (star button on every card)
- 🎲 Random game button
- 📊 Stats page — current streak 🔥, longest streak 🏆, total playtime, games played, favorite category, most-played leaderboard with 👑 #1
- 🔥 Daily streaks (visiting counts) — **weekend freeze**: Sat/Sun never break your streak
- 😊 Nickname ("Welcome back, Alex 👋")
- 🔊 Mute button on the player bar (best effort), Esc = back home, F = fullscreen
- 🎨 Accent picker, cloak tab, ambient effects, UI sounds (all in Settings, saved locally)
- 🌊 Smooth fade transitions between pages

All data is stored in the browser (localStorage) — no accounts, no backend.

## Project structure

```
├── index.html          # Home: search, chips, sections, settings
├── game.html           # Player: iframe, mute, fullscreen, live playtime
├── stats.html          # Stats page
├── css/style.css
├── js/common.js        # Storage, streaks, sounds, transitions
├── js/app.js           # Home logic
├── js/game.js          # Player logic
├── js/stats.js         # Stats logic
├── data/games.json     # ⭐ THE ONLY FILE YOU EDIT TO ADD GAMES
├── assets/games/       # Thumbnail images
└── games/              # Game files (one folder per game, needs index.html)
```

## ➕ Adding a game

1. Drop the thumbnail into `assets/games/` (square, or 16:9 for featured)
2. Drop the game files into `games/my-game/` (must contain `index.html`)
3. Add to `data/games.json`:

```json
{
  "id": "my-game",
  "title": "My Game",
  "developer": "Some Dev",
  "category": "Flash",
  "image": "assets/games/my-game.png",
  "url": "games/my-game/index.html",
  "featured": false,
  "isNew": true
}
```

`"isNew": true` gives it the NEW! badge + top sorting. Remove it after a week or two.

## 🚀 Deploy to Vercel from GitHub

```bash
git init
git add .
git commit -m "game launcher"
git branch -M main
git remote add origin https://github.com/YOUR-USER/YOUR-REPO.git
git push -u origin main
```

Then vercel.com → Add New → Project → import the repo → framework preset **Other** → Deploy.
Every push auto-redeploys.
