<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MAXIFS Function

The `MAXIFS` function in Excel is used to **find the maximum value in a range that meets one or more conditions (
criteria)**. This function is particularly useful when you need to evaluate datasets with specific filtering criteria to
determine the largest value that matches those criteria.

### Key Features of MAXIFS:

- Allows multiple criteria to filter the dataset before finding the maximum value.
- Supports logical operators like greater than (`>`), less than (`<`), equal to (`=`), and wildcards (`*`, `?`) for
  string matching in conditions.
- Can handle numbers, dates, text, and cell references as part of the criteria.

### Syntax:

```plaintext
MAXIFS(max_range, criteria_range1, criteria1, [criteria_range2, criteria2], ...)
```

- **max_range**: The range of cells containing the values to evaluate and find the maximum value.
- **criteria_range1**: The range of cells to apply the first criteria.
- **criteria1**: The condition or criteria to apply to `criteria_range1`.
- **criteria_range2, criteria2...**: Optional. Additional ranges and conditions.

### How It Works:

1. Identifies all the values in `max_range` that meet the criteria specified in the `criteria_range` and `criteria`
   pairs.
2. Returns the largest value from the filtered dataset.

### Examples:

1. **Basic MAXIFS with Single Criterion**:
   Suppose the following dataset:

   | A (Regions) | B (Sales) |
   |-------------|-----------|
   | North       | 500       |
   | South       | 800       |
   | North       | 700       |
   | South       | 600       |

   Formula:
   ```excel
   =MAXIFS(B2:B5, A2:A5, "North")
   ```
   Result: `700` (maximum sales value for "North").

2. **MAXIFS with Numeric Criteria**:
   In the same dataset:
   ```excel
   =MAXIFS(B2:B5, B2:B5, ">600")
   ```
   Result: `800` (maximum value greater than `600`).

3. **MAXIFS with Multiple Criteria**:
   Suppose the dataset includes a new column for months:

   | A (Regions) | B (Sales) | C (Month) |
      |-------------|-----------|-----------|
   | North       | 500       | January   |
   | South       | 800       | January   |
   | North       | 700       | February  |
   | South       | 600       | February  |

   Formula:
   ```excel
   =MAXIFS(B2:B5, A2:A5, "North", C2:C5, "February")
   ```
   Result: `700` (maximum sales for "North" in February).

4. **Using Wildcards for Text Criteria**:
   Suppose the following regions:

   | A (Regions) | B (Sales) |
      |-------------|-----------|
   | North-East  | 500       |
   | North-West  | 700       |
   | South       | 600       |

   Formula:
   ```excel
   =MAXIFS(B2:B4, A2:A4, "North*")
   ```
   Result: `700` (maximum sales in regions starting with "North").

5. **Handling Dates as Criteria**:
   Suppose this dataset:

   | A (Dates)      | B (Sales) |
      |----------------|-----------|
   | 01-Jan-2023    | 400       |
   | 15-Jan-2023    | 600       |
   | 01-Feb-2023    | 800       |

   Formula:
   ```excel
   =MAXIFS(B2:B4, A2:A4, ">=01-Jan-2023", A2:A4, "<01-Feb-2023")
   ```
   Result: `600` (maximum sales in January 2023).

---

### Notes:

- **Range Sizes**:
    - Each `criteria_range` must have the same size as `max_range`; otherwise, Excel will return a `#VALUE!` error.
- **Blank Cells**:
    - Blank cells in `max_range` are ignored when calculating the result.
- **Logical Values**:
    - Logical values (e.g., `TRUE`, `FALSE`) in `criteria_range` are evaluated as `1` and `0`, respectively.
- **Error Handling**:
    - If no values meet the criteria, the formula returns a `0`.

### Applications:

- **Sales Analysis**: Determine the highest sales figure for a specific region, salesperson, or time frame.
- **Financial Reporting**: Identify the maximum income or expense in certain categories.
- **Data Filtering**: Extract the max value from a subset of data meeting strict logical filters.

> **Tip**: Combine `MAXIFS` with other functions like `MINIFS` or `AVERAGEIF` to perform advanced data filtering and
analysis.