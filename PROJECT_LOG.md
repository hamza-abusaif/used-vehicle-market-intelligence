# Project Log

## September 20, 2026

### Completed
- Created the project directory.
- Created the initial folder structure.
- Created the GitHub repository.
- Initialized Git version control.

### Decisions
- Python will be used for data analysis and machine learning.
- Original datasets will remain unchanged inside `data/raw/`.
- Project development will be tracked through Git commits.

### Next
- Set up the Python environment.
- Select the dataset.
- Perform the initial data audit.

### Environment Setup
- Installed Python.
- Created a project-specific virtual environment.
- Installed pandas, NumPy, Matplotlib, Seaborn, scikit-learn, and Jupyter.
- Created `requirements.txt`.
- Created the first notebook: `01_data_audit.ipynb`.

### Learned
- A virtual environment keeps packages isolated for one project.
- `.gitignore` prevents local files such as `.venv/` from being tracked.
- `requirements.txt` records the packages needed to reproduce the project.

### Next
- Select and download the used vehicle dataset.
- Place the original dataset in `data/raw/`.
- Begin the initial data audit.

## September 29, 2026

### Completed
- Successfully loaded the raw vehicle sales dataset into pandas.
- Confirmed the dataset contains 558,837 rows and 16 columns.
- Reviewed column names and data types.
- Examined missing values.
- Checked for exact duplicate rows and found none.
- Generated descriptive statistics for numeric variables.
- Investigated the vehicle condition scoring system.
- Investigated unusually low selling prices.
- Investigated extreme odometer values.

### Key Findings
- Transmission has 65,352 missing values, the largest amount among the variables.
- The condition column uses mixed numeric formatting. Whole grades are stored as values such as 1, 2, 3, 4, and 5, while decimal grades appear as values such as 21, 35, and 49.
- 72 records contain an odometer value of exactly 999,999 miles.
- The repeated 999,999 value appears suspicious because almost all other mileage values above 500,000 occur only once or twice.
- Several vehicles have recorded selling prices of $1 despite having much higher MMR values.
- No cleaning changes have been made to the raw dataset.

### Learned
- `head()` displays the first rows of the current object.
- `shape` returns the number of rows and columns.
- `info()` summarizes data types and non-missing values.
- `isna().sum()` counts missing values.
- `value_counts()` counts how frequently each unique value occurs.
- The order of pandas operations matters. For example, sorting before `head()` produces a different result from applying `head()` before sorting.
- Suspicious values should be investigated before removing or modifying them.

### Next
- Continue investigating suspicious values.
- Determine appropriate cleaning rules for condition, odometer, and selling price.
- Examine categorical inconsistencies such as capitalization in make/model names.
- Begin creating the processed dataset.