# Layoffs Data Cleaning SQL Project
This project involves cleaning and preparing the 2022 Layoffs dataset (from [Kaggle, Swaptr/layoffs-2022]) for further analysis and exploration using SQL. The repository contains the data cleaning SQL script and documentation for each step taken to improve data quality and consistency.

# Project Goals
1)Ensure data integrity by removing duplicates and correcting inconsistencies.

2)Standardize entries for reliable downstream analysis.

3)Handle missing values appropriately.

4)Prepare a clean, analysis-ready version of the raw layoffs dataset.

# Project Structure
Portfolio-Project-Data-Cleaning.sql — Main SQL script with detailed step-by-step cleaning logic.

# Steps Performed
1. **Create Staging Table**
Backs up raw data for reference and rollback.

All cleaning is performed on a staging table to preserve the original dataset.

2. **Remove Duplicates**
Identifies duplicates using a ROW_NUMBER() window function over all relevant columns.

Only true duplicates are removed, ensuring legitimate records remain untouched.

3. **Standardize and Fix Data**
Industry column:

Sets blank strings to NULL for easier handling.

Populates missing industry entries based on other rows for the same company.

Standardizes similar values (e.g., 'Crypto Currency', 'CryptoCurrency' → 'Crypto').

Country column:

Removes trailing periods to ensure consistent country names.

Date column:

Converts string dates to proper SQL DATE datatype.

4. **Handle Null Values**
Leaves NULLs in total_laid_off, percentage_laid_off, and funds_raised_millions to facilitate accurate analysis.

Removes rows where both total_laid_off and percentage_laid_off are NULL (as they carry no useful quantitative data).

5. **Final Cleanup**
Drops helper columns (like row numbers) no longer necessary after deduplication and cleaning.

# Usage Instructions
Import the raw dataset [from Kaggle] into your SQL environment under the world_layoffs.layoffs table.

Run each step from Portfolio-Project-Data-Cleaning.sql in order.

The final cleaned dataset is available in the world_layoffs.layoffs_staging2 table.

# Key SQL Features Used
Window Functions (ROW_NUMBER())

CTEs (Common Table Expressions)

Conditional UPDATEs and DELETEs

String manipulation (TRIM, STR_TO_DATE)

Data type conversion



