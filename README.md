# 🌍 Global Access to Drinking Water (2000–2020)

UN Sustainable Development Goal 6

This project analyzes global access to basic drinking water services between 2000 and 2020 using data from the WHO/UNICEF Joint Monitoring Programme (JMP).

The analysis investigates how access to drinking water has changed across countries, regions, and population groups (national, rural, and urban) and evaluates global progress toward United Nations Sustainable Development Goal 6: Clean Water and Sanitation


## Overview

Access to safe drinking water remains one of the most important global development challenges.
This project analyzes global water access trends using the WHO/UNICEF Joint Monitoring Programme (JMP) dataset covering 2000–2020.

The goal of the analysis was to investigate how access to basic drinking water services has changed over time across national, rural, and urban populations, and to evaluate progress toward United Nations Sustainable Development Goal 6 (Clean Water and Sanitation).

This project was completed as part of the ALX Data Analytics Program and demonstrates practical data analysis skills including:

- Data cleaning

- Data validation

- Feature engineering

- Time-series analysis

- Statistical analysis

- Data visualization

- Exploratory data analysis


## Dataset

Source:
WHO / UNICEF Joint Monitoring Programme (JMP)

Dataset:
Estimates on the Use of Water (2000–2020)

Official dataset source:
https://washdata.org⁠�

[(image)]


The dataset contains 16 original features, including:

## Dataset Features

| Feature | Description |
|--------|-------------|
| name | Country name |
| year | Observation year |
| wat_bas_n | National population with basic water access (%) |
| wat_bas_r | Rural population with basic water access (%) |
| wat_bas_u | Urban population with basic water access (%) |

Water service access levels are recorded for:

- National populations
  
- Urban populations
  
- Rural populations

The dataset allows analysis of changes in water access across countries over time.

# Project Objective

The objective of this analysis was to answer the following questions:

1. How frequently was water access data recorded across countries between 2000 and 2020?

2. How has access to basic drinking water changed over time?

3. How do improvement rates differ between national, rural, and urban populations?

4. Which regions show the greatest progress in improving water access?

5. Are rural populations catching up with urban populations in water service access?

# Data Challenges

Before analysis could begin, several <strong>data quality issues</strong> were identified.

1. Irregular Year Representation
The dataset title indicates coverage from 2000–2020, but not every country has data for every year.

This created challenges when comparing changes across time.

2. Duplicate Records

During feature creation, some rows produced a year difference value of zero, indicating duplicate observations for the same country and year.

3. Missing Values
   
Some cells contained the text “null”, which caused spreadsheet formulas to produce #VALUE! errors during calculations.

4. Invalid Percentage Values
   
Some water access percentages slightly exceeded 100%, which is not logically possible for population access indicators.

These issues required a structured data cleaning process before performing analysis.


# Data Cleaning Process

Step 1 — Sorting the Dataset
The dataset was sorted by:

Country name

Year (ascending)

This ensured that consecutive rows represented different years for the same country, allowing change over time to be calculated.

Step 2 — Creating a Year Difference Feature

A new column called y_diff was created to calculate the difference between two observation years.
Formula logic:

- y_diff = year(n+1) − year(n)


This calculation was only performed when the country name in both rows matched.

Step 3 — Identifying Duplicate Rows

If the calculated year difference equaled zero, this indicated duplicate records.

Duplicate rows were identified and removed to ensure accurate calculations.

Step 4 — Handling Missing Values

Rows containing “null” values caused formula errors.

To resolve this, formulas were wrapped using:

- IFERROR()

This ensured that invalid calculations returned null values instead of errors.

Step 5 — Correcting Invalid Percentages

Some water access values exceeded 100%.

To address this, new rounded features were created:

- wat_bas_n (rounded)

- wat_bas_r (rounded)

- wat_bas_u (rounded)

Values were rounded to zero decimal places.

# Feature Engineering

Several additional variables were created to support deeper analysis.


| Feature | Description |
|--------|-------------|
| y_diff | Difference between observation years |
| ARC_n | Annual rate of change in national water access |
| ARC_r | Annual rate of change in rural water access |
| ARC_u | Annual rate of change in urban water access |
| wat_bas_n_rounded | Rounded national water access |
| wat_bas_r_rounded | Rounded rural water access |
| wat_bas_u_rounded | Rounded urban water access |
| ARC_n_full | Indicator for full national water access |
| ARC_r_full | Indicator for full rural water access |
| ARC_u_full | Indicator for full urban water access |
| ARC_diff | Difference between rural and urban annual rate of change values |
| region | Geographic region of each country |

After cleaning and feature creation, the dataset contained 28 analytical features.

# Analysis

A summary sheet called <b>Global Water Access Report (2000–2020)</b> was created to analyze the dataset.

The analysis included:

<b>Year Representation Analysis</b>

Statistics calculated:

- Minimum year
  
- Maximum year
  
- Average difference between observations
  
- Distribution of years across the dataset

A histogram was created to visualize year distribution across countries.

<b>Annual Rate of Change (ARC)</b>

The Annual Rate of Change (ARC) was used to measure improvement in water access.

Formula used:

- ARC = (value_year2 − value_year1) / (year2 − year1)

ARC values were calculated for:

- National populations

- Rural populations

- Urban populations

These metrics represent annual percentage point changes in water access.

# Access Classification Analysis  

Countries were categorized into groups based on ARC results:

- Countries with no data

- Countries with full access

- Countries where ARC > 0 (improvement)

- Countries where ARC = 0 (no change)

- Countries where ARC < 0 (decline)

This helped identify where water access is improving or declining.

# Data Visualizations

Several charts were created to explore the data.

<b>Year Distribution</b>

A histogram was created to visualize the distribution of observation years across the dataset.

This helped confirm that data points exist across the 2000–2020 time range.

<b>Annual Rate of Change Distribution</b>

Histograms were created to visualize the distribution of :

- National ARC

- Rural ARC

- Urban ARC

These charts helped identify countries with rapid improvement or decline in water access.

<b>Rural vs Urban Change Comparison</b>

A histogram of ARC_diff was created to show the difference between rural and urban water access improvements.

This visualization highlights inequalities between population groups.

<b>Regional Progress Comparison</b>

A regional analysis chart was created to compare:

- National ARC

- Rural ARC

- Geographic region

- Population size

This visualization helped identify which regions are improving fastest.

# Key Insights

The analysis revealed several important trends:

• Rural populations often show higher improvement rates in water access than urban populations.

• Many urban populations already have near-universal access, resulting in ARC values close to zero.

• Sub-Saharan Africa remains the region with the largest population lacking access to basic drinking water services.

• At the current rate of improvement, universal water access in some regions may not be achieved until around 2080.

• Improvements in water access vary widely across countries, indicating that policy, infrastructure, and economic development strongly influence outcomes.

# Tools Used

Google Sheets

Data Cleaning

Feature Engineering

Statistical Analysis

Data Visualization

Lookup Functions

Pivot Tables

Exploratory Data Analysis

# Skills Demonstrated

Data Cleaning

Exploratory Data Analysis

Time Series Analysis

Statistical Analysis

Data Visualization

Data Validation

Spreadsheet Analytics

Data Storytelling
