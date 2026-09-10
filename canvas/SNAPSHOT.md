# Daily ETF Trading Cycle Snapshot

- **Cycle ID:** `2026-09-10T2240Z`
- **Evaluated:** 2026-09-10 18:41 EDT (22:41 UTC)
- **Trigger:** cron `15 14 * * 1-5` (fired 2026-09-10T22:40:12Z)
- **Account:** SPIES (cash, agentic)
- **Result:** no orders

## Guardrails

| Check | Value | Decision |
| --- | --- | --- |
| Settled cash | $200.00 | Pass — spendable |
| Unsettled funds | $0.00 | Pass |
| Buying power | $200.00 | Pass |
| Kill switch ($85) | cash $200.00 | **Not triggered** — buying remains allowed |
| Hard position cap | $10 / 10% per symbol | N/A — no buys |
| Fractional-only | required | N/A — no buys |
| Volatility halt | 09:30–10:00 ET and 15:30–16:00 ET | Window not active now |
| Session | Regular hours closed 16:00 ET | **No orders** — do not queue regular-hours market/stop orders; they would hit the 09:30–10:00 ET halt at the next open |
| Watchlist (hard) | SPY, QQQ, XLK, VTI | Extra scan symbols are log-only |

## Portfolio

| Field | Amount |
| --- | --- |
| Account value | $200.00 |
| Cash / settled | $200.00 |
| Equity value | $0.00 |
| Open positions | none |
| Open / queued / recent orders | none |

## Exit scan

No open positions. 5% profit-target and 3% stop-loss sells were not applicable.

## Quotes

Regular-session last trade vs official prior close (2026-09-09). After-hours print shown for context only; entries/exits use regular-session rules.

### Hard watchlist

| Symbol | RTH last | After-hours | Prior close | Day chg (RTH) | 14-day RSI | RSI < 35 |
| --- | --- | --- | --- | --- | --- | --- |
| SPY | 757.87 | 758.05 | 762.40 | -0.59% | 48.00 | No |
| QQQ | 708.66 | 707.98 | 716.31 | -1.07% | 51.59 | No |
| XLK | 185.21 | 185.47 | 187.87 | -1.42% | 56.16 | No |
| VTI | 373.22 | 373.59 | 375.56 | -0.62% | 46.92 | No |

### Scan-only (not tradable)

| Symbol | RTH last | After-hours | Prior close | Day chg (RTH) | 14-day RSI | RSI < 35 |
| --- | --- | --- | --- | --- | --- | --- |
| XLI | 170.53 | 170.22 | 171.79 | -0.73% | 32.11 | **Yes** — buy blocked (off watchlist + session closed) |
| XLF | 56.88 | 56.90 | 57.06 | -0.32% | 46.02 | No |
| XLE | 64.94 | 64.89 | 65.31 | -0.57% | 68.42 | No |
| XLV | 165.67 | 165.65 | 166.58 | -0.55% | 43.61 | No |
| IWM | 287.74 | 287.71 | 290.64 | -1.00% | 39.87 | No |
| TLT | 80.79 | 80.75 | 81.73 | -1.15% | 40.87 | No |
| GLD | 396.46 | 395.70 | 403.35 | -1.71% | 50.15 | No |

14-day RSI is the latest completed daily regular-session bar (`2026-09-09`). Official SIP close for 2026-09-10 was not yet published at evaluation time.

## Entry decisions

| Symbol | Eligible? | Reason |
| --- | --- | --- |
| SPY | No | RSI 48.00 >= 35 |
| QQQ | No | RSI 51.59 >= 35 |
| XLK | No | RSI 56.16 >= 35 |
| VTI | No | RSI 46.92 >= 35 |
| XLI | No | RSI 32.11 < 35 but **not on hard watchlist**; session also closed |
| XLF, XLE, XLV, IWM, TLT, GLD | No | Off watchlist; RSI >= 35 |

No $10 fractional BUY and no paired 3% stop-loss were placed.

## Executed orders

None.

## Next action

Re-evaluate in the next regular session **after 10:00 ET** (outside the open volatility halt). Continue hourly stop monitoring only if a watchlist position is open.
