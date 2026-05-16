# Computational Financial Modeling

## Project Overview

This repository contains a compact financial data engineering pipeline implemented in Microsoft SQL Server. It demonstrates:

- database provisioning
- financial schema design
- sample data loading
- analytical SQL calculations for common financial models

## Business Context

This project is built for financial engineering scenarios, including:

- simple and compound interest calculations
- hire purchase installments
- inflation projections
- reducing balance depreciation
- effective annual rate analysis

## Repository Structure

- `sql/01_create_database.sql` — creates the `FinancialEngineeringDB` database if it does not already exist
- `sql/02_create_financial_tasks_table.sql` — creates the `FinancialTasks` table with precise financial data types
- `sql/03_load_financial_tasks.sql` — inserts sample financial records for analysis
- `sql/04_financial_analysis.sql` — runs financial calculation examples and query answers
- `reference/financial_modeling_questions.pdf` — original assessment reference document
- `docs/architecture.md` — pipeline and architecture guidance
- `docs/data_dictionary.md` — table definitions and business rules
- `docs/project_overview.md` — project scope and improvement roadmap

## How to Run

1. Open Microsoft SQL Server Management Studio (SSMS) or use `sqlcmd`.
2. Execute the scripts in order:
   - `sql/01_create_database.sql`
   - `sql/02_create_financial_tasks_table.sql`
   - `sql/03_load_financial_tasks.sql`
   - `sql/04_financial_analysis.sql`

### Example command using `sqlcmd`:

```powershell
sqlcmd -S localhost -i "sql\01_create_database.sql"
sqlcmd -S localhost -i "sql\02_create_financial_tasks_table.sql"
sqlcmd -S localhost -i "sql\03_load_financial_tasks.sql"
sqlcmd -S localhost -i "sql\04_financial_analysis.sql"
```

## Data Model

### Table: `FinancialTasks`

- `TaskID` — `INT`, primary key
- `ModelName` — `VARCHAR(100)`, not null
- `Principal` — `DECIMAL(19,4)`
- `AnnualRate` — `DECIMAL(19,4)`
- `TermYears` — `INT`
- `Frequency` — `INT`, default `1`

## Design Notes

- `DECIMAL(19,4)` is used for financial precision and reliable calculations
- `AnnualRate` is stored as a decimal fraction (for example, `0.07` means 7%)
- `Frequency` supports annual, semi-annual, quarterly, and monthly scenarios

## Data Engineering Standards Applied

- idempotent SQL scripts — can be rerun safely
- explicit schema definitions and data types
- sample dataset design across multiple financial scenarios
- documentation for execution flow and model design

## Contribution

To extend this repository, consider adding:

- a Python or Spark-based ingestion pipeline
- automated schema migrations and deployment
- data quality checks and validation rules
- a `tests/` folder for SQL regression and data tests
- a `docs/` folder for lineage, glossary, and business rules
