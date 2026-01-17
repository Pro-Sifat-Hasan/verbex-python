# Contributing

Thanks for helping improve the Verbex SDK. We welcome issues, bug reports, and pull requests.

## Reporting issues

When opening an issue, please include:

- What you expected to happen
- What actually happened
- Steps to reproduce
- Your environment (OS, Python version, `uv` version if used)
- Any relevant logs or screenshots

## Development setup

```bash
uv venv --python 3.14
uv sync --extra dev
```

## Running checks

```bash
uv run pytest
uv run ruff format .
uv run ruff check .
uv run ty check .
```

## Pull request checklist

- Clear description of the change
- Tests added or updated if needed
- `pytest`, `ruff`, and `ty` checks pass
- Documentation updated when behavior changes

## Code of conduct

Be respectful, constructive, and collaborative. We aim to keep this project friendly and professional.
