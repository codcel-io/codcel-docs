<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Compatibility Functions

This contains the list of compatibility functions that are currently supported by Codcel.

## C

### [CHIDIST](./compatibility-functions/chi_dist.md)
Calculates the one-tailed probability of the chi-squared distribution.

- **Purpose:** Useful for hypothesis testing and assessing goodness-of-fit.

- **Formula:** `CHIDIST(x, degrees_freedom)`
  - `x` is the value at which to evaluate the distribution.
  - `degrees_freedom` is the number of degrees of freedom in the distribution.

- **Example Usage:**
  - `=CHIDIST(5.991, 2)` calculates the one-tailed probability for a chi-squared value of 5.991 with 2 degrees of
    freedom.
  - `=CHIDIST(A1, B1)` computes the one-tailed probability using the values in cells `A1` and `B1`.

### [CHIINV](./compatibility-functions/chi_inv.md)
Calculates the inverse of the one-tailed probability of the chi-squared distribution.

- **Purpose:** Useful for deriving the chi-squared value based on a given probability and degrees of freedom.

- **Formula:** `CHIINV(probability, degrees_freedom)`
  - `probability` is the one-tailed probability for which the chi-squared value is to be found.
  - `degrees_freedom` is the number of degrees of freedom in the distribution.

- **Example Usage:**
  - `=CHIINV(0.05, 2)` calculates the chi-squared value for a one-tailed probability of 0.05 with 2 degrees of freedom.
  - `=CHIINV(A1, B1)` computes the chi-squared value using the probability in cell `A1` and degrees of freedom in cell
    `B1`.

### [CHITEST](./compatibility-functions/chi_test.md)
Calculates the test for independence using the chi-squared distribution.

- **Purpose:** Useful for determining the probability of observing a sample result under the null hypothesis, typically
  in contingency table analysis.

- **Formula:** `CHITEST(actual_range, expected_range)`
  - `actual_range` is the range of observed frequencies or values.
  - `expected_range` is the range of expected frequencies or values, calculated based on the null hypothesis.

- **Example Usage:**
  - `=CHITEST({4, 6, 8}, {5, 5, 8})` calculates the chi-squared test statistic for the given observed (`{4, 6, 8}`) and
    expected (`{5, 5, 8}`) ranges.
  - `=CHITEST(A1:A3, B1:B3)` computes the test statistic using observed values in `A1:A3` and expected values in `B1:B3`.

### [CONFIDENCE](./compatibility-functions/confidence.md)
Calculates the confidence interval for a population mean using a normal distribution.

- **Purpose:** Useful for statistical analysis to estimate the range within which a population parameter lies with a
  given level of confidence.

- **Formula:** `CONFIDENCE(alpha, standard_dev, size)`
  - `alpha` is the significance level (1 - confidence level, e.g., 0.05 for 95% confidence).
  - `standard_dev` is the population standard deviation.
  - `size` is the sample size.

- **Example Usage:**
  - `=CONFIDENCE(0.05, 1.5, 100)` calculates the confidence interval margin for a 95% confidence level, a population
    standard deviation of 1.5, and a sample size of 100.
  - `=CONFIDENCE(A1, B1, C1)` computes the confidence interval margin using the significance level in `A1`, standard
    deviation in `B1`, and sample size in `C1`.

### [COVAR](./compatibility-functions/covar.md)
Calculates the covariance of two sets of values.

- **Purpose:** Useful for determining the relationship between two data sets, such as whether an increase in one
  variable corresponds to an increase or decrease in the other.

- **Formula:** `COVAR(array1, array2)`
  - `array1` is the first range of data values.
  - `array2` is the second range of data values.
  - Both arrays must be of equal length, and their values are paired element-wise to calculate covariance.

- **Example Usage:**
  - `=COVAR({1, 2, 3}, {4, 5, 6})` calculates the covariance between the two provided data sets (`{1, 2, 3}` and
    `{4, 5, 6}`).
  - `=COVAR(A1:A3, B1:B3)` computes the covariance for paired data in cells `A1:A3` and `B1:B3`.

### [CRITBINOM](./compatibility-functions/crit_binom.md)
Calculates the smallest value for which the cumulative binomial distribution is greater than or equal to a given
criterion value.

- **Purpose:** Useful for determining the critical value in a binomial distribution, frequently used in quality control,
  hypothesis testing, or risk assessment.

- **Formula:** `CRITBINOM(trials, probability_s, alpha)`
  - `trials` is the number of Bernoulli trials (e.g., total number of experiments).
  - `probability_s` is the probability of success in each trial.
  - `alpha` is the criterion value for the cumulative distribution (between 0 and 1).

