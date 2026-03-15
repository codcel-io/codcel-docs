<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Conditional Functions

This contains the list of conditional functions that are currently supported by Codcel.


## A

### [AVERAGEIF](./conditional-functions/average_if.md)
Calculates the average (arithmetic mean) of all cells that meet a specified condition.

- **Example:** `=AVERAGEIF(A1:A10, ">5")`

## C

### [COUNTIF](./conditional-functions/count_if.md)
Counts the number of cells within a range that meet a single specified criterion.

- **Example:** `=COUNTIF(A1:A10, ">5")`

## I

### [IF](./conditional-functions/if.md)
Checks whether a condition is met and returns one value if TRUE and another if FALSE.

- **Example:** `=IF(A1 > 10, "High", "Low")`

### [IFERROR](./conditional-functions/if_error.md)
Catches errors in a formula and replaces them with a specified alternative value.

- **Example:** `=IFERROR(A1/B1, "Error")`

### [IFS](./conditional-functions/ifs.md)
Checks multiple conditions and returns a value corresponding to the first true condition.

- **Example:** `=IFS(A1>=90, "A", A1>=80, "B", A1>=70, "C")`

## S

### [SUMIF](./conditional-functions/sum_if.md)
Sums the values in a range that meet a specified criterion.

- **Example:** `=SUMIF(A1:A10, ">5", B1:B10)`