# Used Vehicle Market Intelligence

An independent data science project exploring used vehicle sale prices, with the goal of estimating fair market value and identifying potentially underpriced or overpriced vehicles.

**Status:** In development — data audit and cleaning. A pricing model and deal-scoring results are planned; they are not yet implemented.

## Start here

| Resource | Purpose |
| --- | --- |
| [Data audit](notebooks/01_data_audit.ipynb) | Explore data types, missing values, duplicates, and suspicious records |
| [Data cleaning](notebooks/02_data_cleaning.ipynb) | Apply and inspect cleaning decisions on a copy of the raw data |
| [Project log](PROJECT_LOG.md) | Follow development notes, findings, and decisions |

Read the notebooks in numbered order.

## Repository layout

```text
data/
  raw/                         Original input data
    car_prices.csv
  processed/                   Reserved for cleaned exports
notebooks/
  01_data_audit.ipynb
  02_data_cleaning.ipynb
PROJECT_LOG.md                 Development journal
requirements.txt               Recorded Python environment
```

## Data and current work

The initial audit recorded **558,837 rows and 16 columns** in `car_prices.csv`. Findings include missing transmission values, inconsistent condition-score formatting, suspicious prices and odometer readings, and 26 malformed Volkswagen Jetta records.

The cleaning notebook currently:
- Removes the 26 malformed records from the working copy and retains them in a separate in-memory object.
- Creates normalized condition scores while preserving the original column.
- Standardizes make and body capitalization using the most common spelling.
- Checks transmission categories and creates a color column that treats the em dash as missing.

The raw data remains unchanged. The notebook does not yet export a processed dataset, and cleaning is still in progress.

**Data documentation still needed:** the original download URL, dataset attribution, and usage terms have not yet been recorded in this README.

## Run locally

The recorded environment includes Windows-specific dependencies such as `pywinpty`; the steps below target Windows PowerShell.

```powershell
git clone https://github.com/hamza-abusaif/used-vehicle-market-intelligence.git
cd used-vehicle-market-intelligence
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m jupyter lab
```

Open the notebooks from the `notebooks/` folder and use the virtual environment's Python kernel. Their input path is `../data/raw/car_prices.csv`, relative to that folder.

The environment's Python version has not yet been documented. Dependency installation and notebook execution should be verified before treating the workflow as fully reproducible.

## Roadmap

- [x] Establish project folders and a recorded environment
- [x] Create the initial audit notebook
- [x] Begin the cleaning notebook
- [ ] Document dataset source, usage terms, and Python version
- [ ] Finish cleaning decisions for missing values, suspicious prices, and odometer readings
- [ ] Validate and export a processed dataset
- [ ] Explore price patterns and develop a baseline valuation model
- [ ] Evaluate model performance and develop deal scoring
- [ ] Publish findings, limitations, and reproduction instructions

See [PROJECT_LOG.md](PROJECT_LOG.md) for the development history.
