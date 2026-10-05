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
- The repeated 999,999 value appears suspicious because almost all other mileage values above 500,000 occur only a few times.
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

## October 4, 2026

### Completed
- Continued the categorical data-quality audit.
- Reviewed common values for make, transmission, body style, and exterior color.
- Found capitalization inconsistencies in body styles such as `Sedan`/`sedan` and `SUV`/`suv`.
- Found 26 records where the transmission field contains `Sedan` or `sedan`.
- Found 26 records where the color field contains numeric values.
- Confirmed that the same 26 records contain both issues.
- Inspected the full records and found evidence that multiple columns are shifted.

### Key Finding
The 26 suspicious records are 2015 Volkswagen Jetta listings. Their values appear to become misaligned around the trim field. As a result, later values are stored under incorrect column names.

This means the numeric color values and invalid transmission values are likely symptoms of one malformed-record problem rather than separate data-quality problems.

### Learned
- Categorical data should be checked for capitalization differences and invalid categories.
- Looking at an unusual value by itself can be misleading. Inspecting the full row can reveal the underlying problem.
- Boolean masks can be combined using `&` to find records satisfying multiple conditions.
- Matching counts across different suspicious patterns can help identify whether the problems are related.
- Data should not be corrected until the cause of the issue is understood.

### Next
- Finish the remaining raw-data audit.
- Decide how to handle the 26 malformed Volkswagen Jetta records.
- Standardize categorical values such as body-style capitalization.
- Begin the data-cleaning notebook.