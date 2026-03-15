<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->




# NOT IMPLEMENT YET



## BETAINV Function

The `BETAINV` function in Excel returns the inverse of the cumulative beta probability density function (beta distribution). In other words, given a probability, `BETAINV` finds the corresponding x value. This can be particularly useful in statistical analyses where you want to determine a variable's value for a specific percentile within a beta distribution.

### Syntax:

    BETAINV(probability, alpha, beta, [A], [B])


- **probability**: The probability associated with the beta distribution, a value between 0 and 1.
- **alpha**: A parameter of the distribution, which must be greater than 0.
- **beta**: Another parameter of the distribution, which must also be greater than 0.
- **A** (optional): The lower bound to the interval of x. If omitted, A = 0.
- **B** (optional): The upper bound to the interval of x. If omitted, B = 1.

### Example:

1. `=BETAINV(0.4, 2, 3)` would return the x value for which the cumulative beta distribution function has a value of 0.4, given `alpha = 2` and `beta = 3`, and considering the default interval `[0, 1]`.

> **Note**: In Excel 2010 and later versions, the `BETAINV` function has been replaced by the `BETA.INV` function, which offers improved accuracy and additional functionality. However, `BETAINV` remains available for compatibility with earlier versions of Excel.