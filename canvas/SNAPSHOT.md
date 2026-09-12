# Daily ETF Trading Canvas Snapshot

**Cycle ID:** `2026-09-10T2215Z`  
**Triggered at:** 2026-09-10T22:15:27.470Z (cron `15 14 * * 1-5`)  
**Evaluated at:** 2026-09-10T22:16:10Z / 2026-09-10 18:16:10 EDT  
**Account:** SPIES (••••4079) — cash individual  
**Status:** COMPLETE — no orders executed

---

## 1. Guardrails

| Check | Result | Decision |
| --- | --- | --- |
| Settled cash | $200.00 (cash $200.00, unsettled $0.00, buying power $200.00) | Pass — sufficient for a $10 fractional buy |
| Emergency kill switch ($85) | Cash $200.00 >= $85.00 | Pass — buying **not** halted |
| Position size cap | Max $10 (10% of $100 test pool) per name | Standby — no entry this cycle |
| Volatility halt | Regular session closed at 16:00 EDT. Clock is 18:16 EDT (after the 15:30–16:00 EDT close halt) | No live regular-hours book. Any market/fractional order would queue into the 09:30–10:00 EDT open halt, so **no orders are queued** |
| Watchlist only | SPY, QQQ, XLK, VTI | Enforced |
| MCP data quality | Accounts, portfolio, quotes, RSI, positions, orders, and alerts all returned complete, non-ambiguous payloads | Pass — cycle continued |

## 2. Quotes (get_equity_quotes)

Regular-hours last print is used as the session reference. Extended prints are shown for context only.

| Symbol | RTH last | RTH last time (UTC) | Extended last | Prev close (2026-09-09) | Bid / Ask | Day change vs adj. close |
| --- | --- | --- | --- | --- | --- | --- |
| SPY | 757.87 | 2026-09-10T19:59:59Z | 758.30 | 762.40 | 758.28 / 758.38 | -0.59% |
| QQQ | 708.66 | 2026-09-10T19:59:59Z | 708.81 | 716.31 | 708.79 / 708.84 | -1.07% |
| XLK | 185.21 | 2026-09-10T19:59:59Z | 185.47 | 187.87 | 185.29 / 185.44 | -1.42% |
| VTI | 373.22 | 2026-09-10T19:59:58Z | 373.30 | 375.56 | 373.20 / 373.68 | -0.62% |

All four symbols: `has_traded=true`, `state=active`.

## 3. 14-day RSI (daily, period 14, regular hours)

Latest completed daily bar from `get_equity_technical_indicators` (bar date 2026-09-09). Entry requires RSI **< 35**.

| Symbol | RSI(14) | Bar begins | vs 35 | Entry? |
| --- | --- | --- | --- | --- |
| SPY | 47.9992 | 2026-09-09T00:00:00Z | 12.9992 above | No |
| QQQ | 51.5850 | 2026-09-09T00:00:00Z | 16.5850 above | No |
| XLK | 56.1574 | 2026-09-09T00:00:00Z | 21.1574 above | No |
| VTI | 46.9170 | 2026-09-09T00:00:00Z | 11.9170 above | No |

**ENTRY:** No watchlist ETF is oversold. No $10 fractional BUY. No 3% stop-loss order paired.

## 4. Open positions / EXIT scan

| Source | Result |
| --- | --- |
| `get_equity_positions` | `positions: []` |
| `get_equity_orders` (queued) | `orders: []` |
| `get_equity_orders` since 2026-09-01 | `orders: []` |
| `get_alerts` | `alerts: []` |

**EXIT:** No open lots. 5% profit target and 3% stop-loss from cost basis were not evaluated against a live position.

## 5. Executed orders

None this cycle.

## 6. Portfolio after cycle

| Field | Value |
| --- | --- |
| Account value | $200.00 |
| Equity value | $0.00 |
| Cash / settled cash | $200.00 |
| Buying power | $200.00 |
| Open ETF positions | 0 |
| Pending / queued orders | 0 |

## 7. Next cycle notes

- Re-scan RSI after the next regular session. Still require RSI < 35 plus settled cash >= $10 and cash >= $85.
- If a buy becomes eligible, size at **$10 notional** (`type=market`, `dollar_amount=10.00`, `market_hours=regular_hours`) and immediately pair a 3% stop (broker stop or hourly monitor).
- Do not place orders during 09:30–10:00 or 15:30–16:00 America/New_York.
