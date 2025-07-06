# 🦠 COVID-19 Data Exploration with SQL

This project explores global COVID-19 data using SQL. It involves cleaning, analyzing, and deriving insights from two datasets: `CovidDeaths` and `CovidVaccinations`. The analysis was done using SQL Server.


## 📂 Dataset Tables

- **CovidDeaths**: Contains daily reports of total cases, deaths, population, and more by location.
- **CovidVaccinations**: Contains daily vaccination figures by location.


## 🔍 Key SQL Concepts Used

- Filtering and sorting  
- Aggregations (`SUM`, `MAX`)  
- Window functions (`OVER(PARTITION BY ...)`)  
- Joins between tables  
- Common Table Expressions (CTEs)  
- Temporary tables  
- Creating views  


## 🧪 Analysis Performed

- Total cases vs. total deaths: Calculating death percentage by country  
- Total cases vs. population: Estimating infection rates  
- Highest infection and death counts by country  
- Aggregated metrics by continent  
- Global statistics (cases, deaths, death rate)  
- Rolling vaccination totals using window functions  
- Percentage of population vaccinated  
- Storing processed data using a view and temporary table


## 📌 Output Preview

Final views and tables generated can be used for:

- Building dashboards in **Power BI** / **Tableau**
- Further visual analysis

## 📷 Screenshots
![Screenshot 1](Covid%201.png)

![Screenshot 2](Covid%202.png)


## 🛠 Sample Queries

```sql
-- Death percentage for the United States
SELECT Location, date, total_cases, total_deaths, 
       (total_deaths/total_cases)*100 AS DeathPercentage
FROM PortfolioProject..CovidDeaths
WHERE location LIKE '%states%'

-- Countries with the highest infection rate
SELECT Location, MAX(total_cases/population)*100 AS PercentPopulationInfected
FROM PortfolioProject..CovidDeaths
GROUP BY Location
ORDER BY PercentPopulationInfected DESC

