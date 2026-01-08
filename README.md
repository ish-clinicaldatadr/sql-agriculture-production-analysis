# U.S. Agriculture Production Analysis — SQL Relational Data Exploration - UC Davis SQL Foundations


**Relational Data Analysis using SQLite (ANSI SQL)**

A hands-on SQL project analyzing multi-commodity U.S. agricultural production data across states and years, with emphasis on joins, aggregations, subqueries, and missing-data analysis.

---

## 🛠 Tech Stack
- SQLite • DBeaver • ANSI SQL  
- Domain: Agriculture / Production Analytics

---

## 📊 Project Overview

This project analyzes U.S. agricultural production data across multiple commodities — milk, cheese, coffee, honey, and yogurt — using relational SQL techniques.

The goal was to answer **business-style analytical questions**, such as:
- Which states dominate production?
- Which states are missing reported data?
- How do production patterns change over time?
- How can cross-commodity filtering support realistic planning decisions?

Key SQL concepts applied:
- Multi-table joins  
- Aggregations and grouping  
- Subqueries  
- Explicit handling of missing and incomplete data  

---

## Data Model 

All production tables link to a centralized state reference table.

```sql
state_lookup
|
|-- milk_production
|-- cheese_production
|-- coffee_production
|-- honey_production
|-- yogurt_production
```

The `state_lookup` table acts as the authoritative state list, enabling detection of missing production records.

---

## How to Run
1. Clone the repository  
2. Open the SQLite database in DBeaver  
3. Run SQL files in order:
   - `schema.sql`
   - `cleaning.sql`
   - `exploratory.sql`

---

## 📈 Key Queries & Insights

### Identifying Missing States (LEFT JOIN Pattern)
- States present in the reference table but lacking reported milk production in 2023.
```sql
SELECT
    sl.STATE
FROM state_lookup sl
LEFT JOIN milk_production mp
    ON sl.State_ANSI = mp.State_ANSI
    AND mp."Year" = 2023
WHERE mp.State_ANSI IS NULL;
```

Insight:
Missing records do not imply zero production — they often reflect reporting gaps that must be explicitly identified and communicated.


- Cross-Commodity Filtering
Total yogurt production in 2022 for states that also reported cheese production in 2023.
```sql
SELECT
    SUM(yp.Value) AS total_yogurt_production
FROM yogurt_production yp
WHERE yp."Year" = 2022
  AND yp.State_ANSI IN (
      SELECT DISTINCT cp.State_ANSI
      FROM cheese_production cp
      WHERE cp."Year" = 2023
  );
```
Insight:
Cross-commodity filtering avoids misleading comparisons and supports more realistic production and planning analysis.


## Analytical Themes
- Production leaders across commodities
- Detection of “ghost states” (present in reference tables but absent in production data)
- Year-over-year trend analysis
- Distinguishing missing data from zero values

## Key SQL Learnings

#### LEFT JOIN vs WHERE:
- Filters in a WHERE clause can unintentionally convert a LEFT JOIN into an INNER JOIN.
- Best practice: apply conditional filters inside the JOIN clause when preserving unmatched rows.

#### WHERE vs HAVING:
- WHERE filters rows; HAVING filters aggregated results.

#### Missing Data ≠ Zero:
- Use LEFT JOIN + IS NULL to detect missing records.
- Use COALESCE() only when replacing missing values is analytically justified.

## Notes
- Based on a guided assignment from UC Davis – SQL for Data Science (Coursera)
- All SQL logic, queries, and interpretations are original work
- Shared for learning and portfolio demonstration purposes

## About Me
Physician with a strong foundation in Healthcare Data Analytics, combining clinical expertise with structured data analysis, data quality validation, and analytical reasoning.

- **Skills:** SQL • Tableau • Power BI • Excel        
- **Focus Areas:** Population health trends • Healthcare utilization & outcomes • Data quality and validation in clinical datasets
