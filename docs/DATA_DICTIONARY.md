# Data Dictionary

## `FinancialTasks`

| Column | Type | Description | Example |
|---|---|---|---|
| `TaskID` | `INT` | Primary key for each financial task record. | `1` |
| `ModelName` | `VARCHAR(100)` | Descriptive name of the financial model or calculation. | `Compound Interest` |
| `Principal` | `DECIMAL(19,4)` | Initial amount subject to interest, depreciation, or growth. | `12000.0000` |
| `AnnualRate` | `DECIMAL(19,4)` | Annual rate expressed as a decimal fraction. | `0.0650` |
| `TermYears` | `INT` | Length of the modeling period in years. | `8` |
| `Frequency` | `INT` | Number of compounding or accrual periods per year. Defaults to `1`. | `12` |

## Notes

- `DECIMAL(19,4)` ensures financial precision and prevents rounding errors in intermediate calculations.
- `AnnualRate` is stored as a decimal rate, not a percentage (for example, `0.07` means 7%).
- `Frequency` can express monthly, quarterly, semi-annual, or annual compounding.

## Business rules

- `TaskID` must be unique and immutable.
- `ModelName` should be a short human-readable label for the calculation.
- `Principal` should be non-negative.
- `AnnualRate` should typically be between `0.0` and `1.0` for valid rate scenarios.
- `TermYears` should be zero or positive; zero is used for special calculations such as doubling time.
- `Frequency` should be a positive integer.
