<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COMBINA Function

The `COMBINA` function in Excel is used to calculate the number of combinations (or subsets) that can be created by
selecting a specific number of items from a larger set, **with repetitions allowed**. This function is useful in
probability, statistics, or combinatorial analysis when repetition is considered.

### Syntax:

    COMBINA(number, number_chosen)

- **number**: This is a required argument. It specifies the total number of items in the set.
- **number_chosen**: This is a required argument. It specifies the number of items to choose from the set (with
  repetition allowed).

The function calculates combinations with repetition using the formula:

    COMBINA(number, number_chosen) = (number + number_chosen - 1)! / 
                                      (number_chosen! * (number - 1)!)

### Examples:

1. `=COMBINA(5, 2)`  
   Calculates the number of ways to choose 2 items from a set of 5 items, allowing repetition.  
   **Result**: `15`

2. `=COMBINA(4, 3)`  
   Calculates the number of ways to choose 3 items from a set of 4 items, allowing repetition.  
   **Result**: `20`

3. `=COMBINA(3, 1)`  
   Calculates the number of ways to choose 1 item from a set of 3 items, allowing repetition.  
   **Result**: `3`

### Notes:

- The `COMBINA` function works only with non-negative integers. If either argument is non-integer or negative, Excel
  will return a `#NUM!` error.
- The `number_chosen` argument must be greater than or equal to 0, or the function will return a `#NUM!` error.
- Unlike `COMBIN`, the `COMBINA` function accounts for repetitions, making it suitable for scenarios where items can be
  selected multiple times.

> **Tip**: Use the `COMBINA` function to calculate scenarios involving repeated selections, such as arrangements of
colored balls where each color can be chosen multiple times.