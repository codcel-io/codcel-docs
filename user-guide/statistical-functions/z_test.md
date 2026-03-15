<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ZTEST Function

The `ZTEST` function in Excel is used to **calculate the one-tailed probability-value of a z-test**. It is typically
used in hypothesis testing to determine whether a given sample comes from a population with a specified mean.

### Key Features of ZTEST:

- **Hypothesis Testing**: Helps determine how likely it is that a specific sample belongs to a population with a given
  mean.
- **Returns a P-Value**: Represents the probability that the sample mean is different from the population mean (
  one-tailed test).
- **Statistical Analysis**: Useful for z-tests involving known population means and standard deviations.

### Syntax:

```plaintext
ZTEST(array, x, [sigma])
```

- **array**: Required. The array or range of values representing your sample data.
- **x**: Required. The sample mean that you want to test.
- **sigma**: Optional. The population standard deviation. If omitted, Excel uses the sample standard deviation.

### How It Works:

The `ZTEST` function calculates the probability-value (P-value) for a one-tailed z-test. It assumes that the population
is normally distributed, and uses the formula:

```plaintext
Z = (x - μ) / (σ / √n)
```

Where:

- `x` is the sample mean.
- `μ` is the population mean (assumed to be the mean of the `array` if not explicitly provided).
- `σ` is the population standard deviation (or sample standard deviation if `sigma` is not provided).
- `n` is the sample size (the number of values in the `array`).

Excel then calculates the area under the normal curve to the right of this z-score to return the P-value.

### Examples:

1. **Basic Z-Test**:
   Assume a sample `{90, 110, 100}` and you want to test whether the sample mean `x = 105` comes from a population with
   mean `100` and standard deviation `10`:

   ```excel
   =ZTEST({90, 110, 100}, 105, 10)
   ```

   This will return the P-value, which you can interpret in the context of your hypothesis.

2. **Z-Test Without Known Population Standard Deviation**:
   If the population standard deviation is unknown, Excel will use the sample standard deviation from the data in the
   `array`:

   ```excel
   =ZTEST({85, 95, 105, 120}, 100)
   ```

   This scenario calculates the P-value using the sample's statistics.

3. **Using ZTEST for Hypothesis Testing**:
   You perform a z-test with a significance level of 0.05. If the result of the `ZTEST` is less than 0.05, you reject
   the null hypothesis:

   ```excel
   =IF(ZTEST({88, 92, 97, 100, 102}, 98, 5) < 0.05, "Reject Null", "Fail to Reject Null")
   ```

4. **Interpreting Results**:
    - A high P-value (e.g., greater than 0.05): The sample could plausibly come from the population with the given mean.
    - A low P-value (e.g., less than 0.05): The sample mean is significantly different from the population mean.

### Notes:

- Test Direction:
    - The `ZTEST` function always calculates the right-tailed P-value. If you need a two-tailed test, multiply the
      result by 2.
- Assumptions:
    - The population is normally distributed.
    - If `sigma` is not provided, the sample standard deviation is used, which assumes the sample is representative of
      the population.
- **Error Handling**:
    - The function will return `#N/A` if the `array` is empty.
    - Non-numeric inputs in the `array` will cause a `#VALUE!` error.

### Applications:

- **Hypothesis Testing**: Evaluate claims about population means, such as product quality or customer satisfaction
  scores.
- **Quality Control**: Assess whether process outputs differ significantly from expected values.
- **Statistical Research**: Test hypotheses in experimental or observational studies.

> **Tip**: Although `ZTEST` is useful, for more complex hypothesis tests where variances or sample sizes differ
> substantially, consider using Excel's `T.TEST` or statistical software.