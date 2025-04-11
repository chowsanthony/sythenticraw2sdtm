# Synthetic Data Generation and Transformation for SDTM Domains

This proof-of-concept consists of two Jupyter notebooks, `synthetize_raw.ipynb` and `raw2sdtm.sql.ipynb`, which are designed to generate synthetic clinical data and transform it into SDTM-compliant datasets.

## Overview

1. **`synthetize_raw.ipynb`**:
   - **Purpose**: Generates synthetic clinical data based on anonymized real-world data.
   - **Key Steps**:
     - Reads anonymized clinical data from a CSV file.
     - Uses the [SDV (Synthetic Data Vault)](https://sdv.dev/) library to detect metadata and train a Gaussian Copula model for synthetic data generation.
     - Evaluates the quality of the synthetic data using diagnostic tools.
     - Exports the synthetic data in a hierarchical JSON format, grouping smoking-related data under `Usage` and demographic details under `Demog`.

2. **`raw2sdtm.sql.ipynb`**:
   - **Purpose**: Transforms the synthetic data into SDTM-compliant datasets for the DM (Demographics) and SU (Substance Use) domains.
   - **Key Steps**:
     - Loads the synthetic JSON data into an in-memory DuckDB database.
     - Creates SDTM-compliant datasets:
       - **DM Domain**: Extracts demographic information such as age and sex.
       - **SU Domain**: Extracts smoking-related information such as cigarette usage and pack-per-year data.
     - Exports the transformed datasets as CSV files (`sdtm_dm.csv` and `sdtm_su.csv`).

## Workflow

1. Run `synthetize_raw.ipynb`:
   - Install required Python libraries (`sdv`, `seaborn`, `matplotlib`).
   - Generate synthetic data and save it as `synthetic_raw.json`.

2. Run `raw2sdtm.nosql.ipynb`:
   - Install required Python libraries (`duckdb`, `pyarrow`, `polars`).
   - Transform the synthetic data into SDTM-compliant datasets and save them as CSV files.

## Outputs

- **Synthetic Data**:
  - `synthetic_raw.json`: Hierarchical JSON file containing synthetic clinical data.

- **SDTM-Compliant Datasets**:
  - `sdtm_dm.csv`: Demographics (DM) domain dataset.
  - `sdtm_su.csv`: Substance Use (SU) domain dataset.