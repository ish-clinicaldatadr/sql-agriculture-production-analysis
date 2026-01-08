# U.S. Agriculture Production Analysis — SQL Relational Data Exploration

## Project Summary
This project analyzes U.S. agricultural production data across multiple commodities using relational SQL.  
The analysis focuses on identifying production leaders, detecting missing or incomplete reporting, and exploring trends across states and years.

The project is designed to demonstrate **practical SQL analytics skills**, including joins, aggregations, subqueries, and explicit handling of missing data.

---

## Data Source
**Public U.S. Agriculture Production Dataset**

- Population: U.S. states
- Geography: United States
- Time coverage: Multi-year production data
- Commodities analyzed:
  - Milk
  - Cheese
  - Coffee
  - Honey
  - Yogurt

---

## Project Objective
To:
- Analyze multi-table relational datasets using SQL
- Correctly distinguish missing data from zero values
- Perform cross-commodity and time-based analysis
- Apply SQL patterns commonly used in real-world analytics workflows

---

## Database Structure
All production tables are linked to a centralized state reference table to ensure consistent geographic coverage.
state_lookup
├── milk_production
├── cheese_production
├── coffee_production
├── honey_production
└── yogurt_production

---

## Tools Used
- SQLite (database engine)
- DBeaver (SQL interface)
- ANSI SQL

---

## Key Analytical Insights
- Production dominance varies by commodity, with different states leading milk, cheese, and yogurt production.
- Several states appear in reference tables but lack production records for specific commodities or years, indicating **reporting gaps rather than zero production**.
- Cross-commodity filtering enables more realistic comparisons and avoids misleading aggregate conclusions.
- Year-over-year trend analysis highlights variability in specialty commodity production such as coffee.

---

## SQL Techniques Demonstrated
- LEFT JOIN patterns to detect missing records
- Aggregations using GROUP BY and HAVING
- Subqueries for cross-commodity filtering
- COALESCE() for safe handling of missing values
- Correct placement of filters to preserve join behavior

---

## How to Explore This Project
1. Clone this repository
2. Open the SQLite database using DBeaver (or any SQLite-compatible tool)
3. Review:
   - `schema.sql` → table structure
   - `cleaning.sql` → data validation and sanity checks
   - `exploratory.sql` → analytical queries and insights

---

## Notes
This project is based on a guided SQL assignment from the **UC Davis SQL for Data Science** program.  
All SQL queries, logic, and interpretations are original work and are shared for portfolio demonstration purposes.

---

## About Me
Physician (MBBS, DNB Pediatrics) transitioning into **Healthcare Data Analytics**, with a focus on structured data analysis, data quality validation, and analytical reasoning.

**Skills:** SQL • Tableau • Power BI  
**Focus Areas:** Public datasets • Data integrity • Healthcare & population-level analysis
