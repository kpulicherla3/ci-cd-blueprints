# ci-cd-blueprints

This repository contains a focused, production-style project demonstrating practical skills in data engineering, analytics, and platform engineering.

## Scope
- Clear project structure
- Emphasis on correctness and maintainability
- Incremental improvements tracked via pull requests

## How to use
See project-specific documentation in the `docs/` directory or repository root.

## Status
Active development.

## Reusable Python CI workflow template
This repository now provides a reusable Python CI template in:

- `.github/workflows/ci.yml`

It supports direct execution on `push`/`pull_request` and reusable usage via `workflow_call`.

Example usage from another workflow:

```yaml
name: python-ci

on:
  pull_request:
  push:
    branches: [master]

jobs:
  ci:
    uses: ./.github/workflows/ci.yml
    with:
      python-version: "3.12"
      install-command: "python -m pip install -r requirements.txt"
      lint-command: "python -m pip install ruff && ruff check ."
      test-command: "python -m pip install pytest && pytest -q"
      run-lint: true
      run-tests: true
```
