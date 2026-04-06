# 🌍 Global Access to Drinking Water (2000–2020)

UN Sustainable Development Goal 6: Clean Water and Sanitation

---

## 📌 Project Summary

This project analyzes global access to basic drinking water services between 2000 and 2020 using data from the WHO/UNICEF Joint Monitoring Programme (JMP).

The analysis evaluates how access has changed across :

- National populations
  
- Rural populations
  
- Urban populations
  
- Global regions
  
It focuses on measuring progress over time and identifying inequalities in access, particularly between rural and urban populations.


## Dataset

Source:
WHO / UNICEF Joint Monitoring Programme (JMP)

Dataset:
Estimates on the Use of Water (2000–2020)

Official dataset :
https://drive.google.com/file/d/1p6j3MJz-eWaWsIfbPTHQAfUR-Ecm5voW/view?usp=sharing

Clean dataset : https://docs.google.com/spreadsheets/d/19V-E28o6QDEpGCdRJh5gTtqQ5pPgvQRanQ8xtUJmdqk/edit?usp=sharing

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

- Irregular time intervals across countries

- Duplicate records (identified when year difference = 0)
  
- Missing values stored as "null" causing calculation errors
  
- Invalid percentages exceeding 100%
  
- Pivot table errors (#DIV/0!) due to missing values


# Data Cleaning Process

<b>Step 1 Sorting the Dataset</b>

The dataset was sorted by:

Country name

Year <b>(ascending)</b>

This ensured that consecutive rows represented different years for the same country, allowing change over time to be calculated.

<b>Step 2 Creating a Year Difference Feature</b>

A new column called y_diff was created to calculate the difference between two observation years.
Formula logic:

`y_diff = year(n+1) − year(n)`


This calculation was only performed when the country name in both rows matched.

<b>Step 3 Identifying Duplicate Rows</b>

If the calculated year difference equaled zero, this indicated duplicate records.

Duplicate rows were identified and removed to ensure accurate calculations.

![image alt](https://github.com/xolanintsibande/global-water-access-2/blob/800dad359820f7a52ed4f5c60641001c81176fc0/images/duplicate.png)

<b>Step 4 Handling Missing Values</b>

Rows containing “null” values caused formula errors.

To resolve this, formulas were wrapped using:

`IFERROR()`

![image alt](https://github.com/xolanintsibande/global-water-access-2/blob/586e021098ddc12476728a3fc8826f7906344f47/images/IFERROR().png)


This ensured that invalid calculations returned null values instead of errors.

<b>Step 5 Correcting Invalid Percentages</b>

Some water access values <b>exceeded 100%</b>.

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

After cleaning and feature creation, the dataset contained <b>28 analytical features.</b>

# Analysis

A summary sheet called <b>Global Water Access Report (2000–2020)</b> was created to analyze the dataset.

The analysis included:

<b>Year Representation Analysis</b>

Statistics calculated:

- Minimum year : 1 year
  
- Maximum year : 5 years 
  
- Average difference ~ 4.80 years
    
- Distribution of years across the dataset

This confirms that data was not collected annually, requiring adjusted time-based calculations.

<b>Annual Rate of Change (ARC)</b>

ARC measures yearly improvement in water access (percentage points).

Formula used:

`ARC = (value_year2 − value_year1) / (year2 − year1)`

ARC values were calculated for:

- National populations

- Rural populations

- Urban populations

# Access Classification Analysis  

Countries were categorized into groups based on ARC results:

This helped identify where water access is improving or declining.

- Countries with no data

- Countries with full access

- Countries where ARC > 0 (improvement)

- Countries where ARC = 0 (no change)

- Countries where ARC < 0 (decline)

<b>Interpretation :</b>

- More countries are improving than declining

- Urban areas have more countries at full access levels

- Rural areas still lag behind but are improving faster

  
# Regional Progress Comparison

Key Regional Insights:

<b>Sub-Saharan Africa</b>

- Highest ARC_n: 0.5687

- Indicates strong improvement but still lower overall access

<b>South Asia</b>

High improvement: ARC_n ~0.4802

<b>North America</b>

- Very low ARC values (~0.017)

- Indicates already saturated access levels

<b>Global Average ARC</b>

National: 0.2767
Urban: 0.1548
Rural: 0.4845

<b>Interpretation :</b>

- Developing regions show faster growth
  
- Developed regions show minimal change due to already high access

![image alt](https://github.com/xolanintsibande/global-water-access-2/blob/8a2c5d4d6b1503dbd0edcdb2bfb4f490c1971a0c/images/summary_sheet.png)

# Data Visualizations


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

<b>Regional comparison</b>

pivot table + visualization


# Key Insights

The analysis revealed several important trends:

• Rural populations often show higher improvement rates in water access than urban populations.

• Many urban populations already have near-universal access, resulting in ARC values close to zero.

• Sub-Saharan Africa remains the region with the largest population lacking access to basic drinking water services.

• At the current rate of improvement, universal water access in some regions may not be achieved until around 2080.

• Improvements in water access vary widely across countries, indicating that policy, infrastructure, and economic development strongly influence outcomes.

# Tools Used

- Google Sheets

- Data Cleaning

- Feature Engineering

- Statistical Analysis

- Data Visualization

- Lookup Functions

- Pivot Tables

- Exploratory Data Analysis

# Conclusion

- This project demonstrates how data can be used to evaluate global development challenges.

- While progress has been made in improving access to drinking water, significant inequalities remain, particularly across regions and between rural and urban populations.
