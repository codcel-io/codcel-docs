<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# GROUPBY Function

The `GROUPBY` function in Excel is used to **group data by one or more row fields and aggregate values using a specified function**. It creates a summary table from a dataset by grouping rows that share common values and applying an aggregation (such as SUM, AVERAGE, or COUNT) to the associated values. This function is ideal for producing pivot-table-style summaries directly in formulas.

## Key Features of `GROUPBY`:

- Groups rows by one or more fields and aggregates associated values in a single formula.
- Supports any aggregation function, including `SUM`, `AVERAGE`, `COUNT`, `MAX`, `MIN`, and custom `LAMBDA` functions.
- Automatically returns a dynamic spill array that updates when source data changes.
- Optionally includes field headers, grand totals, and subtotals in the output.
- Supports sorting the grouped results in ascending or descending order.
- Accepts an optional filter array to include only rows that meet specific criteria.

## Syntax:

```plaintext
GROUPBY(row_fields, values, function, [field_headers], [total_depth], [sort_order], [filter_array])
```

- **row_fields**: The column(s) used to group the data. Can be a single column or multiple columns for nested grouping.
- **values**: The column(s) containing data to aggregate for each group.
- **function**: The aggregation function to apply to each group (e.g., `SUM`, `AVERAGE`, `COUNT`, `MAX`, `MIN`, or a custom `LAMBDA`).
- **field_headers** (optional): Specifies whether headers are present and how to handle them. Defaults to automatic detection.
  - `0` — No headers
  - `1` — Yes, but don't show
  - `2` — No headers, but generate
  - `3` — Yes, and show
- **total_depth** (optional): Controls grand total and subtotal display. Defaults to no totals.
  - `0` — No totals
  - `1` — Grand total at bottom
  - `2` — Grand total and subtotals
  - `-1` — Grand total at top
  - `-2` — Grand total at top and subtotals
- **sort_order** (optional): Specifies the sort order for grouped results.
  - `0` — No specific sort (keeps original data order)
  - `1` — Ascending order
  - `-1` — Descending order
- **filter_array** (optional): A Boolean array (TRUE/FALSE) that filters which rows to include before grouping. Must be the same height as `row_fields` and `values`.

## How `GROUPBY` Works:

1. Reads the source data from `row_fields` and `values`.
2. If a `filter_array` is provided, excludes rows where the filter is FALSE.
3. Groups rows that share the same value(s) in the `row_fields` columns.
4. Applies the specified aggregation `function` to the `values` for each group.
5. Optionally sorts the results and appends totals/subtotals based on the parameters.
6. Returns the grouped summary as a dynamic spill array.

## Examples:

### 1. Basic Grouping with SUM:

Assume A2:A10 contains regions ("East", "West", "North") and B2:B10 contains sales amounts:

```excel
=GROUPBY(A2:A10, B2:B10, SUM)
```

**Result:**
```
East    4500
North   3200
West    5100
```

Explanation: Groups the sales data by region and returns the total sales for each region.

### 2. Grouping with AVERAGE:

```excel
=GROUPBY(A2:A10, B2:B10, AVERAGE)
```

**Result:**
```
East    1500
North   1067
West    1700
```

Explanation: Calculates the average sales amount for each region.

### 3. Grouping with COUNT:

```excel
=GROUPBY(A2:A10, B2:B10, COUNT)
```

**Result:**
```
East    3
North   3
West    3
```

Explanation: Counts the number of entries in each region group.

### 4. Including Headers:

Assume A1:A10 has "Region" as a header in A1 and B1:B10 has "Sales" as a header in B1:

```excel
=GROUPBY(A1:A10, B1:B10, SUM, 3)
```

**Result:**
```
Region  Sales
East    4500
North   3200
West    5100
```

Explanation: Setting `field_headers` to 3 includes the column headers in the output.

### 5. With Grand Total:

```excel
=GROUPBY(A2:A10, B2:B10, SUM, , 1)
```

**Result:**
```
East    4500
North   3200
West    5100
        12800
```

Explanation: Setting `total_depth` to 1 appends a grand total row at the bottom of the results.

### 6. Sorted in Descending Order:

