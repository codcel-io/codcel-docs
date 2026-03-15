<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BETADIST Function

The `BETADIST` function in Excel calculates the cumulative beta probability density function. It's used to study variability of the proportions in samples drawn from populations. For instance, it can be used in quality control processes where the aim is to measure the defect rate in a production line.

### Syntax:

    BETADIST(x, alpha, beta, [A], [B])


- **x**: The value at which you want to evaluate the function, where `A ≤ x ≤ B`.
- **alpha**: A parameter of the distribution, must be greater than 0.
- **beta**: Another parameter of the distribution, must also be greater than 0.
- **A** (optional): The lower bound of the interval of x. If omitted, A = 0.
- **B** (optional): The upper bound of the interval of x. If omitted, B = 1.

### Example:

1. `=BETADIST(0.5, 2, 3)` would calculate the cumulative beta distribution function value for `x = 0.5` with `alpha = 2` and `beta = 3`, within the default interval `[0, 1]`.

> **Note**: In Excel 2010 and later versions, the `BETADIST` function has been replaced with the `BETA.DIST` function, which offers improved accuracy and additional functionality. However, `BETADIST` remains available for compatibility with earlier versions of Excel.