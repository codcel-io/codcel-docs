<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    RANDBETWEEN(bottom, top)

- **bottom**: The smallest integer value that can be returned.
- **top**: The largest integer value that can be returned.

### Description:

The `RANDBETWEEN` function returns a random integer between the specified `bottom` and `top` values (inclusive). It is
often used when you need random whole numbers within a defined range.

### Examples:

1. `=RANDBETWEEN(1, 10)`:
    - Returns a random integer between `1` and `10`.

2. `=RANDBETWEEN(50, 100)`:
    - Returns a random integer between `50` and `100`.

3. `=RANDBETWEEN(-10, 10)`:
    - Returns a random integer between `-10` and `10`.

4. `=RANDBETWEEN(0, 0)`:
    - Always returns `0` because both `bottom` and `top` are the same.

5. `=RANDBETWEEN(-5, -1)`:
    - Returns a random integer between `-5` and `-1`.

> **Note**: The `RANDBETWEEN` function recalculates its value each time the worksheet changes or is recalculated. To
> freeze the random value, copy the cell and paste it as a static value.