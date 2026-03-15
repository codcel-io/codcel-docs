<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## Excel's BETA.DIST Function

The `BETA.DIST` function in Excel returns the beta probability density function or the cumulative beta probability density function. This function can be applied in various fields, including finance and quality control, to analyze the distribution of proportions and variances.

### Syntax:

    BETA.DIST(x, alpha, beta, cumulative, [A], [B])


- **x**: The value at which you want to evaluate the function.
- **alpha**: A parameter of the distribution. It must be greater than 0.
- **beta**: Another parameter of the distribution. It must also be greater than 0.
- **cumulative**: A logical value (TRUE or FALSE). If TRUE, the function returns the cumulative distribution function. If FALSE, it returns the probability density function.
- **A** (optional): The lower bound of the interval of x. If omitted, A = 0.
- **B** (optional): The upper bound of the interval of x. If omitted, B = 1.

### Examples:

1. `=BETA.DIST(0.5, 2, 3, TRUE)` returns the cumulative beta distribution function value for `x = 0.5` with `alpha = 2` and `beta = 3` within the default interval `[0, 1]`.
2. `=BETA.DIST(0.5, 2, 3, FALSE)` returns the probability density function value for the same parameters.

> **Note**: The `BETA.DIST` function offers improved accuracy and added capabilities compared to its predecessor, the `BETADIST` function, in earlier Excel versions.