```excel
=GROUPBY(A2:A10, B2:B10, SUM, , , -1)
```

**Result:**
```
West    5100
East    4500
North   3200
```

Explanation: Setting `sort_order` to -1 sorts the grouped results from highest to lowest aggregated value.

### 7. With a Filter Array:

Assume C2:C10 contains dates and you want to include only rows from 2024:

```excel
=GROUPBY(A2:A10, B2:B10, SUM, , , , YEAR(C2:C10)=2024)
```

**Result:**
```
East    2100
West    3400
```

Explanation: The `filter_array` limits the grouping to only rows where the year is 2024, excluding "North" because it had no 2024 entries in this example.

### 8. Multi-Column Grouping:

Assume A2:A10 contains regions, B2:B10 contains product categories, and C2:C10 contains sales:

```excel
=GROUPBY(HSTACK(A2:A10, B2:B10), C2:C10, SUM)
```

**Result:**
```
East    Electronics   2500
East    Furniture     2000
North   Electronics   1800
North   Furniture     1400
West    Electronics   3000
West    Furniture     2100
```

Explanation: Using `HSTACK` to combine two columns as `row_fields` creates nested grouping by both region and product category.

### 9. Using a Custom LAMBDA Function:

```excel
=GROUPBY(A2:A10, B2:B10, LAMBDA(x, PERCENTILE.INC(x, 0.9)))
```

**Result:**
```
East    2800
North   2100
West    3500
```

Explanation: Applies a custom LAMBDA that calculates the 90th percentile of sales values within each group instead of a built-in aggregation.

## Notes:

- `GROUPBY` returns a dynamic spill array. The output range must have enough empty cells to accommodate the result, or a `#SPILL!` error will occur.
- The `row_fields` and `values` arguments must have the same number of rows. If they don't, a `#VALUE!` error is returned.
- The `function` argument accepts both built-in functions (like `SUM`, `AVERAGE`, `COUNT`) and custom `LAMBDA` functions for advanced aggregations.
- When using multiple columns for `row_fields`, combine them with `HSTACK` to create nested groupings.
- The `filter_array` must produce a Boolean array the same height as the source data. Rows with FALSE are excluded before grouping.
- If all rows are filtered out, `GROUPBY` returns a `#CALC!` error.
- `GROUPBY` is available in Microsoft 365 and may not be available in older versions of Excel.
- Unlike PivotTables, `GROUPBY` results are formula-driven and update automatically when source data changes.

## Applications:

- **Sales Summaries**: Group sales data by region, product, or salesperson and calculate totals, averages, or counts.
- **Financial Reporting**: Aggregate expenses by category or department for budget analysis.
- **Data Consolidation**: Combine duplicate entries by grouping on a key field and summing or averaging associated values.
- **Dynamic Dashboards**: Build formula-based summaries that refresh automatically without PivotTables.
- **Filtered Aggregation**: Use the filter array to create conditional summaries, such as grouping only data from a specific time period or meeting certain criteria.
- **Multi-Level Grouping**: Combine multiple columns with `HSTACK` to produce nested group-by-group breakdowns.

## Related Functions:

- **PIVOTBY**: Groups data by both row and column fields, creating a two-dimensional pivot-style summary.
- **HSTACK**: Stacks arrays horizontally — used to combine multiple columns for multi-field grouping.
- **VSTACK**: Stacks arrays vertically — useful for combining grouped results from different sources.
- **SORT**: Sorts an array by specified columns, complementing `GROUPBY` for custom ordering.
- **FILTER**: Returns rows from a range that meet specified criteria — can be used alongside or as an alternative to the `filter_array` parameter.
- **UNIQUE**: Extracts unique values from a range — related to the grouping concept of identifying distinct categories.
- **LAMBDA**: Creates custom functions that can be passed as the aggregation argument in `GROUPBY`.

> **Tip:** Combine `GROUPBY` with `HSTACK` for multi-column grouping and a custom `LAMBDA` for aggregation to replicate complex PivotTable functionality entirely within formulas. For example, `=GROUPBY(HSTACK(A2:A100, B2:B100), C2:C100, LAMBDA(x, TEXTJOIN(", ", TRUE, x)))` groups by two fields and concatenates the values instead of summing them.