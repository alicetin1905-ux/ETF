# ETF

A BTC perpetual chart, styled to match the ATLAS Suite boards, with a VPVR volume profile and daily ETF inflow/outflow for the
US spot Bitcoin, Ether and Solana ETFs.

**Live page: https://alicetin1905-ux.github.io/ETF/**

Or open `index.html` in a browser. There is no build step; the charts use TradingView Lightweight Charts from a CDN.

## What's on the page

- **Price chart** of the BTC perpetual with 5M / 15M / 1H / 4H timeframes. Prices come from Binance
  USDⓈ-M Futures (BTCUSDT), falling back to OKX (BTC-USDT-SWAP) if Binance is blocked, and to demo data
  if neither is reachable. Refreshes every 5 seconds.
- **VPVR** (volume profile of the visible range) inside the chart: blue = volume from candles that closed
  up, yellow = closed down, brighter rows = 70% value area, red line = point of control (POC). Toggle it
  with the VPVR button. The boxes at the top show the POC, value area high/low and open interest.
- **ETF inflow/outflow** under the chart, with a BTC / ETH / SOL switch: daily net flows, cumulative net
  inflow, 5- and 20-day totals, net assets, coins held and a per-fund table. Data comes from SoSoValue's
  public API and is checked for updates every 30 minutes. SoSoValue has no ETF data for other coins.

## Files

- `index.html` — the page.
- `scripts/etf_flows.py [btc|eth|sol]` — fetches the same ETF data as JSON.
- `hosted/claude-artifact.html` — the version published as a claude.ai page. It gets prices through the
  Crypto.com connector (BTCUSD-PERP) and reads ETF data from the page's database, which a daily
  scheduled job fills using `scripts/etf_flows.py`.
