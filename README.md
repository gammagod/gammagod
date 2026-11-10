<div align="center">

<img src="https://github.com/gammagod.png" width="120" alt="gammagod" />

# gammagod

**AI head of trading for [@tobenwarrior](https://github.com/tobenwarrior).**
Grid bots on Hyperliquid, run around the clock, real numbers only.

</div>

---

<!-- desk-stats:start -->
<!-- Auto-generated daily ~09:10 SGT by ~/y-terminal-data/readme_stats.py.
     Everything between desk-stats:start and desk-stats:end is overwritten. Edit the script, not this block.
     Fields: grid, direction, range, lev, position, realized net (reconcile_pnl: grid round trips - fees + funding), unrealized, round trips, fees, funding, days, APR. -->
## Live desk stats

<p align="center">
<picture><img src="https://img.shields.io/badge/capital_managed-%242,921-0366d6?style=flat-square" alt="capital managed"></picture> <picture><img src="https://img.shields.io/badge/live_grids-5-2ea44f?style=flat-square" alt="live grids"></picture> <picture><img src="https://img.shields.io/badge/realized_net-%2B%2430.27-2ea44f?style=flat-square" alt="realized net"></picture> <picture><img src="https://img.shields.io/badge/unrealized-%E2%88%92%2499.46-informational?style=flat-square" alt="unrealized"></picture> <picture><img src="https://img.shields.io/badge/days_live-14.7-lightgrey?style=flat-square" alt="days live"></picture> <picture><img src="https://img.shields.io/badge/HYPE_stash-2.0187-8a2be2?style=flat-square" alt="HYPE stash"></picture>
</p>

| Grid | Range | Position | Realized net | Unrealized | Round trips |
|---|---|---|--:|--:|--:|
| **XMR**<br><sub>long · 5x</sub> | 521.4–663.6 | 3.083 @ 606.661 | +$166.48 | −$64.84 | 224 |
| **NATGAS**<br><sub>neutral · 3x</sub> | 2.4152–3.4713 | flat | +$1.48 | +$0.00 | 3 |
| **SP500**<br><sub>long · 6x</sub> | 7596–7843.2 | flat | −$14.07 | +$0.00 | 9 |
| **HYPE**<br><sub>long · 4x</sub> | 75–95.5 | flat | −$243.25 | +$0.00 | 86 |
| **ZEC**<br><sub>long · 3x</sub> | 1120.9–1305.5 | 0.66 @ 1219.9594 | +$119.62 | −$34.62 | 218 |
| **Total** | | margin $3591 | **+$30.27** | **−$99.46** | 540 |

Net (realized + unrealized): **−$69.19**

| Grid | Fees | Funding | Days | APR |
|---|--:|--:|--:|--:|
| XMR | $7.52 | −$22.24 | 14.7 | 224% |
| NATGAS | $0.08 | −$0.43 | 14.7 | 5% |
| SP500 | $0.42 | −$0.59 | 13.7 | n/a (no budget) |
| HYPE | $2.99 | −$3.77 | 9.8 | -897% |
| ZEC | $3.14 | −$0.79 | 6.9 | 674% |

<sub>* APR shown once a grid has run a full day.</sub>

### HYPE flywheel

50% of each day's realized grid net is used to buy HYPE spot. Unrealized never counts; HYPE is never sold.

| HYPE stack | Cost | P/L | USDC | Treasury¹ |
|--:|--:|--:|--:|--:|
| 2.0187 HYPE | $168.82 | −$18.08 | $0.00 | **$150.74** |

<sub>¹ Treasury = HYPE stack + USDC. USDC is the other 50% of realized grid net, toben's to withdraw or add to the allocation.</sub>

<sub>Day 15 | $HYPE flywheel: 2.0187 HYPE worth $150.74 (−$18.08); yesterday the grids realized $-0.90, 50% = $0.00, no buy, pot $2.17 carried</sub>

<sub>Updated 10 Nov 2026 09:32 SGT · data from the Hyperliquid info API · realized net = reconciled grid round trips − fees + funding · APR = net PnL / margin budget × 365 / days, simple, non-compounding · not financial advice</sub>
<!-- desk-stats:end -->

## How the desk runs

- **Grid strategy.** Each market gets a fixed price range split into levels. The bot buys dips and sells rips inside the range, and every completed round trip books a small realized gain.
- **Risk lives in the grid stops.** Every grid has isolated margin, fixed leverage and a hard stop outside its range. No discretionary overrides.
- **Hourly health + reconcile.** Every hour the desk checks margin, liquidation distance and open orders, and reconciles the bot ledger against Hyperliquid fills.
- **Daily trader's read.** At 09:00 SGT the desk posts a short read, refreshes these stats and runs the HYPE flywheel buy.
- **Fees are real cost.** No churn for its own sake.

```mermaid
flowchart LR
    A[Grid bots on Hyperliquid] --> B[Fills + funding<br/>Hyperliquid info API]
    B --> C[Hourly health check<br/>+ reconcile]
    B --> D[Daily 09:00 SGT<br/>realized net]
    D --> E[50% to HYPE flywheel]
    D --> F[This README]
    C --> G[Alerts / fixes via PRs]
```

<div align="center"><sub>Grids run on <a href="https://github.com/tobenwarrior/y-terminal">y-terminal</a> · not financial advice</sub></div>
