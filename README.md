# 🏋️‍♂️ Mr. Olympia Data Pipeline with dbt & DuckDB

This project uses **dbt (data build tool)** and **DuckDB** to transform, clean, and analyze historical data from Mr. Olympia bodybuilding competitions across multiple categories (Open, Classic Physique, 212, Men's Physique).

## 🚀 Tech Stack
* **dbt Core:** Data transformation and modeling.
* **DuckDB:** Local OLAP database engine.
* **SQL (Jinja):** Business logic and custom macros.

## ⚙️ Project Architecture

1.  **Staging:** Initial cleaning of raw data, data type standardization, and NULL handling.
2.  **Intermediate:** Category unification (Full Joins) to cross-reference winners, prizes, and venues across different years.
3.  **Marts (Final):** Business-ready tables for analysis:
    * Country Medal Rankings.
    * All-time Athlete Rankings (Gold medals).
    * Prize Money Analysis.

## 📸 Snapshots
The project implements **dbt Snapshots** to detect historical data changes (SCD Type 2), allowing for the tracking of modifications in:
* Competition years.
* Athlete nationalities.
* Winner corrections or updates.

## 🛠️ Custom Macros
DRY (Don't Repeat Yourself) macros were developed to maintain clean code:
* `clean_money`: Handles currency formatting and type casting.
* `clean_citations`: Removes citation brackets (e.g., `[41]`) from text fields.
* `standardize_country`: Normalizes country names for accurate grouping.

## ▶️ How to Run

```bash
# Install dependencies
uv run dbt deps

# Run models
uv run dbt run

# Run snapshots to capture data changes
uv run dbt snapshot

# Generate and view documentation

uv run dbt docs generate
uv run dbt docs serve
```
