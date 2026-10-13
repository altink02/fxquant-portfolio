# FXQuant — Engineering evidence and development status

**Altin Kalludra** · [Overview](README.md) · [Visual walkthrough](WALKTHROUGH.md)

Portfolio review: **2026-10-13**. This page summarizes records and selected
implementation files in the private repository. It does not claim that the
private application was built, tested, compiled, or run during this portfolio
editing session. No private implementation or raw internal audit is published.

## Verification record

| Record | Reported result | Scope and interpretation |
|---|---|---|
| Consolidated engineering review dated 2026-10-09 | 2,107 tests: 2,105 passed, 0 failures/errors, 2 skipped | Historical full-suite result; optional live exchange-provider tests were skipped |
| Same review, API suite | 84 tests, 0 failures/errors/skips | In-process stop, session permission, and risk-report integration |
| Same review, focused safety set | 226 tests, 0 failures/errors/skips | Risk, paper execution, drawdown boundaries, EA safety, and cost/timing consistency |
| Same review, quality checks | Backend formatting/lint and selected frontend type/lint checks reported clean | Recorded checks for that review state |
| Later Ultimate test report | Focused suites cover rollover, concurrency, manual ownership, chart levels, and the canonical EA | Later checks are separate from the earlier full-suite total; no combined current total is claimed |
| Ultimate static MQL5 check | Canonical EA reported clean with include resolution | Static lint is not MetaEditor compilation |
| Desktop MetaEditor and Strategy Tester | Not verified for the canonical Ultimate EA in the reviewed record | No independent Python-to-MT5 fill-parity claim |
| TradingView Pine compilation | Not verified in the reviewed record | Source/static alignment alone is insufficient |

The old “1,637 passing” badge has been removed because it mixed an older count
with an undated current-pass claim.

## Newer XAUUSD and MetaTrader work

| Area | What exists in the private project | Verification boundary |
|---|---|---|
| MT5 data adapter | Broker quotes/history and read-side account, position, and order inspection | Python order placement, cancellation, and modification are refused |
| Canonical gold EA | Modular settings, broker metadata, market contexts, signals, risk, execution, manual assistance, and dashboard | Source-level implementation; desktop compile/tester proof pending |
| Operating modes | Advisory, manual-assist, demo automation, and separately gated live mode | Portfolio use remains research/demo; live readiness is not claimed |
| Manual-trade assistance | Ownership by magic identifier, trade detection, realized P&L including costs, and pre-trade preview | Focused tests recorded; not a fresh desktop demo |
| Chart plan | Support/resistance zones and preview-versus-executed distinction | Source checks cover closed-bar pivots and zone confirmation |
| Risk state | Canonical EA includes persisted state; later Python tests cover daily/weekly rollover and concurrency | Python restart/cross-process halt durability is still a separate blocker |
| Pine companion | Signal/table alignment and static checking work | TradingView compilation and end-to-end alignment still need verification |

## A useful debugging case

An emergency-stop review found that paper execution could report a position as
closed even when the risk gate had rejected the reduction. The correction reports
a blocked exit with its reason. Other fixes connected dashboard/report/session
permission displays to the effective halt state.

Tests then exercised actual fills before the stop and verified that new
submissions were blocked after it across active and newly created sessions.
Later concurrency checks deliberately neutralized locking and detected
inconsistent snapshots. This is stronger evidence than merely testing that a
button changes its label.

## Current boundaries

- The Python API still needs authentication before remote exposure.
- Python halt state needs durability and synchronization across processes.
- A flatten request can remain pending; it does not guarantee immediate liquidation.
- The canonical EA still needs desktop compilation, a Strategy Tester trade export,
  and independent comparison with Python.
- No strategy has demonstrated a positive, cost-adjusted, out-of-sample edge in
  the reviewed Ultimate validation record.
- Existing screenshots are earlier interface captures. Synthetic inputs, empty
  setup views, and older availability labels are identified in the walkthrough.
- The public repository is a visual case study, not an interactive trading service.

## Evidence provenance

This summary was prepared from the private consolidated review dated
2026-10-09, the Ultimate implementation/test/strategy-validation records, the
Ultimate user guide, and the MT5 adapter's implemented read/write boundary.
These internal records are not linked as public downloads because they contain
private project detail. Selected assertions should be reproduced against the
private implementation before any production-readiness claim.

[Architecture](ARCHITECTURE.md) · [More projects](PORTFOLIO.md)

© Altin Kalludra. All rights reserved.
