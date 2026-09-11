# Daily ETF Trading Cycle Snapshot

- **Cycle ID:** `2026-09-11T1418Z`
- **Evaluated:** 2026-09-11 10:21 EDT (14:21 UTC)
- **Trigger:** cron `15 14 * * 1-5` (fired 2026-09-11T14:18:55Z)
- **Account:** SPIES (cash, agentic)
- **Result:** 2 buys filled; 3% GTC stop-market orders rejected (fractional TIF); price alerts set

## Guardrails

| Check | Value | Decision |
| --- | --- | --- |
| Settled cash (pre-trade) | $200.00 | Pass — spendable |
| Unsettled funds | $0.00 | Pass |
| Buying power (pre-trade) | $200.00 | Pass |
| Kill switch ($85) | cash $200.00 → $180.00 | **Not triggered** — buying remained allowed |
| Hard position cap | $10 / 10% per symbol | Enforced — $10 XLI + $10 TLT |
| Fractional-only | required | Pass — dollar-based market buys |
| Volatility halt | 09:30–10:00 ET and 15:30–16:00 ET | Window not active (10:21 ET) |
| Session | Regular hours open | Orders allowed |
| Watchlist (hard) | SPY, QQQ, XLK, VTI, XLI, XLF, XLE, XLV, IWM, TLT, GLD | All 11 tradable |

## Portfolio

| Field | Amount |
| --- | --- |
| Account value | $200.00 |
| Cash / settled (post-trade) | $180.00 |
| Equity value | $20.00 |
| Open positions | XLI 0.057954 @ $172.5499; TLT 0.123068 @ $81.2557 |
| Open / queued stop orders | none (GTC fractional stop-market rejected) |

## Exit scan

Open positions were scanned against 5% profit / 3% stop from cost basis. Neither XLI nor TLT had reached either threshold at evaluation (both ~0% vs fill). No SELL executed.

| Symbol | Qty | Cost | Last | PnL vs cost | 3% stop | 5% target | Action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| XLI | 0.057954 | $172.5499 | $172.56 | ~0.0% | $167.37 | $181.18 | Hold |
| TLT | 0.123068 | $81.2557 | $81.25 | ~0.0% | $78.82 | $85.32 | Hold |

## Quotes

Regular-session last trade vs official prior close (2026-09-10). 14-day RSI is the latest completed daily regular-session bar (`2026-09-10`).

| Symbol | RTH last | Prior close | Day chg (RTH) | Bid | Ask | 14-day RSI | RSI < 35 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SPY | 765.69 | 757.83 | +1.04% | 765.67 | 765.70 | 44.17 | No |
| QQQ | 716.08 | 708.69 | +1.04% | 716.07 | 716.09 | 46.49 | No |
| XLK | 187.96 | 185.22 | +1.48% | 187.92 | 187.94 | 50.91 | No |
| VTI | 376.93 | 373.24 | +0.99% | 376.91 | 376.94 | 43.22 | No |
| XLI | 172.48 | 170.55 | +1.13% | 172.46 | 172.49 | 30.36 | **Yes** |
| XLF | 57.145 | 56.87 | +0.48% | 57.15 | 57.16 | 44.51 | No |
| XLE | 65.17 | 64.93 | +0.37% | 65.17 | 65.18 | 64.99 | No |
| XLV | 166.17 | 165.66 | +0.31% | 166.15 | 166.18 | 41.47 | No |
| IWM | 289.88 | 287.70 | +0.76% | 289.88 | 289.90 | 36.42 | No |
| TLT | 81.2699 | 80.78 | +0.61% | 81.26 | 81.27 | 34.28 | **Yes** |
| GLD | 401.94 | 396.36 | +1.41% | 401.89 | 401.94 | 45.76 | No |

### Required quote disclosures (verbatim)

Buy review (10:20 AM ET):

- XLI: Bid $172.51 × 100 V · Ask $172.53 × 200 P · Last $172.54 × 200 P. Updated 10:20 AM ET.
- TLT: Bid $81.24 × 13500 Q · Ask $81.25 × 8700 V · Last $81.245 × 149 D. Updated 10:20 AM ET.

Stop-loss review (10:21 AM ET; orders not placed):

- XLI: Bid $172.53 × 400 P · Ask $172.55 × 100 Q · Last $172.54 × 100 V. Updated 10:21 AM ET.
- TLT: Bid $81.24 × 9300 Q · Ask $81.25 × 11000 P · Last $81.2492 × 2450 D. Updated 10:21 AM ET.

## Entry decisions

| Symbol | Eligible? | Reason |
| --- | --- | --- |
| SPY | No | RSI 44.17 >= 35 |
| QQQ | No | RSI 46.49 >= 35 |
| XLK | No | RSI 50.91 >= 35 |
| VTI | No | RSI 43.22 >= 35 |
| XLI | **Yes** | RSI 30.36 < 35; settled cash available; $10 fractional BUY filled |
| XLF | No | RSI 44.51 >= 35 |
| XLE | No | RSI 64.99 >= 35 |
| XLV | No | RSI 41.47 >= 35 |
| IWM | No | RSI 36.42 >= 35 |
| TLT | **Yes** | RSI 34.28 < 35; settled cash available; $10 fractional BUY filled |
| GLD | No | RSI 45.76 >= 35 |

## Executed orders

| Time (UTC) | Symbol | Side | Type | Amount / qty | Fill | State |
| --- | --- | --- | --- | --- | --- | --- |
| 2026-09-11T14:20:53Z | XLI | buy | market | $10.00 / 0.057954 | $172.5499 | filled |
| 2026-09-11T14:20:53Z | TLT | buy | market | $10.00 / 0.123068 | $81.2557 | filled |

Paired 3% GTC `stop_market` sells were **not** placed. Broker rejected both with `Invalid time in force for fractional order.` Per compliance, execution of those stops was aborted (no retry with GFD or other modified parameters).

## Monitoring (stop / target substitute)

Hourly/next-cycle monitoring is required. Informational Robinhood price alerts (not live orders):

| Symbol | Condition | Threshold | Alert ID |
| --- | --- | --- | --- |
| XLI | price_below (3% stop) | $167.37 | `4df3b6a9-dca0-4f81-ac19-8dfa54dd814c` |
| XLI | price_above (5% target) | $181.18 | `2ee087df-d31a-4802-b5b5-2aea68a45baa` |
| TLT | price_below (3% stop) | $78.82 | `09024bd8-35eb-42b7-8c07-1aeba2616b15` |
| TLT | price_above (5% target) | $85.32 | `381223e0-58b8-4652-8ff6-ff8e92121ee4` |

## Next action

Re-evaluate open XLI and TLT vs cost basis. Sell immediately if price is ≤ 3% below entry or ≥ 5% above entry. Do not queue regular-hours market/stop orders inside 09:30–10:00 ET or 15:30–16:00 ET.
