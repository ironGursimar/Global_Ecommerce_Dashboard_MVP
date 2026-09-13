# Story 2 - Sprint 1
## EMV-02: Check what is wrong with the raw files

## What this story is for

I need to know what is wrong with the original data before I clean it. I will
check the raw files first and keep the original files unchanged.

## What i know right now

There are no raw CSV or data files in `data/raw/` yet. The folder only has:

- `data/raw/README.md` - a note telling us to put original exports here.

So there are no real problems to report yet. Missing values, wrong types,
duplicates, bad dates, bad numbers, and outliers cannot be checked until the
raw files are added.

## Checks i need to do

For every file added to `data/raw/`, I will record:

| Check | What i am looking for |
| --- | --- |
| File and column list | The files and fields that are actually present |
| Row count | Empty files or files with unexpectedly few rows |
| Column names | Spelling problems, duplicate names, and unclear names |
| Missing values | Blank cells and how many there are in each field |
| Duplicate rows | Exact duplicate records and repeated business IDs |
| Data types | Numbers stored as text, mixed types, and boolean values written in different ways |
| Dates | Invalid dates, mixed formats, and dates outside the expected period |
| Numbers | Currency symbols, commas, negative values, impossible values, and extreme values |
| Categories | Different spellings or case for the same value |
| Relationships | Broken customer, order, product, or other IDs |
| Target field | Missing or inconsistent purchase/target values |
| Sensitive data | Personal fields that should not be used or exposed |

## What the final result should say

The completed check will have a small table for each raw file showing:

- file name and row/column count
- columns with missing values
- duplicate count
- wrong or mixed data types
- invalid dates and values
- category values that need standardising
- IDs or links that do not match
- the cleaning action needed for each problem

I will not silently fix anything in the raw folder. The cleaned version will go
to `data/clean/`, and the original raw file will stay unchanged.

## How to check the folder now

Run this from the repository root in PowerShell:

```powershell
Get-ChildItem data/raw -File
```

Expected right now:

```text
README.md
```

After raw files are added, run:

```powershell
Get-ChildItem data/raw -File | Select-Object Name, Length, LastWriteTime
```

Expected: a list of the original files, with their sizes and dates. A data
profile must then be run on each CSV before any cleaning starts.

## Done now and future work

**Done now:** the raw folder was checked and the current situation is written
down honestly. There are no raw data problems to report because no raw data has
been added yet.

**Future work:** add the original exports, run all checks above, save the
findings, and then make the cleaned files in `data/clean/`.
