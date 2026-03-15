<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## Z.TEST Function

The `Z.TEST` function in Excel is used to **calculate the one-tailed probability value of a z-test**. It is typically
used in hypothesis testing to determine whether the mean of a dataset is significantly different from a specific value.

### Key Features of Z.TEST:

- **One-Tailed Test**: It calculates the probability that a sample mean is greater than a specified hypothesized
  population mean.
- **Works with the Normal Distribution**: Assumes the dataset follows a normal distribution.
- **Returns a p-value**: The result is a probability value that helps assess the significance of the difference.

### Syntax:

```plaintext
Z.TEST(array, x, [sigma])
```

- **array**: Required. The range of numbers in the sample dataset.
- **x**: Required. The hypothesized population mean to compare the sample mean against.
- **sigma**: Optional. The population standard deviation. If omitted, the function uses the sample standard deviation to
  estimate the population standard deviation.

### How It Works:

1. Calculates the mean (`m`) and standard deviation (`s`) of the sample dataset (if population standard deviation is not
   provided).
2. Computes the z-value using the formula:

   ```plaintext
   z = (m - x) / (s / √n)
   ```

   where:
    - `m` = sample mean
    - `x` = hypothesized population mean
    - `s` = sample standard deviation (or population standard deviation if provided)
    - `n` = sample size

3. Finds the one-tailed p-value corresponding to this z-value from the standard normal distribution.

### Examples:

1. **Basic Use**:

   To test whether the mean of the dataset `{10, 12, 15, 20, 25}` differs from `18` with no population standard
   deviation provided:

   ```excel
   =Z.TEST({10, 12, 15, 20, 25}, 18)
   ```

   **Explanation**:
    - Sample mean (`m`) = `(10 + 12 + 15 + 20 + 25) / 5 = 16.4`
    - Sample standard deviation is computed automatically.
    - Z.TEST returns the one-tailed probability that the sample mean is greater than `18`.

2. **Including Population Standard Deviation**:

   If the population standard deviation is known to be `5`, you can include it in the formula:

   ```excel
   =Z.TEST(A1:A5, 18, 5)
   ```

   **Explanation**:
    - The function uses the provided population standard deviation `5` instead of calculating the sample standard
      deviation.

3. **Using Named Ranges**:

   Assuming the dataset is named `Scores`, test against a mean of `20`:

   ```excel
   =Z.TEST(Scores, 20)
   ```

   This calculates the z-test probability for the named range `Scores`.

### Notes:

- **One-Tailed Test**:
    - `Z.TEST` returns the probability that the sample mean is greater than the hypothesized mean (`x`).
    - For a two-tailed test, multiply the result by `2`.

- **Error Handling**:
    - If `array` contains fewer than 2 numbers, `Z.TEST` returns a `#NUM!` error.
    - If `sigma` or values within the dataset are invalid, it may return errors like `#VALUE!`.

- **Logical Values**:
    - Logical values and text representations of numbers in the dataset are ignored.

### Applications:

- **Statistical Hypothesis Testing**: Determine if a sample mean is significantly different from a hypothesized value.
- **Quality Control**: Check if a production sample mean deviates significantly from the target level.
- **Scientific Research**: Analyze data in controlled experiments to test hypotheses.

> **Tip**: Use `NORM.S.DIST` to further analyze the z-value or to calculate probabilities manually if necessary.