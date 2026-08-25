# Introduction 

Hello, this project is the analysis of the data job market in year 2023 in Poland. The project is created to understand the job market effectively. The year 2023 is a particular choice due  to the comprehensive data available. It showcases the top paying and in demand skills to help understand the job markets and oppurtunities for the role of Data Analyst and Data Scientist

The data is sourced from [Luke Barousse's](https://lukebarousse.com/python) which is a foundation for my analysis. Using Python, I explore key questions such as most demanded skills and salary trends.

# Tools I used 
**Python. I also used the following Python libraries: 

    - Pandas 
    - Matplotlib 
    - Seaborn 
** Jupyter Lab: I used to run my Python scripts 

# Project 1

# Data Preparation and Cleanup

This section outlines the steps taken to prepare the data for analysis, ensuring accuracy and usability.

## Import & Clean Up Data

I start by importing necessary libraries and loading the dataset, followed by initial data cleaning tasks to ensure data quality.

```python
# Importing Libraries
import ast
import pandas as pd
import seaborn as sns
from datasets import load_dataset
import matplotlib.pyplot as plt  

# Loading Data
dataset = load_dataset('lukebarousse/data_jobs')
df = dataset['train'].to_pandas()

# Data Cleanup
df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)
```

## Filter jobs in Poland

To focus my analysis on the Polish job market, I apply filters to the dataset, narrowing down to roles based in Poland.

```python
df_Poland = df[df['job_country'] == 'Poland']

```

# Project 2
1. What are the skills most in demand for the Data Analyst, Data Scientist and Data Engineer roles.

### Result 
![Graph of top skills demanded in Data jobs in Poland](Skill_count.png)

### Insights 
+ Python is the most demanded role for Data Scientist and Data Engineeers, mentioned at least in <span style="color:red">60%</span> of job postings.
+ For the role of Data Analyst, SQL is the most demanded skill as it is a great tool to do relational database management and analysis.
+ Both <span style="color:red"> Python and SQL</span> are demanded in at least <span style="color:red">30% </span> of job postings across all three job titles mentioned
 
# Project 3

2. Comparison and analysis of trending skills for Data Analyst and Data Scientist by month

### Results 


```Python 
from matplotlib.ticker import PercentFormatter

sns.lineplot(data=top_5_DA, ax=ax[0], dashes=False, palette=skill_palette, legend=False)
ax[0].set_title("Data Analyst")
ax[0].yaxis.set_major_formatter(PercentFormatter(decimals=0))
ax[0].set_xlabel(" ")
sns.despine()
plt.show()
```

![Comparison of trending skills for Data Analyst and Data Scientist in Poland](Skill_compare.png)

### Insights 
+ SQL and Python are among top 3 meost mentioned skills for both Data Analyst and Data Scientist positions
+ Cloud skills such as Azure and AWS show an increase in their share of Data Scientist job postings towards the end of 2023.
+ For Data Analyst positions, SQL is mentioned more often than visualisation tools such as Power BI and Tableau.
4. Python is more in demand programming language than R, for Data Scientist roles.


# Project 4
3. How well do different job titles pay?
4. How well do different skills pay for the role of Data Analyst?

# Result

![Salary distribution in Poland](Salary_Analysis_1.png)


### Insights 
+ Median salaries of Data Scientist and Data Engineer are comparable.
+ Median salary of Data Analyst is lowest.

# Results 
``` Python 
#Top 10 most paid skills 
sns.barplot(data=df_DA_top_pay,y=df_DA_top_pay.index, x="median", ax=ax[0], hue="median", palette="dark:b_r") 
ax[0].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f"{int(x/1000)}k"))

#Top 10 most in demand skills
sns.barplot(data=df_DA_top_count,y=df_DA_top_count.index, x="median", ax=ax[1], hue="median", palette="light:b") 
ax[1].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f"{int(x/1000)}k"))
plt.show()

```
![Highest paid and most in demand skills for Data Analyst in Poland](Salary_Analysis_2.png)

### Insights 
+ The top plot highlights that the highest salaries are dominated by specialized, niche competencies such as advanced cloud platforms, machine learning frameworks, or big data infrastructure tools.Core Skills Dominate 
+ Conversely, the bottom plot shows that the roles with the highest job count rely on foundational, highly accessible tools (like SQL, Excel, or Python).


# Bonus project 

Additionaly I make a heat map to understand the salaries of all job titles in top 10 countries with most data available. 

# Result 
![Heat map of salaries in different countries](Bonus_Analysis.png)

# Insights 
+ United States and Canada lead with the highest average salaries across all job titles.
+ The United Kingdom shows an exceptionally low average salary (bright yellow) specifically for Cloud Engineers.
+ Machine Learning Engineers and Senior Data Scientists consistently command the highest compensation across most listed countries.
+ Australia, India, and Poland generally offer mid to lower salary ranges (teal and green shades) compared to North America and Western Europe.