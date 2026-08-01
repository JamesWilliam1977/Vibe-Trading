---
name: add-new-backtest-engine
description: Workflow command scaffold for add-new-backtest-engine in Vibe-Trading.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-new-backtest-engine

Use this workflow when working on **add-new-backtest-engine** in `Vibe-Trading`.

## Goal

Adds a new market or asset class backtest engine, enabling simulation of new trading environments (e.g., ChinaA, Crypto, GlobalEquity, ChinaFutures, Forex, Composite, etc).

## Common Files

- `agent/backtest/engines/*.py`
- `agent/backtest/engines/__init__.py`
- `agent/backtest/runner.py`
- `agent/backtest/models.py`
- `agent/backtest/metrics.py`
- `agent/tests/test_*engine.py`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create or update engine file in agent/backtest/engines/ (e.g., china_a.py, crypto.py, forex.py, composite.py)
- Update agent/backtest/engines/__init__.py to register the new engine
- Update agent/backtest/runner.py to route to the correct engine based on market detection
- Update or create models and metrics if new data structures or calculations are needed (agent/backtest/models.py, agent/backtest/metrics.py)
- Add or update tests for the new engine in agent/tests/

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.