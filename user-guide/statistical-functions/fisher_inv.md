<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FISHERINV Function

The `FISHERINV` function in Excel calculates the **inverse Fisher transformation** of a given number. This function is
often used in statistics to revert a Fisher-transformed value (produced by the `FISHER` function) back to its original,
untransformed scale.

### Key Features of FISHERINV:

- Computes the **inverse Fisher transformation** for a given input value.
- Useful for converting Fisher-transformed values back into correlation coefficients or other original data scales.
- Frequently applied in statistical analysis, particularly when dealing with correlations and their normalized values.

### Syntax:

```plaintext
FISHERINV(y)
```

- **y**: The Fisher-transformed value to be converted back to the original scale.

### Formula:

The `FISHERINV` function implements the following mathematical transformation:

```plaintext
FISHERINV(y) = (e^(2y) - 1) / (e^(2y) + 1)
```

Where `e` represents the base of the natural logarithm.

### Examples:

1. **Revert the Fisher-transformed value:**

    ```excel
    =FISHERINV(0.54931)
    ```

   This calculates the inverse Fisher transformation of the value `0.54931` and returns the original correlation
   coefficient (~0.5).

2. **Analyze transformed data:**

   Suppose you have a Fisher-transformed value stored in cell `B1`:

    ```excel
    =FISHERINV(B1)
    ```

   This reverts the Fisher-transformed value in `B1` back to its original scale.

3. **Combine FISHER and FISHERINV:**

   To verify that the `FISHER` and `FISHERINV` functions are inverse operations:

    ```excel
    =FISHERINV(FISHER(0.5))
    ```

   This returns the original value `0.5`.

### Notes:

- The `FISHERINV` function is defined for all real numbers, as Fisher-transformed values can range from `-∞` to `∞`.
- This function is commonly paired with the `FISHER` function to move back and forth between transformed and original
  scales.

### Applications:

- **Statistical Analysis of Correlations:** Convert normalized Fisher-transformed values back into correlation
  coefficients.
- **Hypothesis Testing:** Interpret results of statistical tests relying on Fisher-transformed values by reverting them
  to their original context.
- **Reversing Fisher Transformations:** Use the inverse transformation to interpret normalized correlation values in
  their original scale.

> **Tip:** Use `FISHERINV` to easily interpret Fisher-transformed results in the context of the original data.