# Global Data Job Salaries Analysis

## Overview

This project analyses salary data from global data-related jobs around the world.

The objective is to identify:

- Countries with the highest average salaries
- Job titles with the highest average salaries
- Salary differences across countries and job roles

The analysis was performed using Python and Pandas.

---

## Dataset

Source:
https://huggingface.co/datasets/lukebarousse/data_jobs

The dataset contains information about:

- Job titles
- Countries
- Salaries
- Employment types
- Remote work status
- Other job-related attributes

---

## Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook

---

## Data Cleaning

The following cleaning steps were performed:

1. Missing yearly salaries were replaced using hourly salaries when available.
2. Yearly salary was approximated as:

   Salary = Hourly Salary × 40 hours/week × 52 weeks/year

3. Records with both salary measures missing were removed.

---

## Research Questions

### 1. Which countries have the highest average salaries?

Countries with fewer than 100 observations were excluded to ensure reliable comparisons.

### 2. Which job titles have the highest average salaries?

Job titles with fewer than 100 observations were excluded.

### 3. Which job title has the highest average salary in each country?

A country-job title salary matrix was created to compare salary structures.

---

## Results

Key findings include:

- Significant salary differences between countries.
- Certain technical roles consistently achieve higher salaries.
- Salary structures vary substantially across countries.

---
