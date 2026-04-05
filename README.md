**F1 Performance Analytics: SQL & R Case Study**

Project Overview
This project demonstrates a comprehensive, end-to-end data analysis of Formula 1 historical records. By integrating SQL (SQLite) for complex data engineering and R for statistical processing, I extracted actionable insights regarding driver performance, team dominance, and historical trends.

Data Source
The analysis is based on the Formula 1 World Championship (1950-2023) dataset sourced from Kaggle (https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020).

This relational dataset contains extensive records of:
- Races & Results: Finishing positions, points, and grid starts.
- Performance Metrics: Lap times (over 589,000 records) and fastest laps.
- Entities: Comprehensive data on drivers, constructors, and circuits.

Technical Stack
- Language: R (v4.5.2+).
- Database Engine: SQLite (via RSQLite).
- Key Libraries: DBI (Database Interface), readr (Data Import), ggplot2 (Visualization).

ETL Process (Extract, Transform, Load)To ensure high-performance querying, I established a local ETL pipeline:
- Ingestion: Multiple CSV datasets were imported into a temporary SQLite database residing in RAM for rapid processing.
- Data Integrity: Performed critical data type conversions, such as formatting date and time strings into standard SQL-compliant formats to ensure accurate time-series analysis.
- Database Migration: R data frames were copied into the SQLite environment with schema optimizations (e.g., overwriting tables to ensure fresh sessions).

Key Business Insights & Analytical Queries (Examples):

Competitive Benchmarking (Window Functions)I utilized CTEs (Common Table Expressions) and Window Functions to analyze the 2023 season:
  - Winner Identification: Used RANK() partitioned by raceId to programmatically identify winners for every GP in 2023.
  - Performance Variance: Applied the LAG() function to track Max Verstappen's points progression. By calculating the points_diff between consecutive races, I analyzed his performance stability.

Operational & Historical Outliers
  - Extreme Performance: Identified rare instances where drivers won a Grand Prix after starting from grid position >15, highlighting exceptional race strategy and recovery.
  - Historical Dominance: Analyzed the "Monaco Grand Prix" to rank the most successful drivers at F1's most technically demanding circuit.

Market & Demographic Segmentation
  - Driver Eras: Categorized over 800 drivers into "Pioneer", "Classic", and "Modern" eras using CASE logic based on their date of birth.
  - Nationality Analysis: Aggregated career wins by nationality, identifying the United Kingdom and Germany as the most dominant regions in F1 history.

Team Performance Post-2010
  - Filtered constructor results to identify teams with over 1,000 points since 2011, highlighting the era of Mercedes and Red Bull dominance.

Project Structure
- F1_sql_analysis.Rmd: The core analysis file containing all R and SQL code.
- F1_sql_analysis.pdf: The final rendered report.
- Datasets/: (Ignored via .gitignore) Placeholder for raw CSV files from Kaggle.

Conclusion
This project illustrates the ability to handle large-scale relational data, perform advanced SQL operations, and translate raw numbers into a narrative of sports performance and historical evolution.