- **Example Usage:**
  - `=CRITBINOM(10, 0.5, 0.95)` calculates the smallest value such that the cumulative probability of a binomial
    distribution with 10 trials and success probability of 0.5 is at least 0.95.
  - `=CRITBINOM(A1, B1, C1)` computes the critical value using the inputs in `A1` (`trials`), `B1` (`probability_s`),
    and `C1` (`alpha`).

## E

### [EXPONDIST](./compatibility-functions/expon_dist.md)
Calculates the exponential distribution (density or cumulative).

- **Purpose:** Useful for modeling the time until an event occurs, such as the time between arrivals in a Poisson
  process or the time between system failures.

- **Formula:** `EXPONDIST(x, lambda, cumulative)`
  - `x` is the value at which to evaluate the distribution (must be non-negative).
  - `lambda` is the rate parameter of the distribution (must be positive).
  - `cumulative` is a logical value:
    - If `TRUE`, calculates the cumulative distribution function (CDF).
    - If `FALSE`, calculates the probability density function (PDF).

- **Example Usage:**
  - `=EXPONDIST(1, 0.5, TRUE)` calculates the cumulative probability for an exponential distribution at `x = 1` with a
    rate parameter (`lambda`) of `0.5`.
  - `=EXPONDIST(A1, B1, FALSE)` computes the probability density using the value in `A1` for `x` and the rate parameter
    in `B1`, assuming `cumulative` is false.

## F

### [FDIST](./compatibility-functions/f_dist.md)
Calculates the F probability distribution (density or cumulative).

- **Purpose:** Useful for comparing variances of two data sets, typically in analysis of variance (ANOVA) or regression
  analysis.

- **Formula:** `FDIST(x, degrees_freedom1, degrees_freedom2, cumulative)`
  - `x` is the value at which to evaluate the distribution (must be non-negative).
  - `degrees_freedom1` is the numerator degrees of freedom (must be positive).
  - `degrees_freedom2` is the denominator degrees of freedom (must be positive).
  - `cumulative` is a logical value:
    - If `TRUE`, calculates the cumulative distribution function (CDF).
    - If `FALSE`, calculates the probability density function (PDF).

- **Example Usage:**
  - `=FDIST(3.5, 2, 10, TRUE)` calculates the cumulative probability for an F distribution at `x = 3.5` with 2 numerator
    degrees and 10 denominator degrees of freedom.
  - `=FDIST(A1, B1, C1, FALSE)` computes the probability density using the value in `A1` for `x`, `B1` for numerator
    degrees, and `C1` for denominator degrees, assuming `cumulative` is false.

### [FINV](./compatibility-functions/f_inv.md)
Calculates the inverse of the F probability distribution (the value of x for a given probability).

- **Purpose:** Useful for finding the critical value of an F distribution for a specified probability and degrees of
  freedom, often applied in ANOVA tests.

- **Formula:** `FINV(probability, degrees_freedom1, degrees_freedom2)`
  - `probability` is the probability for which to calculate the inverse F value (must be between 0 and 1).
  - `degrees_freedom1` is the numerator degrees of freedom (must be positive).
  - `degrees_freedom2` is the denominator degrees of freedom (must be positive).

- **Example Usage:**
  - `=FINV(0.05, 2, 10)` calculates the F critical value for a probability of 0.05 with 2 numerator and 10 denominator
    degrees of freedom.
  - `=FINV(A1, B1, C1)` computes the F critical value using the probability in `A1`, numerator degrees in `B1`, and
    denominator degrees in `C1`.

### [FTEST](./compatibility-functions/f_test.md)
Calculates the result of an F-test, which returns the two-tailed probability that the variances in two arrays are not
significantly different.

- **Purpose:** Useful for comparing the variability of two data sets and determining if they come from populations with
  equal variances (homogeneity of variance).

- **Formula:** `FTEST(array1, array2)`
  - `array1` is the first range of data values.
  - `array2` is the second range of data values.
  - Both arrays must have numeric values and should not be empty.

- **Example Usage:**
  - `=FTEST({1, 2, 3}, {4, 5, 6})` calculates the F-test probability for the two provided data sets (`{1, 2, 3}` and
    `{4, 5, 6}`).
  - `=FTEST(A1:A3, B1:B3)` computes the F-test result for data in cells `A1:A3` and `B1:B3`.

## H

### [HYPGEOMDIST](./compatibility-functions/hypgeom_dist.md)
Calculates the hyper geometric distribution probability.

- **Purpose:** Useful for calculating probabilities without replacement, such as quality control sampling or card game
  probabilities.

- **Formula:** `HYPGEOMDIST(sample_s, number_sample, population_s, number_population)`
  - `sample_s` is the number of successes in the sample.
  - `number_sample` is the size of the sample.
  - `population_s` is the number of successes in the population.
  - `number_population` is the total population size.

