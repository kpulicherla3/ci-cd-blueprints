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

## Reusable Python CI workflow

This repository includes a reusable GitHub Actions workflow for Python projects:

- `.github/workflows/python-reusable-ci.yml`

### What it provides

- Configurable Python version
- Configurable install and test commands
- Optional working directory override
- Built-in pip caching

### How to use it from another workflow

Create a caller workflow (for example, `.github/workflows/python-ci.yml`) and invoke the reusable workflow:

name: python-ci
on:
  pull_request:
  push:
    branches: [master]
jobs:
  ci:
    uses: ./.github/workflows/python-reusable-ci.yml
    with:
      python-version: "3.11"
      install-command: "pip install -r requirements.txt"
      test-command: "pytest -q"
      working-directory: "."

If your project has different commands or structure, adjust the `with` values accordingly.
