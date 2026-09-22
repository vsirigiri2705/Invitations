# Options Signals

A mobile-first web app to compose stock **options signals** (Call/Put, ticker, strike, expiry, position action) and dispatch them to WhatsApp in one tap.

Live, zero-backend, hosted free on GitHub Pages.

## What it does

- **Direction** — Call / Put toggle
- **Ticker** — searchable across ~7,100 US symbols (NASDAQ / NYSE / AMEX), searches by symbol *and* company name; any custom symbol is accepted too
- **Strike price** and **Expiry** (defaults to next Friday)
- **Action** — Average / Hold / Sell, to signal your latest thinking on the position
- **Note** — optional free-text
- **Live preview** of the exact WhatsApp-formatted message (uses WhatsApp `*bold*` / `_italic_`)
- **Send** — copies the message and opens WhatsApp
- **History** — last 50 sent signals stored locally; copy, re-send, or reload into the form
- Light / dark theme, works offline after first load

## The WhatsApp constraint (read this)

WhatsApp provides **no public way to auto-post into a group**:

- The official Cloud API does not support groups at all.
- The `wa.me` link can pre-fill text but targets an individual number, not a group, and requires a manual send tap.

So the app uses the only free, ToS-safe flow that reaches a group:

1. Tap **Send** → the message is copied to your clipboard and WhatsApp opens.
2. Pick your group and paste. One extra tap.

Optionally set a **direct contact number** in Settings to open a 1:1 chat with the text pre-filled (still a manual send, per WhatsApp).

> Want true one-tap auto-post to a group? That requires either a paid always-on server running `whatsapp-web.js` (against WhatsApp ToS, ban risk) or switching the channel to **Telegram** (official Bot API, free, no risk). Ask if you want the Telegram variant.

## Deploy (free, GitHub Pages)

1. Push this repo to GitHub.
2. Repo **Settings → Pages → Build and deployment → Source: Deploy from a branch**.
3. Branch: your default branch, folder `/ (root)`. Save.
4. App is live at `https://<user>.github.io/<repo>/` within ~1 minute.

No build step. It is plain static HTML/CSS/JS.

## Files

- `index.html` — the entire app (markup, styles, logic inline)
- `data/tickers.json` — slim `{s: symbol, n: name}` list of US tickers
- `.nojekyll` — tells GitHub Pages to serve the `data/` folder as-is

## Refresh the ticker list

Source: [rreichel3/US-Stock-Symbols](https://github.com/rreichel3/US-Stock-Symbols). Re-fetch the per-exchange JSON and rebuild `data/tickers.json` as `{s, n}` objects sorted by symbol.

## Roadmap ideas

- Live option quotes / underlying price
- Position P&L tracking
- Multi-leg spreads
- Telegram channel delivery (true auto-send)
