# Layers Dice Online — Pirate Dark Fantasy

Mobile-friendly browser multiplayer Liar's Dice with private 5-character rooms, 2–10 players, pirate-themed styling, animated dice, local session resume, and the custom rules described below.

## Rules implemented
- Normal bidding ranks **face value first** (2 < 3 < 4 < 5 < 6 < Joker), then quantity within the same face. Thus 1×5 is higher than 99×4, while 4×2 is higher than 3×2.
- If any active player has exactly one die, a special round starts with a one-die player opening. Their first bid must be a number 2–6 and locks the face for the round. Later bids can only increase quantity in that same number row.
- In this one-die special round, Jokers are not counted as a number and do not act as wildcards. Only the exact announced face is counted.
- In ordinary rounds, a bid on 2–6 counts matching dice plus Jokers; a Joker bid counts Jokers only.
- Each player starts with five dice. A challenge loser loses one die; the last player with dice wins.
- Dice hide/restore controls only change the local visual display, not the actual game.

## Run locally
1. Install Node.js 18 or newer.
2. In this folder run `npm install`.
3. Run `npm start` and open `http://localhost:3000`.

## Deploy on Render
- Build command: `npm install`
- Start command: `npm start`
- Root directory: leave empty when `package.json`, `server.js` and `public/` are at repository root.
- Upload/commit all files, then use Render **Manual Deploy → Deploy latest commit**.

## Session saving caveat
Room state is written to `rooms-data.json` on the server and the browser stores a player token so refreshing the page can rejoin the same seat. This is best-effort persistence: Render's default ephemeral filesystem can be cleared during restarts/deploys. For reliable long-term persistence, attach a persistent disk or use a database. The JSON file is intended for a single server instance.
