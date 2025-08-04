# Layoffs Data Cleaning SQL Project

This project focuses on cleaning and preparing the [2022 Layoffs dataset from Kaggle (swaptr/layoffs-2022)] for advanced data analysis using SQL. The repository includes a comprehensive SQL script with step-by-step cleaning logic and documentation to enhance dataset quality and reliability.

---

## Project Goals

- Ensure data integrity by removing duplicates and correcting inconsistencies
- Standardize entries to enable consistent downstream analysis
- Handle missing values thoughtfully
- Produce a clean, analysis-ready version of the raw layoffs dataset

---

## Project Structure

- `Portfolio-Project-Data-Cleaning.sql` — Main SQL script containing detailed, step-by-step cleaning queries and comments

---

## Steps Performed

### 1. Create Staging Table
- Back up raw data by duplicating the original table
- Perform all cleaning operations in the staging table to keep the raw table unchanged

### 2. Remove Duplicates
- Identify duplicate rows using `ROW_NUMBER()` window functions over all relevant columns
- Retain only unique records, carefully verifying legitimate repeats to prevent accidental loss
- Use helper columns as necessary during deduplication

### 3. Standardize and Fix Data
- **Industry column:**
  - Convert blanks to `NULL`
  - Populate missing industry values using entries from identical company names where possible
  - Standardize name variants, e.g., `'Crypto Currency'` and `'CryptoCurrency'` → `'Crypto'`
- **Country column:**
  - Remove trailing periods for consistency (e.g., `'United States.'` → `'United States'`)
- **Date column:**
  - Convert string-formatted dates to the SQL `DATE` datatype using `STR_TO_DATE`

### 4. Handle Null Values
- Leave `NULL`s in `total_laid_off`, `percentage_laid_off`, and `funds_raised_millions` where appropriate
- Remove rows where both `total_laid_off` and `percentage_laid_off` are `NULL` (i.e., useless for quantitative analysis)

### 5. Final Cleanup
- Drop temporary/helper columns (e.g., `row_num`) created during cleaning
- Final, cleaned dataset is available in the `world_layoffs.layoffs_staging2` table

---

## Usage Instructions

1. Import the raw dataset (see Kaggle link above) into your SQL environment as the `world_layoffs.layoffs` table
2. Run each section of the `Portfolio-Project-Data-Cleaning.sql` script in sequence
3. The final cleansed dataset will be found in the `world_layoffs.layoffs_staging2` table

---

## Key SQL Features Used

- Window Functions (`ROW_NUMBER()`)
- Common Table Expressions (CTEs)
- Conditional `UPDATE` and `DELETE`
- String manipulation (`TRIM`, `STR_TO_DATE`)
- Data type conversion

---

## EXAMPLE QUERY
SELECT * FROM world_layoffs.layoffs_staging2 LIMIT 10;

---

## Prerequisites

- MySQL or compatible database supporting window functions and CTEs
- Sufficient permissions to create, alter, and drop tables

---

## Acknowledgements

- [Kaggle - swaptr/layoffs-2022]

---

## Contact

For questions or contributions, please contact:  
**Jaiveer Singh Sahni** - www.linkedin.com/in/jaiveer-singh-sahni-112823261

---




