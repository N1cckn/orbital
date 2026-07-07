# ORBITAL — Space Economy Markets

A single-file markets-intelligence dashboard for the space economy: aerospace, defense, and satellite equities on one screen. Built as a portfolio project exploring the intersection of space and finance.

**Live demo:** _add your GitHub Pages link here after deploying_

---

## What it does

**Markets** — A proprietary equal-weight sector index (ORBX) across 14 public companies, with a market-cap heatmap colored by daily moves, top gainers/decliners, breadth stats, a full coverage table with 30-day sparklines and composite scores, and an upcoming-catalysts calendar.

**News** — Live headlines pulled from Yahoo Finance per-ticker RSS feeds, with automatic fallback to the GDELT global news index and Hacker News if the primary feed is unreachable. Stories are auto-tagged with tickers, filterable by company, refresh every 5 minutes, and every card links to the original publisher. Presented as a hero story, a card grid, and a compact "wire" timeline.

**Company** — Deep-dive per name: price charts from 1-day intraday out to full history since IPO (with the IPO reference price marked), 50-day moving average, bull/base/bear scenario projections with confidence bands, fundamentals, computed risk metrics (annualized volatility, max drawdown, Sharpe), a transparent 0–100 composite "Orbital Score" with factor breakdown, and an interactive valuation sandbox (growth / exit multiple / discount-rate sliders → implied share price).

**Compare** — Up to four companies indexed to 100 at the window start, plus a side-by-side metrics table that highlights the best value per row.

**Portfolio Lab** — Allocate a hypothetical $10,000 across up to six names (with one-click presets), backtested over 12 months against the ORBX index: total return, alpha vs. benchmark, volatility, max drawdown, Sharpe ratio, an allocation donut, and a pairwise return-correlation matrix.

**IPO Watch** — The private pipeline (SpaceX/Starlink, Anduril, Sierra Space, Axiom, Relativity, and more) with estimated valuations, last raises, and listing-outlook badges.

**Sector Map** — Every company plotted by revenue growth vs. operating margin, bubble size by market cap.

Plus: a continuously sliding live ticker belt with terminal-style price flashes, a ⌘K command palette, a watchlist, and full mobile support (touch-scrub chart tooltips, phone-native chart canvases, responsive layouts).

## Tech notes

- **Zero dependencies, one file.** Vanilla JavaScript, hand-built SVG charts, CSS custom properties. No frameworks, no build step — open `index.html` in any modern browser.
- **Simulated live feed.** Prices are generated with seeded random walks (Brownian-bridge reconstruction back to each company's actual IPO date) and tick every 2.5 seconds. The interface is honestly labeled "LIVE · SIM" — the architecture is designed so a real market-data API could drop in.
- **All analytics are computed, not hardcoded** — Sharpe ratios, drawdowns, correlations, the scoring model, and the backtests all derive from the generated price series at runtime.
- **Resilient news pipeline.** Yahoo Finance RSS (via CORS relay) → GDELT → Hacker News → clearly-labeled offline samples, with the active provider shown in the UI.
- **Graceful degradation.** Polyfills and CSS fallbacks for older mobile browsers, a guidance screen for JavaScript-disabled preview contexts, and a visible error toast rather than silent failures.

## Disclaimer

Company fundamentals and prices are illustrative demo data, not real-time market data. Nothing here is investment advice. News headlines are fetched from third-party feeds and belong to their respective publishers.

## Roadmap

Real market data via a keyed API and a small backend proxy, persistent watchlists and portfolios, more coverage names, and earnings-transcript summaries per company.
