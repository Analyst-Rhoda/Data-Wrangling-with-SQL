# Data Wrangling with SQL

## Table of Contents
- [Introduction: Why Data Wrangling Matters](#introduction-why-data-wrangling-matters)
- [Project Overview: The Dirty Data Challenge](#project-overview-the-dirty-data-challenge)
- [Step 1: Understanding the Raw Customer Dataset](#step-1-understanding-the-raw-customer-dataset)
- [Step 2: My Approach Using SQL](#step-2-my-approach-using-sql)
- [Step 3: Column-by-Column Cleaning](#step-3-column-by-column-cleaning)
  - Cleaning Emails  
  - Fixing Phone Numbers  
  - Standardizing Dates of Birth  
  - Normalizing Gender Values  
  - Cleaning Income Data  
  - Fixing Marital Status  
  - Handling Null National IDs  
- [Step 4: Final Cleaned Dataset Snapshot](#step-4-final-cleaned-dataset-snapshot)
- [Why It Matters: The Value of Clean Data](#why-it-matters-the-value-of-clean-data)
- [Full SQL Code Used](#full-sql-code-used)
- [Impact & Lessons Learned](#impact--lessons-learned)
- [Conclusion: Your Data Wrangling Journey](#conclusion-your-data-wrangling-journey)

---

## Introduction: Why Data Wrangling Matters

In the data world, **clean data is everything**.

Messy data leads to faulty analysis, poor decisions, and missed insights. Data wrangling is the essential first step in any data project — transforming raw, inconsistent data into clean, structured, and reliable information.

In this project, I demonstrate how I used SQL to transform a messy customer dataset into a trustworthy asset for analysis, reporting, and insights.

---

## Project Overview: The Dirty Data Challenge

The dataset I worked on had 3,000+ records of customer data with issues like:

- Inconsistent name formats  
- Typos in email addresses  
- Mixed phone number formats  
- Multiple date formats  
- Gender mismatches  
- Marital status inconsistencies  
- Income in varying currencies and formats  
- Missing or malformed National ID fields

**My mission:** Use SQL to clean and wrangle this dataset, making it usable for analytics, business decisions, and data modeling.

---

## Step 1: Understanding the Raw Customer Dataset

Before jumping in, I explored and diagnosed issues. Here's what I discovered:

| Column         | Example Problems                                       |
|----------------|--------------------------------------------------------|
| `email`        | `"johnsmith@gmail,com"`, `"mary@.yahoo.com"`          |
| `phone`        | `"0703-555-2222"`, `"+2347035552222"`, `"0703 555 2222"` |
| `dob`          | `"25th June 1999"`, `"1999-06-25"`, `"06/25/1999"`     |
| `gender`       | `"F"`, `"f"`, `"Female"`, `"MALE"`, `"others"`         |
| `income`       | `"₦90,000"`, `"NGN 70,000"`, `"Seventy Thousand"`     |
| `marital_status` | `"single"`, `"Single"`, `"SINGLE"`, `null`          |
| `national_id`  | `null`, `"N/A"`, `"11223344"`                         |

---

## Step 2: My Approach Using SQL

Instead of cleaning data in Excel or Python, I chose to use **pure SQL** for all wrangling.

### Tools Used:
- PostgreSQL  
- SQL `UPDATE`, `REGEXP_REPLACE`, `CASE`, `COALESCE`, `CAST`  
- Conditional logic and string functions  

### Why SQL?
- Efficient on large datasets  
- Great for data engineers & analysts  
- Easy to document and replicate  
- Directly modifies records in the database  

---

## Step 3: Column-by-Column Cleaning

### Cleaning Emails
**Problem:** Typos, misplaced symbols, uppercase text  
**Solution:** Replaced commas, lowercased text, and removed unwanted characters.

---

### Fixing Phone Numbers
**Problem:** Mixed formats, missing country code  
**Solution:** Standardized all numbers to begin with `+234` and removed formatting inconsistencies.

---

### Standardizing Dates of Birth
**Problem:** Multiple date formats  
**Solution:** Converted all to `YYYY-MM-DD` using date parsing.

---

### Normalizing Gender Values
**Problem:** Inconsistent casing and value variety  
**Solution:** Mapped all entries to `Male`, `Female`, or `Other`.

---

### Cleaning Income Data
**Problem:** Currency symbols, words instead of numbers  
**Solution:** Removed symbols and manually cleaned textual income values.

---

### Fixing Marital Status
**Problem:** Variants in capitalization and nulls  
**Solution:** Standardized casing using `INITCAP()` and replaced nulls with `'Unknown'`.

---

### Handling Null National IDs
**Problem:** Missing or invalid entries like `'N/A'`  
**Solution:** Replaced them with `'Unknown'`.

---

## Step 4: Final Cleaned Dataset Snapshot

Here’s how the data looked after cleaning:

| Full Name         | Email                        | Phone          | DOB         | Gender | Income | Marital Status | National ID  |
|-------------------|------------------------------|----------------|-------------|--------|--------|----------------|--------------|
| Brooke Alexander  | brookealexander@gmail.com    | +2347035552222 | 1999-12-16  | Female | 90000  | Single          | 1234567890   |
| John Smith        | johnsmith@gmail.com          | +2348024443333 | 1985-07-22  | Male   | 100000 | Married         | Unknown       |

---

## Why It Matters: The Value of Clean Data

- Clean data = better models, smarter decisions, fewer errors  
- Reduces time analysts waste fixing errors during analysis  
- Makes dashboards, visualizations, and models more reliable  
- Enables consistent processing across systems  

---

## Full SQL Code Used

You can find the full SQL code for each transformation [here](#) (insert GitHub repo or Notion link if available).

---

## Impact & Lessons Learned

By cleaning the data using SQL:

- I learned to handle diverse real-world inconsistencies.  
- Strengthened my SQL skills in regular expressions, conditionals, and updates.  
- Improved the dataset’s readiness for visualization, analysis, and modeling.

> "Your models are only as good as your data. Clean data is not optional — it’s the foundation."

---

## Conclusion: Your Data Wrangling Journey

This project taught me that data wrangling is not just technical — it’s strategic.  
The ability to take messy, unusable data and turn it into gold is one of the most powerful skills a data analyst or engineer can have.

---

### Next Steps

I’m exploring ways to automate similar wrangling tasks using SQL stored procedures and integrating SQL with Python for dynamic pipelines.

---

*Let me know if you'd like this turned into a PDF, blog, Notion post, or paired with a visual dashboard!*
