# ⚾ Atlanta Braves 2026 Dashboard

A live MLB dashboard for the Atlanta Braves — single HTML file, no API key, no backend, no build step. Just put it on GitHub Pages and share the link.

**Data source:** [MLB Stats API](https://statsapi.mlb.com) — free, public, no authentication required.

---

## Deploy to GitHub Pages (3 steps)

### 1. Create a new repo
Go to [github.com/new](https://github.com/new), name it `braves-dashboard`, set it to **Public**, and click **Create repository**.

### 2. Upload the file
On the new repo page, click **Add file → Upload files**, drag in `index.html`, and commit.

Or via the command line:
```bash
git clone https://github.com/YOUR_USERNAME/braves-dashboard.git
cd braves-dashboard
cp /path/to/index.html .
git add index.html
git commit -m "Add Braves dashboard"
git push
```

### 3. Enable Pages
Go to **Settings → Pages**, set source to **Deploy from a branch**, pick `main` / `(root)`, and click **Save**.

Your dashboard is live in ~60 seconds at:
```
https://YOUR_USERNAME.github.io/braves-dashboard
```

---

## Why it works on GitHub Pages but not as a local file

The MLB Stats API is a public API, but browsers block cross-origin requests from `file://` URLs (this is called CORS). GitHub Pages serves your file over `https://`, which the MLB API accepts. If you want to run it locally during development, use any simple local server:

```bash
# Python (built-in)
python3 -m http.server 8000
# then open http://localhost:8000

# Node (npx, no install needed)
npx serve .
```

---

## Features

| Tab | What's in it |
|-----|-------------|
| **Overview** | Record, win %, streak, last 10, runs/game, ERA, AVG, OPS · NL East standings · Wins/losses season arc chart · Runs scored vs. allowed per game |
| **Game Log** | Every completed 2026 regular season game with result, score, and running record |
| **Stats** | Full team hitting (AVG, OBP, SLG, OPS, HR, RBI, SB…) and pitching (ERA, WHIP, K, saves, holds…) |
| **Schedule** | Full 162-game schedule — past games show results, future games show local start times |

Hit **⟳ Refresh** any time to pull fresh data from the MLB API.

---

## Customizing for another team

1. Find your team's ID at `https://statsapi.mlb.com/api/v1/teams?sportId=1`
2. Change `const TEAM_ID = 144` near the top of `index.html`
3. Change `leagueId=104` (NL) to `leagueId=103` if switching to an AL team
4. Update the page title and header text

---

## License
MIT — do whatever you want with it. Go Braves! ⚾
