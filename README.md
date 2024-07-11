Here's a detailed README file for your COVID-19 Analysis Dashboard project on GitHub:

---

# COVID-19 Analysis Dashboard using Power BI

## Project Overview

The COVID-19 Analysis Dashboard is an interactive tool designed to provide insights into the COVID-19 pandemic. Using Power BI, this project integrates, analyzes, and visualizes comprehensive COVID-19 data from multiple sources to present a clear and detailed picture of the pandemic's impact and progress.

## Features

- **Data Integration**: Consolidates data on COVID-19 cases, deaths, and vaccinations from multiple CSV files.
- **Interactive Visualizations**: Utilizes line charts, bar charts, and tables to display trends over time and compare pre- and post-vaccination metrics.
- **Dynamic Filtering**: Offers slicers and filters to drill down into specific regions, time periods, and data categories.
- **Advanced Analytics**: Implements DAX measures to calculate key metrics, including:
  - Total Cases
  - Total Deaths
  - Death Percentage
  - Affected Percentage
  - Survival Rate
  - Survival Count

## Purpose and Impact

This dashboard serves as a powerful tool for public health officials, researchers, and the general public to understand the spread and impact of COVID-19. By visualizing crucial data points and trends, this project aids in informed decision-making and effective communication of the pandemic's status.

## Technologies Used

- **Power BI**: For building and designing the interactive dashboard.
- **DAX (Data Analysis Expressions)**: For creating complex measures and calculated columns.
- **CSV Files**: As data sources containing detailed information on COVID-19 cases, deaths, and vaccinations.

## Data Sources

1. **Cases and Deaths Data**: Contains columns for Name, WHO Region, cumulative cases, cases per 100,000 population, newly reported cases in the last 7 days, and deaths data.
2. **Daily Reports Data**: Includes columns for Date_reported, Country_code, Country, WHO_region, New_cases, Cumulative_cases, New_deaths, and Cumulative_deaths.
3. **Vaccination Data**: Provides information on COUNTRY, ISO3, WHO_REGION, data sources, total vaccinations, persons vaccinated, and vaccination types used.
4. **Vaccine Authorization Data**: Contains columns for ISO3, PRODUCT_NAME, VACCINE_NAME, COMPANY_NAME, AUTHORIZATION_DATE, and START_DATE.

## DAX Measures

Here are some of the DAX measures used in this project:

- **Total Cases**
  ```dax
  Total Cases = SUM('dim_global_area'[Cases - cumulative total])
  ```

- **Total Deaths**
  ```dax
  Total Deaths = SUM('dim_global_area'[Deaths - cumulative total])
  ```

- **Death Percentage**
  ```dax
  Death Percentage = 
  DIVIDE(
      SUM('dim_global_area'[Deaths - cumulative total]), 
      SUM('dim_global_area'[Cases - cumulative total]), 
      0
  ) * 100
  ```

- **Affected Percentage**
  ```dax
  Affected Percentage = 
  DIVIDE(
      SUM('dim_global_area'[Cases - cumulative total]), 
      SUM('dim_global_area'[Population]), 
      0
  ) * 100
  ```

- **Survival Rate**
  ```dax
  Survival Rate = 
  100 - DIVIDE(
      SUM('dim_global_area'[Deaths - cumulative total]), 
      SUM('dim_global_area'[Cases - cumulative total]), 
      0
  ) * 100
  ```

- **Survival Count**
  ```dax
  Survival Count = 
  SUM('dim_global_area'[Cases - cumulative total]) - 
  SUM('dim_global_area'[Deaths - cumulative total])
  ```
