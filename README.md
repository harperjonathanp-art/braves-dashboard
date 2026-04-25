# ⚾ Atlanta Braves 2026 Dashboard

A live, AI-powered MLB dashboard for the Atlanta Braves — built as a single HTML file with no backend, no build step, and no dependencies to install.

**[Live Demo →](https://your-username.github.io/braves-dashboard)**

![Braves Dashboard](https://img.shields.io/badge/Atlanta-Braves-CE1141?style=flat-square&logo=data:image/svg+xml;base64,)

---

## Features

- **AI-powered live data** — Claude searches the web and returns current stats, standings, game log, and schedule on every refresh
- **4 tabs**: Overview · Game Log · Stats · Schedule
- **Charts**: Wins/losses season arc, runs scored vs. allowed per game
- **NL East standings** with win-percentage bars
- **Zero dependencies** — single `index.html`, works in any browser
- **API key stored locally** — never committed to your repo

---

## How to Deploy on GitHub Pages

### 1. Create a new GitHub repo

Go to [github.com/new](https://github.com/new) and create a public repository called `braves-dashboard` (or any name you like).

### 2. Add the file

Upload `index.html` to the root of the repo. You can do this via the GitHub web UI (drag and drop) or via git:

```bash
git clone https://github.com/YOUR_USERNAME/braves-dashboard.git
cd braves-dashboard
cp /path/to/index.html .
git add index.html
git commit -m "Add Braves dashboard"
git push
```

### 3. Enable GitHub Pages

1. Go to your repo on GitHub
2. Click **Settings** → **Pages** (left sidebar)
3. Under **Source**, select **Deploy from a branch**
4. Set **Branch** to `main` (or `master`) and folder to `/ (root)`
5. Click **Save**

Your dashboard will be live at:
```
https://YOUR_USERNAME.github.io/braves-dashboard
```
(Takes ~60 seconds to deploy on first push.)

### 4. Get an Anthropic API key

1. Go to [console.anthropic.com/keys](https://console.anthropic.com/keys)
2. Create a new key
3. When you open the dashboard, paste the key into the setup screen
4. The key is stored in your browser's `localStorage` — it is **never** sent to GitHub or anyone except Anthropic's API

---

## How It Works

```
Browser → Anthropic API (claude-sonnet + web_search tool)
                ↓
      Claude searches the web for current
      Braves stats, standings, schedule
                ↓
      Returns structured JSON → Dashboard renders
```

The dashboard bakes in seed data (last known stats) so it renders instantly. Clicking **Refresh** triggers a live AI-powered fetch — this calls the Anthropic API directly from your browser and costs a few cents per click.

---

## Data Refreshed on Each Click

| Section | Data |
|---------|------|
| Overview | Record, win %, streak, last 10, ERA, AVG, OPS |
| Standings | Full NL East W-L and win percentage |
| Game Log | Every completed 2026 regular season game |
| Schedule | Next 7 upcoming games with times |
| Charts | Season wins/losses arc, runs scored vs. allowed |

---

## Sharing

Once deployed, just send the GitHub Pages URL to friends. They'll see a setup screen asking for their own API key — each person uses their own key, so you don't share yours.

Alternatively, if you want a "no key required" version for friends, you can bake a key into the HTML — but **do not commit that version to a public repo** or your key will be exposed.

---

## Customization

The seed data at the top of `index.html` (the `SEED` object) can be edited to any team by changing:
- The team names and records in `nlEast`
- The `recentGames`, `upcomingGames`, and `gameLog` arrays
- The `hitting` and `pitching` stats objects

And updating the AI prompt in `fetchAI()` to ask about a different team.

---

## License

MIT — do whatever you want with it. Go Braves! ⚾
