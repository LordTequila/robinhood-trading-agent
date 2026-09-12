# ETF trading cycle snapshot

- **Cycle id:** `2026-09-10T2224Z`
- **Evaluated:** 2026-09-10 18:24 EDT (22:24 UTC)
- **Trigger:** weekday cron `15 14 * * 1-5` (delayed fire at 22:24 UTC)
- **Account:** SPIES (cash, tradable). Account number omitted.
- **Session:** Regular hours closed at 16:00 ET. Evaluation is after the close.
- **Result:** No orders placed.

## Guardrails

| Check | Result |
| --- | --- |
| Settled cash / buying power | **$200.00** cash, **$200.00** buying power, unsettled funds **$0.00** |
| Emergency kill switch (< $85) | **Not triggered** ($200.00 available) |
| Hard position cap ($10 / 10%) | No new allocation. Cap remains $10 fractional notional if an entry fires. |
| Watchlist buys | Restricted to **SPY, QQQ, XLK, VTI**. Extra tickers were scanned only. |
| Entry rule | 14-day RSI < 35 on a short-term pullback |
| Exit rule | Sell at **+5%** from cost basis or **-3%** stop from cost basis |
| Volatility halt | No orders in 09:30–10:00 ET or 15:30–16:00 ET |
| After-close order policy | Do **not** queue `regular_hours` market / fractional-dollar orders after the close — they would print at 09:30 ET inside the open halt window |
| Open positions | **None** |
| Queued / confirmed orders | **None** |
| MCP data quality | Quotes, portfolio, positions, orders, and RSI calls returned complete data. Daily RSI latest bar is **2026-09-09** (today’s completed daily bar not yet published). |

## Quotes (regular-session last trade vs prior official close)

Prior official close is 2026-09-09. Last regular trade timestamps are 2026-09-10 ~15:59:59 ET.

| Symbol | Role | Last regular | Prior close | Day change | After-hours last |
| --- | --- | --- | --- | --- | --- |
| SPY | watchlist | 757.87 | 762.40 | -0.59% | 758.51 |
| QQQ | watchlist | 708.66 | 716.31 | -1.07% | 708.98 |
| XLK | watchlist | 185.21 | 187.87 | -1.42% | 185.47 |
| VTI | watchlist | 373.22 | 375.56 | -0.62% | 373.30 |
| XLF | scan-only | 56.88 | 57.06 | -0.32% | 56.90 |
| XLE | scan-only | 64.94 | 65.31 | -0.57% | 64.97 |
| XLV | scan-only | 165.67 | 166.58 | -0.55% | 166.23 |
| XLI | scan-only | 170.53 | 171.79 | -0.73% | 170.22 |
| IWM | scan-only | 287.74 | 290.64 | -1.00% | 287.80 |
| TLT | scan-only | 80.79 | 81.73 | -1.15% | 80.76 |
| GLD | scan-only | 396.46 | 403.35 | -1.71% | 396.00 |

## 14-day RSI (daily, regular bounds, period 14)

Latest published bar: **2026-09-09**. Entry threshold: RSI < 35.

| Symbol | Role | RSI | Entry? |
| --- | --- | --- | --- |
| SPY | watchlist | 48.09 | No |
| QQQ | watchlist | 51.79 | No |
| XLK | watchlist | 56.29 | No |
| VTI | watchlist | 47.04 | No |
| XLF | scan-only | 46.10 | No (off-watchlist) |
| XLE | scan-only | 68.12 | No (off-watchlist) |
| XLV | scan-only | 43.41 | No (off-watchlist) |
| XLI | scan-only | **32.41** | **Blocked** — RSI < 35 but XLI is outside the hard watchlist; session also closed |
| IWM | scan-only | 40.16 | No (off-watchlist) |
| TLT | scan-only | 41.17 | No (off-watchlist) |
| GLD | scan-only | 50.22 | No (off-watchlist) |

## Exits

No open equity positions. Profit-target (+5%) and stop-loss (-3%) scans had nothing to sell.

## Orders this cycle

None. No BUY (no watchlist RSI < 35; market closed). No SELL (flat).

Machine log: `canvas/cycles/2026-09-10T2224Z.json`
