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
     Fields: grid, direction, range, lev, position, realized net (closedPnl - fees + funding), unrealized, round trips, fees, funding, days, APR. -->
## Live desk stats

<p align="center">
<picture><img src="https://img.shields.io/badge/capital_managed-%242,141-0366d6?style=flat-square" alt="capital managed"></picture> <picture><img src="https://img.shields.io/badge/live_grids-3-2ea44f?style=flat-square" alt="live grids"></picture> <picture><img src="https://img.shields.io/badge/realized_net-%2B%2432.02-2ea44f?style=flat-square" alt="realized net"></picture> <picture><img src="https://img.shields.io/badge/unrealized-%2B%2419.62-informational?style=flat-square" alt="unrealized"></picture> <picture><img src="https://img.shields.io/badge/days_live-1.8-lightgrey?style=flat-square" alt="days live"></picture> <picture><img src="https://img.shields.io/badge/HYPE_stash-0.4098-8a2be2?style=flat-square" alt="HYPE stash"></picture>
</p>

**Capital managed:** allocated $2,141.47 · deployed $2,141.47 · grid equity $2,193.11 (allocated + realized + unrealized) · **+2.41%** on allocation

| Grid | Range | Position | Realized net | Unrealized | Round trips |
|---|---|---|--:|--:|--:|
| **XMR**<br><sub>long · 5x</sub> | 521.4–663.6 | 1.905 @ 595.795 | +$21.61 | +$12.52 | 18 |
| **NATGAS**<br><sub>neutral · 3x</sub> | 2.4152–3.4713 | flat | +$7.01 | +$0.00 | 2 |
| **SP500**<br><sub>long · 6x</sub> | 7596–7843.2 | 0.125 @ 7670.0 | +$3.39 | +$7.10 | 3 |
| **Total** | | margin $2141 | **+$32.02** | **+$19.62** | 23 |

Net (realized + unrealized): **+$51.64**

| Grid | Fees | Funding | Days | APR |
|---|--:|--:|--:|--:|
| XMR | $2.24 | −$1.79 | 1.8 | 797% |
| NATGAS | $0.02 | −$0.01 | 1.7 | 190% |
| SP500 | $0.14 | +$0.10 | 0.8 | n/a<sup>*</sup> |

<sub>* APR shown once a grid has run a full day.</sub>

### HYPE flywheel

50% of each day's realized grid net is used to buy HYPE spot. Unrealized never counts; HYPE is never sold.

| HYPE held | Cost | Avg price | Mark value | P/L |
|--:|--:|--:|--:|--:|
| 0.4098 | $32.59 | $79.52 | $33.29 | +$0.71 |

<sub>Day 2 | $HYPE flywheel: 0.4098 HYPE worth $33.29 (+$0.71); yesterday the grids realized $19.13, 50% = $9.57, bought 0.13 HYPE at $81.544</sub>

<sub>Updated 28 Oct 2026 11:15 SGT · data from the Hyperliquid info API · realized net = closedPnl − fees + funding · APR = net PnL / margin budget × 365 / days, simple, non-compounding · not financial advice</sub>
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
