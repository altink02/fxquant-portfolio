# FXQuant — Visual walkthrough

**Altin Kalludra** · [Project overview](README.md) · [Architecture](ARCHITECTURE.md) · [Engineering evidence](EVIDENCE.md)

This is a public, screenshot-based product tour. The ten images are existing,
unaltered captures from an earlier FXQuant development build. The System Health
capture displays a 2026-09-22 runtime date; the other capture dates are not
independently recorded. Several screens contain synthetic data, empty setup
states, or older phase messages. None represents a live trading account.

The sequence below follows a practical workflow: inspect permissions and data,
form a hypothesis, test it, apply risk checks, then explore EA export and paper
simulation. Click an image to inspect it at its original size.

## Tour map

| Step | Screen | Focus |
|---|---|---|
| 1 | [Dashboard and permissions](#1-dashboard-and-permissions) | dashboard |
| 2 | [Market-data lake](#2-marketdata-lake) | data |
| 3 | [Instrument metadata](#3-instrument-metadata) | markets |
| 4 | [Cross-instrument scanner](#4-crossinstrument-scanner) | scanner |
| 5 | [Strategy registry](#5-strategy-registry) | strategies |
| 6 | [Research and validation controls](#6-research-and-validation-controls) | strategy-lab |
| 7 | [Risk gate and emergency controls](#7-risk-gate-and-emergency-controls) | risk |
| 8 | [EA export and model equivalence](#8-ea-export-and-model-equivalence) | ea-generator |
| 9 | [Paper-session setup](#9-papersession-setup) | paper |
| 10 | [Runtime health and capability reporting](#10-runtime-health-and-capability-reporting) | health |

## 1. Dashboard and permissions

[![Dashboard and permissions — archived FXQuant interface capture](screenshots/01-dashboard.png)](screenshots/01-dashboard.png)

**What you see:** Start by checking the operating mode, separate paper/live panels, drawdown tiers, and component health. This capture says RESEARCH and LIVE OFF. Its paper-availability text predates newer paper-session work.

**Why it matters:** Clear operating permissions and honest missing values help the operator understand what the platform can actually do.

## 2. Market-data lake

[![Market-data lake — archived FXQuant interface capture](screenshots/06-data.png)](screenshots/06-data.png)

**What you see:** Inspect dataset inventory, bar ranges, partition counts, and quality rules. The capture shows ten stored datasets and 70,976 bars; these are capture-time inventory figures.

**Why it matters:** Parquet storage and DuckDB queries make the research input inspectable. UTC storage and explicit timezone handling reduce silent alignment errors.

## 3. Instrument metadata

[![Instrument metadata — archived FXQuant interface capture](screenshots/07-markets.png)](screenshots/07-markets.png)

**What you see:** Review tick size, quantity steps, minimum order sizes, and instrument capabilities. The green tradable flags describe instrument metadata, not permission to trade in RESEARCH mode.

**Why it matters:** Broker constraints affect rounding and sizing; they belong in the instrument model rather than in UI-only labels.

## 4. Cross-instrument scanner

[![Cross-instrument scanner — archived FXQuant interface capture](screenshots/04-scanner.png)](screenshots/04-scanner.png)

**What you see:** Compare trend efficiency, normalized volatility, quality, and data provenance. This capture marks its ranked inputs SYNTHETIC; these ranks are demonstration inputs, not actionable signals.

**Why it matters:** Data provenance travels with the ranking so simulated inputs cannot be mistaken for live market evidence.

## 5. Strategy registry

[![Strategy registry — archived FXQuant interface capture](screenshots/02-strategies.png)](screenshots/02-strategies.png)

**What you see:** Inspect strategy family, version, regime restrictions, and experiment status. The library includes buy-and-hold and no-trade controls.

**Why it matters:** A hypothesis must be compared with controls, and restricted strategy families remain visible rather than silently disappearing.

## 6. Research and validation controls

[![Research and validation controls — archived FXQuant interface capture](screenshots/03-strategy-lab.png)](screenshots/03-strategy-lab.png)

**What you see:** Select the instrument, timeframe, costs, and parameters, then choose backtest, walk-forward, Monte Carlo, or leakage scan. This image shows configuration before a run, not a completed backtest.

**Why it matters:** Cost assumptions are explicit. Confirmed-bar decisions and conservative intrabar handling make replay assumptions reviewable.

## 7. Risk gate and emergency controls

[![Risk gate and emergency controls — archived FXQuant interface capture](screenshots/05-risk.png)](screenshots/05-risk.png)

**What you see:** Inspect exposure caps, loss limits, sizing rules, spread and quote-age gates, and the emergency-stop interface. This is an older capture; its phase note is superseded by later in-process paper-stop integration.

**Why it matters:** The current private tests exercise real pre-halt fills and blocked post-halt submissions. Restart durability and cross-process control remain open gaps.

## 8. EA export and model equivalence

[![EA export and model equivalence — archived FXQuant interface capture](screenshots/08-ea-generator.png)](screenshots/08-ea-generator.png)

**What you see:** Inspect supported strategy translations, fidelity warnings, and the minimum validation status. The visible refusal is intentional: the selected strategy is still an experiment.

**Why it matters:** A refused export is a useful result. Model-level condition checks are separate from independent MetaTrader compilation and fill parity.

## 9. Paper-session setup

[![Paper-session setup — archived FXQuant interface capture](screenshots/09-paper.png)](screenshots/09-paper.png)

**What you see:** Configure a strategy, symbols, timeframe, warm-up, starting equity, and reconciliation interval. No session has been started in this screenshot.

**Why it matters:** Paper sessions reuse the risk and execution machinery with a simulated venue. This empty setup view is not evidence of realized profit or live execution.

## 10. Runtime health and capability reporting

[![Runtime health and capability reporting — archived FXQuant interface capture](screenshots/10-health.png)](screenshots/10-health.png)

**What you see:** Inspect component health, environment, operating mode, and engine capability details. The capture marks PostgreSQL UNKNOWN and overall health DEGRADED.

**Why it matters:** Missing infrastructure is reported rather than painted green. The earlier LEAN panel includes a NOT IMPLEMENTED description; its AVAILABLE label is not a claim that the integration works.

## Newer work not pictured here

The private project also contains the canonical XAUUSD EA, manual-trade assistance,
chart level/plan rendering, and Pine alignment work. These ten captures do not
show that newer MetaTrader interface. No new desktop capture is available in this
workspace, so none is represented by a fabricated image.

Read the [engineering evidence](EVIDENCE.md) for the source-level work and its
verification limits. The public repository provides documentation and screenshots;
it does not distribute Python, MQL5, Pine, or application source.

[Back to project overview](README.md) · [More projects and CV](PORTFOLIO.md)

© Altin Kalludra. All rights reserved.