- **Example Usage:**
  - `=HYPGEOMDIST(2, 10, 20, 100)` calculates the probability of exactly 2 successes in a sample of 10 drawn from a
    population of 100 with 20 successes.
  - `=HYPGEOMDIST(A1, B1, C1, D1)` computes the hypergeometric probability using the inputs: `A1` for `sample_s`, `B1`
    for `number_sample`, `C1` for `population_s`, and `D1` for `number_population`.

## N

### [NORMSINV](./compatibility-functions/norm_s_inv.md)
Calculates the inverse of the standard normal cumulative distribution (Z value) for a given probability.

- **Purpose:** Useful for finding the Z-score corresponding to a specific cumulative probability in a standard normal
  distribution (mean = 0, standard deviation = 1).

- **Formula:** `NORMSINV(probability)`
  - `probability` is the probability for which to calculate the inverse Z value (must be between 0 and 1, exclusive).

- **Example Usage:**
  - `=NORMSINV(0.95)` calculates the Z-score corresponding to a cumulative probability of 0.95 in the standard normal
    distribution.
  - `=NORMSINV(A1)` computes the Z-score using the probability value in cell `A1`.

## P

### [PERCENTRANK](./compatibility-functions/percent_rank.md)
Calculates the rank of a value in a data set as a percentage of the data set.

- **Purpose:** Useful for statistical analysis to determine the relative standing of a value within a data set,
  expressed as a percentage.

- **Formula:** `PERCENTRANK(array, x, [significance])`
  - `array` is the range of data values.
  - `x` is the value for which to calculate the rank as a percentage.
  - `[significance]` is an optional parameter that specifies the number of significant digits (defaults to 3 if
    omitted).

- **Example Usage:**
  - `=PERCENTRANK({10, 20, 30, 40, 50}, 30)` calculates the percentage rank of `30` within the data set
    `{10, 20, 30, 40, 50}`.
  - `=PERCENTRANK(A1:A10, B1, 5)` calculates the percentage rank of the value in `B1` within the range `A1:A10` and
    rounds the result to 5 significant digits.
  
## Q

### [QUARTILE](./compatibility-functions/quartile.md)
Calculates the quartile of a data set.

- **Purpose:** Useful for dividing a data set into four equal parts, each containing a quarter of the data points, and
  identifying the spread and center of the data.

- **Formula:** `QUARTILE(array, quart)`
  - `array` is the range of data values.
  - `quart` is the quartile to calculate:
    - `0` returns the minimum value.
    - `1` returns the first quartile (25th percentile).
    - `2` returns the median (50th percentile).
    - `3` returns the third quartile (75th percentile).
    - `4` returns the maximum value.

- **Example Usage:**
  - `=QUARTILE({1, 2, 3, 4, 5}, 2)` calculates the median (50th percentile) of the data set `{1, 2, 3, 4, 5}`.
  - `=QUARTILE(A1:A10, 1)` calculates the first quartile (25th percentile) for the data range `A1:A10`.

## R

### [RANK](./compatibility-functions/rank.md)
Calculates the rank of a number in a data set.

- **Purpose:** Useful for determining the position of a specific value in a data set relative to other values in
  ascending or descending order.

- **Formula:** `RANK(number, array, [order])`
  - `number` is the value for which to determine the rank.
  - `array` is the range of data values.
  - `[order]` is an optional parameter:
    - If `0` or omitted, ranks in descending order (largest value is rank 1).
    - If `1`, ranks in ascending order (smallest value is rank 1).

- **Example Usage:**
  - `=RANK(45, {50, 40, 45, 30}, 0)` calculates the rank of `45` in descending order within the data set.
  - `=RANK(A1, A1:A10, 1)` calculates the rank of the value in `A1` in ascending order relative to the range `A1:A10`.

## S

### [STDEVP](./compatibility-functions/st_dev_p.md)
Calculates the standard deviation of an entire population.

- **Purpose:** Useful for measuring the dispersion or spread of a dataset when the data represents the entire
  population.

- **Formula:** `STDEVP(array)`
  - `array` is the range of data values representing the entire population.
  - All values in `array` must be numeric.

- **Example Usage:**
  - `=STDEVP({2, 4, 6, 8})` calculates the standard deviation for the population `{2, 4, 6, 8}`.
  - `=STDEVP(A1:A10)` computes the standard deviation for the population data in the range `A1:A10`.

## V

### [VARP](./compatibility-functions/var_p.md)
Calculates the variance of an entire population.

- **Purpose:** Useful for measuring variability when the data represents the entire population.

- **Formula:** `VARP(array)`
  - `array` is the range of data values representing the entire population.
  - All values in `array` must be numeric.

- **Example Usage:**
  - `=VARP({2, 4, 6, 8})` calculates the variance for the population `{2, 4, 6, 8}`.
  - `=VARP(A1:A10)` computes the variance for the population data in the range `A1:A10`.