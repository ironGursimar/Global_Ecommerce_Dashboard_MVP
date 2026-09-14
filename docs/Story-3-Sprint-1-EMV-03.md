# Story 3 - Sprint 1
## EMV-03: Clean the data and make it ready to use

## What this story is about

Story 2 told us what is wrong with the files. In this story, I will make clean
copies of the data. I will not change the original files in `data/raw/`.

The cleaned files will go in `data/clean/`.

## Steps i will do

### 1. Put the files in the right place

Put these files in `data/raw/`:

`customers.csv`, `sessions.csv`, `transactions.csv`, `train.csv`, `test.csv`,
`sample_submission.csv`, `marketing_campaigns.csv`, and `geo_data.csv`.

First, keep a copy of the original files. Do not edit them directly.

### 2. Check the columns and types

Read every file and write down:

- column name
- what the column means
- the type it should have
- whether it is allowed to be blank

IDs should stay as IDs. Dates should become date values. Counts should become
whole numbers. Rates and scores should become numbers.

### 3. Fix blank email rates

`customers.email_open_rate` has 22,746 blank values.

I will:

1. check how many blanks there are again
2. add a flag like `email_open_rate_missing`
3. fill the blank rates using a value decided from the customer data, such as
   the median
4. write down the rule used

I will not quietly replace the blanks without recording it.

### 4. Make labels consistent

I will use one format for values that mean the same thing:

- `US`, `USA`, and `U.S.` become one country value
- `usa` and `uk` are changed to the same uppercase format
- traffic sources use one case
- device names use one case
- `0`, `1`, `TRUE`, `FALSE`, `Yes`, and `No` become one true/false format

I will check the unique values again after this step.

### 5. Turn money text into numbers

I will clean these columns:

- `customers.credit_limit`
- `transactions.order_value`
- `marketing_campaigns.campaign_budget`

I will remove `$` and commas, then save them as numeric columns. I will check
that no money value became blank by mistake.

### 6. Check strange values before deciding what to do

I will not delete strange values without checking them first.

- `avg_review_score` has values above 5. I will check the rows and decide
  whether these should be capped, corrected, or marked as invalid.
- `session_duration` has very large values. I will confirm the unit and decide
  how to handle the extreme values.
- `order_value` and `items_count` can be zero. I will check if these are real
  free/failed orders before removing anything.

Every decision will be written in a small cleaning log.

### 7. Deal with the noise columns

I will list all `noise_*` columns. I will leave them out of the modelling data
unless there is a clear reason to keep them. I will record which columns were
removed and why.

### 8. Keep the files connected

After cleaning, I will check that:

- every session customer still exists in `customers`
- every transaction customer still exists in `customers`
- every session campaign still exists in `marketing_campaigns`
- every session region still exists in `geo_data`
- train and test customers do not overlap
- the sample submission still matches the test customers

### 9. Save the clean files

Save the cleaned copies in `data/clean/` with clear names. For example:

- `customers_clean.csv`
- `sessions_clean.csv`
- `transactions_clean.csv`
- `train_clean.csv`
- `test_clean.csv`
- `marketing_campaigns_clean.csv`
- `geo_data_clean.csv`

Keep the target column in the training file. Do not add the target to the test
file.

### 10. Check the result again

Before calling the cleaning finished, check:

- missing values
- duplicate rows
- column types
- date values
- number ranges
- category values
- linked IDs
- train/test overlap
- target balance

The final check should show what was fixed and what was kept as a warning.

## What should be delivered

This story is complete when I have:

- clean copies in `data/clean/`
- a short cleaning log
- a simple data dictionary
- before-and-after row and column counts
- a final check showing that the clean files are usable

## Done now and future work

**Done now:** the cleaning steps are written from the real problems found in
Story 2.

**Future work:** add the archive files to `data/raw/`, run these steps, make the
clean files, and record the final results. No raw file has been changed yet.
