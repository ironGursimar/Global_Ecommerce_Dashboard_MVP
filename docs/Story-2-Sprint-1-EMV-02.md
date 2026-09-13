# Story 2 - Sprint 1
## EMV-02: Check what is wrong with the raw files

## What i checked

I checked the dataset zip file before cleaning it. It has 8 CSV files:

- `customers.csv` - 200,000 rows and 17 columns
- `sessions.csv` - 2,000,000 rows and 11 columns
- `transactions.csv` - 500,000 rows and 11 columns
- `train.csv` - 160,000 rows and 2 columns
- `test.csv` - 40,000 rows and 1 column
- `sample_submission.csv` - 40,000 rows and 2 columns
- `marketing_campaigns.csv` - 200 rows and 6 columns
- `geo_data.csv` - 100 rows and 5 columns

The files can be put in `data/raw/`. I will keep those original files as they
are and make cleaned copies in `data/clean/`.

## What i found

### Missing values

- `customers.csv` has 22,746 blank values in `email_open_rate`.
- The other columns checked had no blank values.

### Values that are written in different ways

- `customers.country_code` uses `US`, `USA`, `U.S.`, `usa`, `DE`, `de`, `UK`,
  and `uk`. These need one standard format.
- `sessions.traffic_source` has `Ads`, `ads`, `Organic`, `organic`, and
  `SOCIAL`.
- `sessions.device_type` has `Desktop`, `desktop`, `Mobile`, `mobile`, and
  `TABLET`.
- `sessions.bounce_flag` uses `0`, `1`, `FALSE`, `TRUE`, `No`, and `Yes`.
- `transactions.discount_applied` uses `0`, `1`, `FALSE`, `TRUE`, `No`, and
  `Yes`.

### Text that should be numbers

- `customers.credit_limit` contains values like `$10,966`.
- `transactions.order_value` contains values like `$20.39`.
- `marketing_campaigns.campaign_budget` contains values like `$46,187`.
- These dollar signs and commas need to be removed before converting the
  columns to numbers.

### Values that need checking

- `customers.avg_review_score` goes as high as `6.39`, even though a normal
  five-star score should not be above `5`.
- `sessions.session_duration` goes as high as `82,433.88`. This needs an
  outlier check and a decision about the correct unit and maximum.
- `transactions` has `0` for `order_value` and `items_count`. These may be
  valid free/failed orders, or they may need to be removed or flagged.
- Several columns named `noise_*` are present. They should not be used unless
  there is a clear reason, because they look like added noise fields.

### Things that are okay so far

- The CSV rows had matching column counts. No malformed rows were found.
- No exact duplicate rows were found in the files checked.
- All session and transaction customer IDs matched `customers.csv`.
- All session campaign IDs matched `marketing_campaigns.csv`.
- All session region IDs matched `geo_data.csv`.
- `train.csv` and `test.csv` had no customer overlap.
- `sample_submission.csv` has the same customer IDs as `test.csv`.
- The training target has 127,514 zeros and 32,486 ones, so the target is
  imbalanced and this must be considered when training the model.

## What needs to be done

1. Copy the original CSV files into `data/raw/` without changing them.
2. Make a data dictionary with the column meaning and expected type.
3. Fill or safely flag the 22,746 missing `email_open_rate` values.
4. Standardise country, traffic source, device, and yes/no values.
5. Remove currency symbols and commas, then convert money fields to numbers.
6. Check the review scores above 5 and decide whether to cap, remove, or flag
   them.
7. Check the very long sessions and confirm the duration unit.
8. Decide how to handle zero-value orders and zero-item transactions.
9. Remove or justify the `noise_*` columns before modelling.
10. Save the cleaned files in `data/clean/` and write down every change.
11. Recheck IDs, dates, missing values, duplicates, and target balance after
    cleaning.

## Done now and future work

**Done now:** the raw archive was inspected and the actual problems are listed
above. The main problems are missing values, inconsistent labels, money stored
as text, suspicious ranges, and possible noise columns.

**Future work:** add the original files to `data/raw/`, perform the cleaning,
save the cleaned data, and run the checks again. No cleaning has been done yet.
