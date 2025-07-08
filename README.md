# Layoffs Dataset – SQL Data Cleaning Project

This project demonstrates how I cleaned a real-world dataset using SQL (MySQL). The dataset, sourced from [Kaggle](https://www.kaggle.com/datasets/swaptr/layoffs-2022), includes layoff information from global companies during 2020–2023. My focus was to clean and prepare the data for further analysis by handling duplicates, nulls, formatting, and standardization.

---

## Dataset

- Source: [Layoffs 2022 - Kaggle (Swaptr)](https://www.kaggle.com/datasets/swaptr/layoffs-2022)
- File Used: `layoffs.csv`

---

## Tools Used

- MySQL (Workbench)
- SQL

---

## Data Cleaning Steps

The entire data cleaning logic is implemented in `Data cleaning_worlds_layoffs.sql`.

### Steps Performed:

1. **Initial Table Copy**  
   - Created a staging table `layoffs_staging` to preserve the original dataset.

2. **Removing Duplicates**  
   - Used a Common Table Expression (CTE) with `ROW_NUMBER()` to identify and delete duplicate records.

3. **Creating a Second Staging Table (`layoffs_staging2`)**  
   - Stored unique rows along with a `row_num` column to cleanly handle deletion.

4. **Whitespace Removal**  
   - Used `TRIM()` to remove leading/trailing spaces from company names and other fields.

5. **Date Formatting**  
   - Converted date strings to MySQL's native `DATE` format using `STR_TO_DATE()`.

6. **Handling Null & Blank Values**  
   - Identified rows with missing values (especially `total_laid_off` and `percentage_laid_off`) and deleted them if both were missing.
   - Also handled empty strings and `NULL` cases across key columns.

7. **Column Cleanup**  
   - Dropped the helper column `row_num` after final cleaning.
