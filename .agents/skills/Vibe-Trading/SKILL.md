```markdown
# Vibe-Trading Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches the core development patterns, coding conventions, and collaborative workflows used in the Vibe-Trading repository. Vibe-Trading is a Python-based trading agent platform built on Flask, supporting extensible backtesting, data loading, skill modules, and a modern frontend. The repository emphasizes modularity, clear contribution workflows, and internationalized documentation.

## Coding Conventions

- **File Naming:**  
  Use `snake_case` for Python files and directories.
  ```
  agent/backtest/engines/china_a.py
  agent/backtest/loaders/akshare_loader.py
  ```

- **Import Style:**  
  Prefer alias imports for clarity and brevity.
  ```python
  import pandas as pd
  import numpy as np
  from agent.backtest.engines import china_a as ca_engine
  ```

- **Export Style:**  
  Use named exports (explicitly define what is exported).
  ```python
  # In agent/backtest/engines/china_a.py
  class ChinaABacktestEngine:
      ...

  __all__ = ["ChinaABacktestEngine"]
  ```

- **Commit Messages:**  
  Follow [Conventional Commits](https://www.conventionalcommits.org/) with prefixes: `fix`, `docs`, `feat`, `test`.
  ```
  feat: add composite backtest engine for multi-asset support
  fix: correct forex loader fallback logic
  docs: update SKILL.md for ml-strategy
  test: add regression tests for crypto engine
  ```

## Workflows

### Add New Backtest Engine
**Trigger:** When supporting backtesting for a new market or asset class  
**Command:** `/add-backtest-engine`

1. Create or update the engine file in `agent/backtest/engines/` (e.g., `china_a.py`, `crypto.py`).
2. Register the new engine in `agent/backtest/engines/__init__.py`.
3. Update `agent/backtest/runner.py` to route based on market detection.
4. If needed, update or create models/metrics in `agent/backtest/models.py` and `agent/backtest/metrics.py`.
5. Add or update tests for the new engine in `agent/tests/`.
6. Document the new engine in `README.md` and relevant `SKILL.md` files.

**Example:**
```python
# agent/backtest/engines/crypto.py
class CryptoBacktestEngine:
    ...
```
```python
# agent/backtest/engines/__init__.py
from .crypto import CryptoBacktestEngine
```

---

### Add or Update Skill
**Trigger:** When introducing or updating an analytical, trading, or export capability  
**Command:** `/add-skill`

1. Create or update `SKILL.md` in `agent/src/skills/<skill-name>/`.
2. Add example code/supporting files in the skill directory as needed.
3. Register or categorize the skill in `agent/src/agent/skills.py`.
4. Update `README.md` and all translations to reflect the new skill.
5. Add or update tests for the skill in `agent/tests/`.

---

### Add or Update Data Loader
**Trigger:** When supporting a new data provider or improving data source reliability  
**Command:** `/add-data-loader`

1. Create or update loader file in `agent/backtest/loaders/` (e.g., `akshare_loader.py`).
2. Register the loader and define fallback chains in `agent/backtest/loaders/registry.py`.
3. Update `agent/backtest/runner.py` to use the new loader or fallback logic.
4. Update or add `SKILL.md` for the data source.
5. Document the new data source in `README.md`.
6. Add or update tests for the loader in `agent/tests/`.

---

### Add API Endpoint or CLI Command
**Trigger:** When exposing a new feature via API or CLI  
**Command:** `/add-api-endpoint`

1. Add or update handler in `agent/api_server.py` or `agent/cli.py`.
2. Update `frontend/src/lib/api.ts` and/or relevant frontend components if needed.
3. Update `README.md` and all translations to document the new endpoint/command.
4. Add or update tests in `agent/tests/`.

---

### Add or Update Frontend Feature
**Trigger:** When exposing new backend features or improving web UI  
**Command:** `/add-frontend-feature`

1. Add or update React components in `frontend/src/components/` or `frontend/src/pages/`.
2. Update `frontend/src/lib/api.ts` for new API calls.
3. Update i18n files if new text is introduced.
4. Update `README.md` and translations to reflect UI changes.
5. Update `vite.config.ts` if new proxy routes are needed.

---

### Add or Update Tests and CI
**Trigger:** When adding features, fixing bugs, or improving test coverage  
**Command:** `/add-test`

1. Add or update test files in `agent/tests/`.
2. Update `.github/workflows/test.yml` for CI integration if needed.
3. Update `pyproject.toml` with new test dependencies/config.
4. Update `.gitignore` to exclude test artifacts if necessary.

---

### Update README and Translations
**Trigger:** When shipping new features, skills, or updating documentation/news  
**Command:** `/update-readme`

1. Update `README.md` with new entries, skill/tool counts, or documentation.
2. Update all translation files (`README_zh.md`, `README_ja.md`, `README_ko.md`, `README_ar.md`).
3. Optionally update contributor or roadmap sections.

---

### Add or Update GitHub Templates and Policies
**Trigger:** When improving contributor experience or project governance  
**Command:** `/add-github-policy`

1. Add or update files in `.github/` (issue templates, PR templates, workflows).
2. Add or update `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`.
3. Update `README.md` to reference new or updated policies.

---

## Testing Patterns

- **Framework:** Not explicitly detected, but Python tests are in `agent/tests/`.
- **File Pattern:** Python test files use the pattern `test_*.py`.  
  (Note: Some frontend tests may use `*.test.ts` for TypeScript.)

**Example:**
```python
# agent/tests/test_crypto_engine.py
import pytest
from agent.backtest.engines.crypto import CryptoBacktestEngine

def test_crypto_backtest_basic():
    engine = CryptoBacktestEngine()
    result = engine.run(...)
    assert result.success
```

## Commands

| Command               | Purpose                                                      |
|-----------------------|--------------------------------------------------------------|
| /add-backtest-engine  | Add a new market or asset class backtest engine              |
| /add-skill            | Add or update an agent skill                                 |
| /add-data-loader      | Add or update a data loader for new data sources             |
| /add-api-endpoint     | Add a new API endpoint or CLI command                        |
| /add-frontend-feature | Add or update a frontend feature or panel                    |
| /add-test             | Add or update tests and CI integration                       |
| /update-readme        | Update README and all translation files                      |
| /add-github-policy    | Add or update GitHub templates, contributing, or policies    |
```
