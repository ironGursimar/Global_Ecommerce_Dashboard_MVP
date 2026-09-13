# Story 1 - Sprint 1
## EMV-01: Set up the project folders

## What i made

I made the first basic folder setup for the Ecommerce MVP. The folders are
empty for now, but they are ready for the later work.

- `data/raw/` - source exports; raw files are not edited in place.
- `data/clean/` - generated, validated analysis-ready data.
- `data/database/` - generated SQLite database files.
- `notebooks/` - exploratory analysis and experiments.
- `src/` - reusable data, feature, model, and database code.
- `tests/` - automated tests and validation checks.
- `docs/` - project documentation.
- `models/` - model artifacts and evaluation results.
- `dashboard/` - Streamlit dashboard code.
- `chatbot/` - natural-language-to-safe-SQL chatbot code.

I used small `.gitkeep` files so Git keeps the empty folders. The three data
folders have small README files. I also added the main `README.md`,
`requirements.txt`, and `.gitignore`. No real data, app code, model, database,
or chatbot has been added yet.

## Acceptance criteria

| What was needed | Where the proof is |
| --- | --- |
| Main project base exists | `README.md`, `requirements.txt`, `.gitignore` |
| Raw, clean, and database folders exist | `data/raw/README.md`, `data/clean/README.md`, `data/database/README.md` |
| The other work folders exist | `.gitkeep` files in `notebooks`, `src`, `tests`, `docs`, `models`, `dashboard`, and `chatbot` |
| The setup and next steps are written down | `README.md` |
| Local and generated files are ignored | `.gitignore` |

## How to check it

Run these from the repo folder in PowerShell:

```powershell
git ls-files data/raw data/clean data/database notebooks src tests docs models dashboard chatbot
```

Expected: one tracked file is shown for each folder. The data folders show
their README files. The other folders show `.gitkeep`.

```powershell
$required = @(
  'data/raw', 'data/clean', 'data/database', 'notebooks', 'src', 'tests',
  'docs', 'models', 'dashboard', 'chatbot'
)
$required | Where-Object { -not (Test-Path -LiteralPath $_ -PathType Container) }
```

Expected: no output. That means all the folders exist.

```powershell
git check-ignore data/example.sqlite models/example.joblib .env
```

Expected:

```text
data/example.sqlite
models/example.joblib
.env
```

## Done now and future work

**Done now:** the folder setup, the small README files, the layout notes, and
the ignore rules are all in place.

**Future work:** adding data, cleaning it, making the SQLite database, writing
code and tests, training a model, and building the dashboard and chatbot.
Those belong to later stories, not this one.
