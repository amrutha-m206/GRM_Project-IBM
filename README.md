# New Tasks folder

## Task 1 - Remove duplicate course completions and keep latest record per learner

It performs the following steps:

- Loads the dataset into a pandas DataFrame.
- Converts the `Completion Date` column to proper datetime format, handling ISO timestamps , including UTC timezone.
- Converts UTC completion dates to Indian Standard Time (IST, UTC+05:30).
- Identifies duplicate course completions by the same learner (based on `Learner - ID` and `Learning activity - Title`).
- For duplicates, keeps only the latest completion record based on the converted completion date.

## Output

After processing, the final dataframe contains **one row per learner-course pair**, representing the **latest completion** record based on the completion date converted to IST timezone.

The dataFrame includes the following key columns:

- `Learner - ID`: Unique learner identifier.
- `Learner - Name`: Learner's name.
- `Learning activity - Title`: Course title.
- `Completion Date IST`: Completion date and time converted to Indian Standard Time (timezone-aware).

Duplicates of the same course completed multiple times by the same learner are removed, keeping only the most recent completion based on the IST-converted timestamp.

Rows with missing or unparseable completion dates (`NaT`) will be later inspected separately as they are excluded from the deduplication step.

---


