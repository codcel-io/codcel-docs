<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LOGNORMDIST Function

The `LOGNORMDIST` function in Excel is used to return the cumulative lognormal distribution of a value `x`. The
lognormal distribution describes a continuous distribution of a random variable whose natural logarithm is normally
distributed. This function is often used in financial modeling and risk analysis.

### Syntax

```excel
LOGNORMDIST(x, mean, standard_dev)
```

### Parameters

- **x**: The value at which to evaluate the function. This must be a positive number.
- **mean**: The mean of the natural logarithm of the distribution.
- **standard_dev**: The standard deviation of the natural logarithm of the distribution. This must be a positive number.

### Notes

- If `x` is ≤ 0, or if `standard_dev` ≤ 0, the function will return an error.
- The cumulative distribution function (CDF) is calculated as:  
  \[
  \text{LOGNORMDIST}(x) = \frac{1}{x \cdot \sigma \cdot \sqrt{2\pi}} e^{-\frac{(\ln(x) - \mu)^2}{2\sigma^2}}
  \]
  Where:
    - \( x \) is the input value.
    - \( \mu \) is the mean of the natural logarithm of the distribution (mean).
    - \( \sigma \) is the standard deviation of the natural logarithm of the distribution (standard_dev).

### Deprecation

In recent versions of Excel (2010 and later), the `LOGNORMDIST` function has been replaced with `LOGNORM.DIST`. The
newer version provides more precise control over cumulative vs. probability density functions:

- Use `LOGNORM.DIST` for newer models to specify cumulative (TRUE) or probability density (FALSE) explicitly using an
  additional argument.

### Example

```excel
=LOGNORMDIST(4, 3.5, 1.2)
```

This returns the cumulative lognormal distribution of the value `4` with a mean of `3.5` and a standard deviation of
`1.2`.