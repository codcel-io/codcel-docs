<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COMBIN Function

The `COMBIN` function in Excel is used to calculate the number of combinations (or subsets) that can be created by
selecting a specific number of items from a larger set. This is commonly used in probability and statistics.

### Syntax:

    COMBIN(number, number_chosen)

- **number**: This is a required argument. It specifies the total number of items in the set.
- **number_chosen**: This is a required argument. It specifies the number of items to choose from the set.

The function calculates combinations using the formula:

    COMBIN(number, number_chosen) = number! / (number_chosen! * (number - number_chosen)!)

### Examples:

1. `=COMBIN(5, 2)`  
   Calculates the number of ways to choose 2 items from a set of 5 items.  
   **Result**: `10`

2. `=COMBIN(10, 3)`  
   Calculates the number of ways to choose 3 items from a set of 10 items.  
   **Result**: `120`

3. `=COMBIN(8, 1)`  
   Calculates the number of ways to choose 1 item from a set of 8 items.  
   **Result**: `8`

### Notes:

- The `COMBIN` function only works with non-negative integers. If either argument is non-integer or negative, Excel will
  return a `#NUM!` error.
- The `number_chosen` argument must be less than or equal to the `number` argument, or the function will also return a
  `#NUM!` error.
- This function does not account for order in selections—use `PERMUT` if the order of items matters.

> **Tip**: Use the `COMBIN` function when solving problems related to lottery odds, project planning, or any other
scenario where you need to calculate combinations without concern for order.