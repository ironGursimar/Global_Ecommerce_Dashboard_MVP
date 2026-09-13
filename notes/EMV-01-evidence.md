# EMV-01 evidence: Set up the project folders

## What was created

The initial Ecommerce MVP base was created in commit `c633163` as a lightweight
Python project skeleton. Git-tracked placeholder files keep otherwise-empty
folders in the repository, while the data folders also contain short usage
README files:

- `data/raw/` — source exports; raw files are not edited in place.
- `data/clean/` — generated, validated analysis-ready data.
- `data/database/` — generated SQLite database files.
- `notebooks/` — exploratory analysis and experiments.
- `src/` — reusable data, feature, model, and database code.
- `tests/` — automated tests and validation checks.
- `docs/` — project documentation.
- `models/` — model artifacts and evaluation results.
- `dashboard/` — Streamlit dashboard code.
- `chatbot/` — natural-language-to-safe-SQL chatbot code.

The base was made without application code or runtime data: `.gitkeep` files
preserve the empty code, documentation, model, dashboard, chatbot, notebook,
and test directories; the three data directories use their README files as
their initial tracked content. `README.md` records the layout and intended
workflow, and `requirements.txt` is reserved for dependencies added by later
stories. `.gitignore` excludes local environments, secrets, generated
databases, and generated model artifacts.

## Acceptance criteria and evidence

| Acceptance criterion | Evidence |
| --- | --- |
| A repository-level project base exists | `README.md`, `requirements.txt`, `.gitignore` |
| Raw, clean, and database data locations exist | `data/raw/README.md`, `data/clean/README.md`, `data/database/README.md` |
| Dedicated locations exist for notebooks, source, tests, docs, models, dashboard, and chatbot work | `notebooks/.gitkeep`, `src/.gitkeep`, `tests/.gitkeep`, `docs/.gitkeep`, `models/.gitkeep`, `dashboard/.gitkeep`, `chatbot/.gitkeep` |
| The initial structure and workflow are documented | `README.md` sections “Repository layout” and “Planned workflow” |
| Empty/generated content will not be accidentally committed | `.gitignore` rules for environments, secrets, SQLite files, and model artifacts |

## Reproducible verification

Run these commands from the repository root in PowerShell:

```powershell
git ls-files data/raw data/clean data/database notebooks src tests docs models dashboard chatbot
```

Expected output includes one tracked file for each required directory:
`data/raw/README.md`, `data/clean/README.md`,
`data/database/README.md`, and `.gitkeep` entries under
`notebooks`, `src`, `tests`, `docs`, `models`, `dashboard`, and `chatbot`.

```powershell
$required = @(
  'data/raw', 'data/clean', 'data/database', 'notebooks', 'src', 'tests',
  'docs', 'models', 'dashboard', 'chatbot'
)
$required | Where-Object { -not (Test-Path -LiteralPath $_ -PathType Container) }
```

Expected output: no output, meaning every required directory exists.

```powershell
git check-ignore data/example.sqlite models/example.joblib .env
```

Expected output:

```text
data/example.sqlite
models/example.joblib
.env
```

## Completed evidence versus future work

**Completed:** the folder scaffold, tracked placeholders, data-folder guidance,
repository layout documentation, and ignore rules described above are present.

**Future work:** adding source data, cleaning and validation pipelines, a
SQLite database, notebooks, reusable source code, tests, trained models,
dashboard pages, chatbot behavior, and their dependencies. Those are not
claimed by EMV-01 and should be evidenced by their respective backlog stories.
