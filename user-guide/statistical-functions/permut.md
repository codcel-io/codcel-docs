<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PERMUT Function

The `PERMUT` function in Excel is used to **calculate the number of permutations for a given number of objects chosen
from a larger set**. Permutations are arrangements of objects where the order matters.

### Key Features of PERMUT:

- **Order Matters**: Unlike combinations, permutations consider the arrangement of objects, making it useful in
  scenarios where order is important.
- **Efficient**: Quickly computes the exact number of permutations without manually performing the calculations.
- **Useful in Probability and Counting Problems**: Commonly applied in probability theory, statistics, and arrangements.

### Syntax:

```plaintext
PERMUT(number, number_chosen)
```

- **number**: Required. The total number of items in the set (a non-negative integer).
- **number_chosen**: Required. The number of items to be chosen for permutation (a non-negative integer that must be
  less than or equal to `number`).

### How It Works:

The formula for calculating permutations is given by:

```math
P(n, r) = n! / (n - r)!
```

Where:

- `n` is the total number of items (`number` argument).
- `r` is the number of items chosen (`number_chosen` argument).
- `!` denotes factorials (e.g., `4! = 4 × 3 × 2 × 1 = 24`).

### Examples:

1. **Basic Example**:
   To calculate the number of ways to arrange 3 objects chosen from a set of 5:
   ```excel
   =PERMUT(5, 3)
   ```
   Result: `60` permutations because there are 60 possible arrangements of 3 objects from 5.

2. **Choosing All Items**:
   To calculate the number of arrangements of all 4 objects in a set:
   ```excel
   =PERMUT(4, 4)
   ```
   Result: `24` permutations (`4! = 4 × 3 × 2 × 1 = 24`).

3. **Single Item Arrangements**:
   To calculate the number of arrangements when only 1 item is chosen from 6:
   ```excel
   =PERMUT(6, 1)
   ```
   Result: `6` permutations.

### Notes:

- **Range Check**:
    - If `number` or `number_chosen` is negative, Excel returns a `#NUM!` error.
    - If `number_chosen` is greater than `number`, Excel also returns a `#NUM!` error.
- **Non-integer Inputs**:
    - If non-integer values are provided, Excel truncates them to integers before performing calculations.
- **Maximum Limit**:
    - The resulting number of permutations cannot exceed the limits for large numbers in Excel; otherwise, an error will
      occur.

### Applications:

- **Business and Logistics**: Determine different orders of deliveries or task assignments.
- **Mathematics**: Solve permutations-based problems in probability and statistics.
- **Competitions**: Compute possible rankings or outcomes based on participant arrangements.
- **Science and Research**: Analyze permutations in various experiments.

> **Tip**: Use the `COMBIN` function if the order of the items does not matter when choosing objects from a set.