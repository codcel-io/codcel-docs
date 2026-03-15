<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MINIFS Function

The `MINIFS` function in Excel is used to **find the minimum value in a range that meets one or more conditions (
criteria)**. This function is ideal for analyzing datasets where you need to filter data with specific criteria and
determine the smallest value that matches those criteria.

### Key Features of MINIFS:

- Allows multiple criteria to filter the dataset before finding the minimum value.
- Supports logical operators like less than (`<`), greater than (`>`), equal to (`=`), and wildcards (`*`, `?`) for
  string-based filtering.
- Handles numbers, dates, text, and cell references as part of the criteria.

### Syntax:

```plaintext
MINIFS(min_range, criteria_range1, criteria1, [criteria_range2, criteria2], ...)
```

- **min_range**: The range of cells containing the values to evaluate and find the minimum value.
- **criteria_range1**: The range of cells to apply the first criteria.
- **criteria1**: The condition or criteria to apply to `criteria_range1`.
- **criteria_range2, criteria2...**: Optional. Additional ranges and their corresponding conditions.

### How It Works:

1. Identifies the values in `min_range` that match the specified criteria in the `criteria_range` and `criteria` pairs.
2. Returns the smallest value from the filtered dataset.

### Examples:

1. **Basic MINIFS with Single Criterion**:
   Suppose the following dataset:

   | A (Regions) | B (Sales) |
   |-------------|-----------|
   | North       | 500       |
   | South       | 800       |
   | North       | 700       |
   | South       | 600       |

   Formula:
   ```excel
   =MINIFS(B2:B5, A2:A5, "North")
   ```
   Result: `500` (minimum sales value for "North").

2. **MINIFS with Numeric Criteria**:
   Using the same dataset:
   ```excel
   =MINIFS(B2:B5, B2:B5, "<700")
   ```
   Result: `500` (minimum value less than `700`).

3. **MINIFS with Multiple Criteria**:
   Suppose the dataset is updated with a third column for months:

   | A (Regions) | B (Sales) | C (Month) |
      |-------------|-----------|-----------|
   | North       | 500       | January   |
   | South       | 800       | January   |
   | North       | 700       | February  |
   | South       | 600       | February  |

   Formula:
   ```excel
   =MINIFS(B2:B5, A2:A5, "South", C2:C5, "February")
   ```
   Result: `600` (minimum sales for "South" in February).

4. **Using Wildcards for Text Criteria**:
   Suppose the following dataset:

   | A (Regions) | B (Sales) |
      |-------------|-----------|
   | North-East  | 500       |
   | North-West  | 700       |
   | South       | 600       |

   Formula:
   ```excel
   =MINIFS(B2:B4, A2:A4, "North*")
   ```
   Result: `500` (minimum sales in regions starting with "North").

5. **Handling Dates as Criteria**:
   Suppose this dataset:

   | A (Dates)      | B (Sales) |
      |----------------|-----------|
   | 01-Jan-2023    | 400       |
   | 15-Jan-2023    | 600       |
   | 01-Feb-2023    | 800       |

   Formula:
   ```excel
   =MINIFS(B2:B4, A2:A4, ">=01-Jan-2023", A2:A4, "<01-Feb-2023")
   ```
   Result: `400` (minimum sales in January 2023).

---

### Notes:

- **Range Sizes**:
    - Each `criteria_range` must have the same dimensions as `min_range`; otherwise, Excel will return a `#VALUE!`
      error.
- **Blank Cells**:
    - Blank cells in `min_range` are ignored when calculating the result.
- **Logical Values**:
    - Logical values (e.g., `TRUE`, `FALSE`) in `criteria_range` are evaluated as `1` and `0`, respectively.
- **Error Handling**:
    - If no values meet the criteria, the formula returns `0`.

### Applications:

- **Sales Analysis**: Determine the smallest sales figure within specific regions, teams, or time periods.
- **Budget Reporting**: Find the minimum expense or cost category satisfying given conditions.
- **Data Analysis**: Extract the smallest value from subsets of data filtered by logical conditions.

> **Tip**: Combine `MINIFS` with similar functions like `MAXIFS` or `AVERAGEIF` to perform detailed data filtering and
calculations.