# Energy Consumption Dataset — Data Cleaning

## Project overview
This project prepares an energy-consumption dataset for analysis using Python and Pandas. It checks missing values, duplicate records, data types, and inconsistent values.

## Dataset
- Records: 1,000
- Columns: 11
- Subject: Energy consumption and building/environmental characteristics
- Original file: `dataset/raw_dataset.csv`

## Data-quality findings
| Check | Initial result | Action |
|---|---:|---|
| Missing values | 0 | No imputation required |
| Duplicate full rows | 0 | No rows removed |
| Timestamp data type | `object` (text) | Converted to datetime |
| Timestamp parsing failures | 0 | All timestamps parsed |
| Duplicate timestamps | 0 | No timestamp duplicates |
| Day-of-week mismatches | 879 | Recalculated from Timestamp |
| Negative numeric values | 0 | No correction required |
| Categorical whitespace | 0 in inspected categories | Standardized text consistently |

## Cleaning performed
1. Parsed `Timestamp` using the source format `%d-%m-%Y %H:%M`.
2. Standardized categorical text fields by trimming whitespace and applying title case.
3. Recalculated `DayOfWeek` from `Timestamp`. This was necessary because 879 of the original weekday labels did not agree with the date.
4. Converted measurement columns to numeric types.
5. Rechecked missing values, duplicate rows, weekday consistency, and negative numeric values.

**Important assumption:** `Timestamp` is treated as the source of truth for the weekday. If the dataset owner intended `DayOfWeek` to represent a different business calendar, confirm that before using the corrected column.

## Output
- `dataset/raw_dataset.csv` — unchanged source data
- `dataset/cleaned_dataset.csv` — cleaned data
- `data_cleaning.ipynb` — reproducible cleaning notebook

## Tools
- Python
- Pandas
- NumPy
- Jupyter Notebook / Google Colab

## How to run
1. Download or clone this repository.
2. Open `data_cleaning.ipynb` in Jupyter or upload it to Google Colab.
3. Keep `raw_dataset.csv` inside the `dataset` folder, or upload the CSV when prompted.
4. Run the notebook cells from top to bottom.

## Validation
The cleaned output contains no missing values, no duplicate full rows, no weekday mismatches, and no negative numeric values in the inspected numeric columns.
