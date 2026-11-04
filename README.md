# League Ledger

Season-long tracker for a 10-team, 9-category head-to-head fantasy basketball league (2026-27 NBA season). Built as a single-page web app.

## What's here

- `index.html` — the entire app: layout, styles and logic in one file. Exported from the claude.ai artifact on Nov 4, 2026 (version 1793660338-b3e7).

## How it runs today

The live copy is a published claude.ai artifact: https://claude.ai/artifact/Uq5Wh8KfoKajBUzZGENKfp

Two parts of the page only work there:

- **Shared data.** Rosters, moves, targets, weekly results, player pool and season totals are stored in the artifact's built-in database (`window.claude` runtime), not inside this file. Opening `index.html` on its own shows the layout with no league data.
- **Refresh rosters button.** Reads the league's ESPN pages through the Claude desktop app's built-in browser. Outside that app the button is disabled.

## Toward a standalone website

To turn this into a site any league can use, the plan is to:

1. Replace the artifact database with a hosted one (e.g. Supabase or Firebase).
2. Add a setup screen that takes an ESPN league ID and season and maps team ids to owner names.
3. Move the ESPN fetching to a small server-side function so it works in any browser.
4. Host the result on GitHub Pages or a similar static host.

## Data model (current)

Collections in the artifact database:

- `settings/league` — league settings, team names, ESPN mapping
- `rosters/<teamId>` — each team's players
- `moves/<id>` — adds, drops, trades, IR moves
- `targets/<id>` — waiver shopping list
- `weeks/w<N>` — category results per week
- `players/pool` — player pool with per-game stats
- `league/totals`, `league/weeks`, `league/schedule`, `league/lastRefresh`, `draft/board`
