<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ATAN2 Function

The `ATAN2` function in Excel returns the arctangent of the quotient of its arguments, in radians between `-π` and `π`. It provides the angle theta of an (x, y) point, giving a result from `0` to `2π`.

Unlike the `ATAN` function, which only takes one argument, `ATAN2` takes two arguments. It's useful because it considers the signs of both arguments, distinguishing between, for example, angles in the first and third quadrants.

### Syntax:

    ATAN2(x_num, y_num)

- **x_num**: The x-coordinate.
- **y_num**: The y-coordinate.

### Examples:

1. `=ATAN2(1, 1)` would return a value in radians, approximately 0.7854 (or 45° when converted to degrees), as this is the angle corresponding to the point (1,1) in the first quadrant.
2. `=ATAN2(-1, -1)` would return approximately -2.3562 radians (or -135°), representing the third quadrant.
3. `=ATAN2(A1, A2)` would return the arctangent based on the x and y values in cells A1 and A2, respectively.

> **Note**: If you want the result in degrees rather than radians, you can use the formula `=DEGREES(ATAN2(x_num, y_num))`.