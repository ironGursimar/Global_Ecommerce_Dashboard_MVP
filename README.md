# Ecommerce MVP

Ecommerce customer purchase prediction, dashboard, and SQL chatbot project.

## Repository layout

- `data/raw/` — original source files; never edit these files.
- `data/clean/` — cleaned, analysis-ready data generated from `data/raw/`.
- `data/database/` — SQLite database files generated from clean data.
- `notebooks/` — exploratory analysis and experiments.
- `src/` — reusable data, feature, model, and database code.
- `tests/` — automated tests and validation checks.
- `docs/` — data dictionary, target definition, and project documentation.
- `models/` — trained model artifacts and evaluation results.
- `dashboard/` — Streamlit dashboard code.
- `chatbot/` — natural-language-to-safe-SQL chatbot code.

## Story EMV-01 status

The initial project folder structure is in place. Raw data, cleaned data, notebooks, source code, and the SQLite database each have a dedicated location.

## Planned workflow

1. Put source CSV files in `data/raw/`.
2. Clean and validate them into `data/clean/`.
3. Load the clean datasets into SQLite under `data/database/`.
4. Build features and models from the database through code in `src/`.
5. Serve the dashboard and chatbot from their dedicated folders.
