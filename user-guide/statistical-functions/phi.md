<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PHI Function

The `PHI` function in Excel is used to **return the value of the density function for a standard normal distribution**
at a given value. This function is commonly used in statistics to evaluate probabilities and analyze data under a normal
distribution curve.

### Key Features of PHI:

- **Standard Normal Distribution**: Computes the density of the standard normal distribution, which has a mean of 0 and
  a standard deviation of 1.
- **Single Input Value**: Takes a single numeric argument and calculates the height of the probability density function
  at that point.
- **Useful in Probability and Statistics**: Frequently applied in fields like finance, data science, and risk analysis.
- **Positive Output**: The result is always a non-negative value, as it represents the height of the curve.

### Syntax:

```plaintext
PHI(x)
```

- **x**: Required. The numeric value for which to calculate the density of the standard normal distribution.

### How It Works:

The `PHI` function calculates the result using the formula for the **standard normal probability density function**:

```plaintext
PHI(x) = (1 / √(2π)) * e^(-x^2 / 2)
```

Where:

- \( e \) is the base of the natural logarithm.
- \( π \) is the mathematical constant Pi.

This formula determines the height of the standard normal curve at the point \( x \).

### Examples:

1. **Basic Example**:
   To calculate the value of the density function at \( x = 0 \):
   ```excel
   =PHI(0)
   ```
   Result: `0.39894228`

2. **Positive Input**:
   To calculate the density at \( x = 1.5 \):
   ```excel
   =PHI(1.5)
   ```
   Result: `0.1295176`

3. **Negative Input**:
   To calculate the density at \( x = -2 \):
   ```excel
   =PHI(-2)
   ```
   Result: `0.05399097`

4. **Large Positive Input**:
   To calculate the density at \( x = 4 \):
   ```excel
   =PHI(4)
   ```
   Result: `0.00013383`

### Notes:

- **Input Restrictions**:
    - The `x` value can be any real number (positive, negative, or 0).
    - If `x` is non-numeric, Excel will return a `#VALUE!` error.

- **Use Case**:
    - Use `PHI` when you need the height of the standard normal curve at a given point, commonly for tasks like
      calculating probabilities or visualizing the standard normal distribution.

- **Complementary Function**:
    - The `NORM.DIST` function is related but evaluates the **cumulative distribution function** or the full area under
      the curve up to a given \( x \), rather than the density at \( x \).

### Applications:

- **Data Analysis**: Compute and visualize normal distribution curves.
- **Finance**: Analyze asset returns or risk under normal distribution assumptions.
- **Statistical Modeling**: Evaluate likelihoods and densities for standard normal values.

> **Tip**: The `PHI` function is limited to the standard normal distribution. For distributions with different means or
> standard deviations, use the `NORM.DIST` function instead.