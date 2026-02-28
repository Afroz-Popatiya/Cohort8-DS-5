# Setup

## Creating Your Environment

1. **Create a virtual environment called `c8ds5-project-env`:**
```bash
   uv venv c8ds5-project-env --python 3.11
```

2. **Activate the environment:**
   - macOS/Linux:
```bash
     source c8ds5-project-env/bin/activate
```
   - Windows (Git Bash):
```bash
     source c8ds5-project-env/Scripts/activate
```

3. **Install all dependencies from `pyproject.toml`:**
```bash
   uv sync
```

## Using Your Environment

Your terminal prompt will show `(c8ds5-project-env) $` when active.

To activate later:
- macOS/Linux: `source c8ds5-project-env/bin/activate`
- Windows: `source c8ds5-project-env/Scripts/activate`

To deactivate: `deactivate`

## What Gets Created?
- `c8ds5-project-env/` — your isolated environment folder
- `uv.lock` — exact package versions (auto-generated, don't edit)
- `.gitignore` — should exclude `c8ds5-project-env/` and `__pycache__/`