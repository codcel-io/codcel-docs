<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    RANDARRAY([rows], [columns], [min], [max], [whole_number])

- **rows** *(optional)*: The number of rows to fill with random numbers. Defaults to `1` if omitted.
- **columns** *(optional)*: The number of columns to fill with random numbers. Defaults to `1` if omitted.
- **min** *(optional)*: The smallest value for the random numbers. Defaults to `0` if omitted.
- **max** *(optional)*: The largest value for the random numbers. Defaults to `1` if omitted.
- **whole_number** *(optional)*: A logical value (`TRUE` or `FALSE`) specifying whether only whole numbers should be
  returned:
    - `TRUE`: Generates whole numbers.
    - `FALSE` or omitted: Generates decimal numbers.

### Examples:

1. `=RANDARRAY()`:
    - Returns a single random decimal between `0` and `1`.

2. `=RANDARRAY(3, 2)`:
    - Returns a `3x2` array of random decimal numbers between `0` and `1`.

3. `=RANDARRAY(2, 4, 5, 10)`:
    - Returns a `2x4` array of random decimal numbers between `5` and `10`.

4. `=RANDARRAY(3, 3, 1, 100, TRUE)`:
    - Returns a `3x3` array of random whole numbers between `1` and `100`.

5. `=RANDARRAY(5, 1, -10, 10, FALSE)`:
    - Returns a `5x1` array of random decimal numbers between `-10` and `10`.

> **Note**: The `RANDARRAY` function is a dynamic array formula, meaning it will automatically spill into adjacent
> cells. Ensure enough space is available in the worksheet to avoid a `#SPILL!` error.