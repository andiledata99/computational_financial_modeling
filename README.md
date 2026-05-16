# Computational Financial Modeling

## Project Overview

This repository demonstrates a small-scale financial data engineering pipeline built on Microsoft SQL Server. It includes database provisioning, schema creation, sample data ingestion, and analytical formula questions for financial modeling tasks.

## Business Context

The project is designed for financial engineering use cases such as interest calculations, compounding growth, hire purchase installments, inflation projections, depreciation modeling, and effective annual rate analysis.

## Repository Structure

- `scripts/1.creating_database.sql` - Creates the `FinancialEngineeringDB` database if it does not exist.
- `scripts/2.creating_financial_tasks_table.sql` - Defines the `FinancialTasks` table and enforces decimal precision for financial accuracy.
- `scripts/3.inserting_data_into_table.sql` - Loads sample financial task records used for analysis and modeling.
- `scripts/4.Answers.sql` - Contains practical assessment query answers and implementation examples for financial formulas.
- `project_framework/computational_financial_modeling_(SQL)_questions.pdf` - The original assessment question set for reference.

## How to Run

1. Open Microsoft SQL Server Management Studio (SSMS) or use `sqlcmd`.
2. Run `scripts/1.creating_database.sql` to create the target database.
3. Run `scripts/2.creating_financial_tasks_table.sql` to build the table schema.
4. Run `scripts/3.inserting_data_into_table.sql` to insert sample records.
5. Run `scripts/4.Answers.sql` to execute the financial calculations.

Example command using `sqlcmd`:

```powershell
sqlcmd -S localhost -i "scripts\1.creating_database.sql"
sqlcmd -S localhost -i "scripts\2.creating_financial_tasks_table.sql"
sqlcmd -S localhost -i "scripts\3.inserting_data_into_table.sql"
sqlcmd -S localhost -i "scripts\4.Answers.sql"
```

## Data Model

`FinancialTasks`
- `TaskID` (INT, Primary Key)
- `ModelName` (VARCHAR(100), NOT NULL)
- `Principal` (DECIMAL(19,4))
- `AnnualRate` (DECIMAL(19,4))
- `TermYears` (INT)
- `Frequency` (INT, DEFAULT 1)

Design rationale:
- `DECIMAL(19,4)` ensures high-precision financial calculations.
- The schema is intentionally simple for a teaching/assessment pipeline, but production-ready patterns are noted below.

## Data Engineering Standards Applied

- Idempotent SQL scripting: each script can be rerun without creating duplicate objects.
- Explicit schema definitions and data types.
- Sample dataset includes multiple financial formulas and frequency scenarios.
- Documentation captures the execution process and data model.

## Recommended Enhancements for Production

To align this repository with real-world data engineering practices, the next steps are:

- Add an ETL orchestration layer (Airflow, dbt, Azure Data Factory, or equivalent).
- Introduce staging/curated zones for raw, transformed, and analytical data.
- Add data validation and quality checks for values such as rate ranges and non-null fields.
- Add automated tests and CI/CD for SQL deployments.
- Add metadata and business glossary documentation.

## Contribution

If you want to extend this project, consider adding:

- A Python or Spark-based ingestion pipeline.
- Automated schema migrations.
- Additional financial data sources and batch load logic.
- A `docs/` folder containing data lineage, source-to-target mapping, and PM/analytics notes.

