# FantasyFootballWebsite

Live site: https://jahmann9.github.io/FantasyFootballWebsite/

This repository is a lightweight, static fantasy football reporting site built around a single JSON dataset. There is no backend, database, or build pipeline; the app is intentionally simple and centered on presenting league data in a browser.

## What is in the repo?

- `league_summary.json` — the source of truth for the league data. It contains:
  - `career_totals`: each player's season/career-level record, including wins, losses, points for, points against, average points, and winning percentage.
  - `head_to_head`: nested records by player, then opponent, with each matchup's wins, losses, and points scored/allowed.
- `TwoHandLeague.html` — the single-page dashboard that reads the JSON and renders it into a user-friendly table and expandable matchups view.

## How the app works

1. The browser loads `TwoHandLeague.html`.
2. The script calls `loadDefaultData()`, which fetches `league_summary.json` from the same folder.
3. The JSON is parsed and passed to `render(data)`.
4. `render(data)` builds:
   - a sortable career totals table
   - expandable head-to-head sections for each player
5. The page also includes controls to:
   - render pasted JSON manually
   - clear the textarea
   - reset to the default dataset
   - load a small sample dataset for testing

## Data flow

The repo follows a very straightforward pattern:

```text
league_summary.json
        |
        v
TwoHandLeague.html (JavaScript)
        |
        v
Browser renders report UI
```

This means the app is easy to inspect and edit: if you want to change the league numbers, update the JSON, and the page will reflect those changes automatically when refreshed.

## Local usage

You can view the dashboard either by opening `TwoHandLeague.html` directly in a browser or by serving the folder locally, for example:

```bash
python -m http.server
```

Then open the localhost URL shown in the terminal.

## Notes

- The app is designed for presentation rather than persistence.
- It does not require a package install or app framework.
- The HTML file contains the logic for sorting, rendering, and data fallback behavior in embedded JavaScript.

In short, this repo is a static data-reporting tool for a fantasy football league: one JSON file provides the numbers, and one HTML page turns those numbers into a readable report.
