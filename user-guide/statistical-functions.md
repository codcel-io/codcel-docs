<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Statistical Functions

This contains the list of statistical functions that are currently supported by Codcel.

## A

### [AVEDEV](./statistical-functions/ave_dev.md)
Calculates the average of the absolute deviations of data points from their mean.

- **Purpose:** Useful for measuring the spread of data values around the mean without regard to direction.

- **Formula:** `AVEDEV(number1, [number2], ...)`
    - `number1, [number2], ...` are the numbers or ranges for which to calculate the average deviation.

- **Example Usage:**
    - `=AVEDEV(4, 6, 8, 10)` calculates the average absolute deviation of the numbers from their mean.
    - `=AVEDEV(A1:A5)` computes the average absolute deviation for the range of cells `A1` to `A5`.

### [AVERAGEA](./statistical-functions/average_a.md)
Calculates the average (arithmetic mean) of the values in a group, treating TRUE as 1, FALSE as 0, and text as 0.

- **Purpose:** Useful for averaging data that includes logical values or text in addition to numbers.

- **Formula:** `AVERAGEA(number1, [number2], ...)`
  - `number1, [number2], ...` are the numbers, logical values, ranges, or arrays to calculate the average.

- **Example Usage:**
  - `=AVERAGEA(4, TRUE, "text", 8)` calculates the average, treating `TRUE` as 1 and "text" as 0. The result is
    `(4 + 1 + 0 + 8) / 4 = 3.25`.
  - `=AVERAGEA(A1:A5)` computes the average for the range of cells `A1` to `A5`, considering logical or text values if
    present.

### [AVERAGEIF](./conditional-functions/average_if.md)
Calculates the average (arithmetic mean) of all the cells in a range that meet a given condition.

- **Purpose:** Useful for calculating averages based on criteria, such as numerical conditions or matching specific
  text.

- **Formula:** `AVERAGEIF(range, criteria, [average_range])`
  - `range`: The range of cells to evaluate against the criteria.
  - `criteria`: The condition or test that determines which cells to average. This can include logical operators (e.g.,
    `>5`, `="apples"`).
  - `[average_range]` (optional): The actual cells to average. If omitted, the values in `range` are averaged.

- **Example Usage:**
  - `=AVERAGEIF(A1:A10, ">5")` calculates the average of all numbers in the range `A1:A10` that are greater than 5.
  - `=AVERAGEIF(A1:A10, "apples", B1:B10)` computes the average of corresponding values in `B1:B10` where `A1:A10`
    equals "apples".

### [AVERAGEIFS](./statistical-functions/average_ifs.md)
Calculates the average (arithmetic mean) for cells specified by a set of multiple criteria.

- **Purpose:** Useful for calculating averages based on multiple conditions or criteria.

- **Formula:** `AVERAGEIFS(average_range, criteria_range1, criteria1, [criteria_range2, criteria2], ...)`
  - `average_range`: The range of cells to calculate the average for.
  - `criteria_range1`: The range of cells to evaluate against the first criteria.
  - `criteria1`: The first condition to be met for a cell to be included in the average.
  - `[criteria_range2, criteria2], ...` (optional): Additional ranges and criteria to evaluate.

- **Example Usage:**
  - `=AVERAGEIFS(B1:B10, A1:A10, ">5", C1:C10, "apples")` calculates the average of values in `B1:B10` where
    corresponding values in `A1:A10` are greater than 5 and corresponding values in `C1:C10` equal "apples".
  - `=AVERAGEIFS(A1:A20, B1:B20, "<100", C1:C20, ">=50")` computes the average of values in `A1:A20` where the
    corresponding values in `B1:B20` are less than 100 and values in `C1:C20` are greater than or equal to 50.

## B

### [BETAINV](./statistical-functions/beta_inv.md)
Calculates the inverse of the Cumulative Beta Probability Density Function (BETA.DIST). This is used to find the value
of the beta distribution, given a cumulative probability.

- **Purpose:** Useful for statistical analysis where the beta distribution is utilized, such as modeling in project
  planning or business processes.

- **Formula:** `BETAINV(probability, alpha, beta, [A], [B])`
  - `probability`: The cumulative probability associated with the beta distribution.
  - `alpha`: A parameter of the distribution that shapes its form (must be > 0).
  - `beta`: Another parameter of the distribution that shapes its form (must be > 0).
  - `[A]` (optional): The lower bound of the interval of x (default is 0 if omitted).
  - `[B]` (optional): The upper bound of the interval of x (default is 1 if omitted).

- **Example Usage:**
  - `=BETAINV(0.5, 2, 2, 0, 1)` calculates the inverse of the beta cumulative probability density function for the
    probability 0.5, with parameters alpha = 2, beta = 2, lower bound = 0, and upper bound = 1.
  - `=BETAINV(0.75, 3, 4)` computes the value of the beta distribution for the given parameters and default bounds (0 to
    1).

### [BETA.INV](./statistical-functions/beta__inv.md)
Calculates the inverse of the Cumulative Beta Probability Density Function (BETA.DIST). This is used to find the value
of the beta distribution, given a cumulative probability.

- **Purpose:** Useful for statistical analysis where the beta distribution is utilized, such as modeling in project
  planning or business processes.

- **Formula:** `BETA.INV(probability, alpha, beta, [A], [B])`
  - `probability`: The cumulative probability associated with the beta distribution.
  - `alpha`: A parameter of the distribution that shapes its form (must be > 0).
  - `beta`: Another parameter of the distribution that shapes its form (must be > 0).
  - `[A]` (optional): The lower bound of the interval of x (default is 0 if omitted).
  - `[B]` (optional): The upper bound of the interval of x (default is 1 if omitted).

- **Example Usage:**
  - `=BETA.INV(0.5, 2, 2, 0, 1)` calculates the inverse of the beta cumulative probability density function for the
    probability 0.5, with parameters alpha = 2, beta = 2, lower bound = 0, and upper bound = 1.
  - `=BETA.INV(0.75, 3, 4)` computes the value of the beta distribution for the given parameters and default bounds (0
    to 1).

### [BINOMDIST](./statistical-functions/binom_dist.md)
Calculates the individual term binomial distribution probability. It can be used in statistical analysis, particularly
in quality control, where you want to determine the probability of a specific number of successes in a series of trials.

- **Purpose:** Helps in analyzing data that follows a binomial distribution.

- **Formula:** `BINOMDIST(number_s, trials, probability_s, cumulative)`
  - `number_s`: The number of successes in the trials.
  - `trials`: The number of independent trials.
  - `probability_s`: The probability of success on each trial.
  - `cumulative`: A logical value that determines the form of the function. If `TRUE`, BINOMDIST returns the cumulative
    distribution probability. If `FALSE`, it returns the probability mass function.

- **Example Usage:**
  - `=BINOMDIST(6, 10, 0.5, FALSE)` calculates the probability of exactly 6 successes in 10 trials with a 0.5
    probability of success on each trial.
  - `=BINOMDIST(6, 10, 0.5, TRUE)` calculates the cumulative probability of obtaining at most 6 successes in 10 trials.

### [BINOM.DIST](./statistical-functions/binom__dist.md)
Calculates the binomial distribution probability. It can be used in statistical analysis, particularly in scenarios
involving a fixed number of independent trials with the same probability of success.

- **Purpose:** Used to determine probabilities in a binomial distribution, such as the likelihood of a certain number of
  successes in repeated trials.

- **Formula:** `BINOM.DIST(number_s, trials, probability_s, cumulative)`
  - `number_s`: The number of successes in the trials (must be an integer greater than or equal to 0 and less than or
    equal to `trials`).
  - `trials`: The number of independent trials (must be an integer greater than or equal to 0).
  - `probability_s`: The probability of success on each trial (must be between 0 and 1).
  - `cumulative`: A logical value that controls the type of distribution:
    - If `TRUE`, BINOM.DIST returns the cumulative distribution function (i.e., the probability of at most `number_s`
      successes).
    - If `FALSE`, it returns the probability mass function (i.e., the probability of exactly `number_s` successes).

- **Example Usage:**
  - `=BINOM.DIST(6, 10, 0.5, FALSE)` calculates the probability of exactly 6 successes in 10 trials with a 0.5 success
    probability.
  - `=BINOM.DIST(6, 10, 0.5, TRUE)` computes the cumulative probability of at most 6 successes in 10 trials.

### [BINOM.DIST.RANGE](./statistical-functions/binom__dist__range.md)
Calculates the probability of a random variable being within a given range in a binomial distribution. Useful for
statistical analysis when assessing probabilities over a range of outcomes.

- **Purpose:** Determines the probability of a specified range of successes in a fixed number of independent trials.

- **Formula:** `BINOM.DIST.RANGE(trials, probability_s, number_s, [number_s2])`
  - `trials`: The number of independent trials.
  - `probability_s`: The probability of success on each trial (must be between 0 and 1).
  - `number_s`: The lower bound of the successes for which you want to calculate the probability.
  - `[number_s2]` (optional): The upper bound of the successes for which you want to calculate the probability. If
    omitted, calculates the probability for `number_s` only.

- **Example Usage:**
  - `=BINOM.DIST.RANGE(10, 0.5, 6)` calculates the probability of exactly 6 successes in 10 trials, each with a 0.5
    probability of success.
  - `=BINOM.DIST.RANGE(10, 0.5, 6, 8)` calculates the probability of obtaining between 6 and 8 successes (inclusive) in
    10 trials with a 0.5 success probability.
  - `=BINOM.DIST.RANGE(20, 0.3, 5, 10)` computes the probability of between 5 and 10 successes (inclusive) in 20 trials
    with a success probability of 0.3.

### [BINOMINV](./statistical-functions/binom_inv.md)
Calculates the smallest value for which the cumulative binomial distribution is equal to or greater than a specified
criterion. This is useful for determining thresholds in binomial distributions.

- **Purpose:** Useful when you need to find a cutoff point for successes in a series of trials where the cumulative
  probability meets a specific criterion.

- **Formula:** `BINOMINV(trials, probability_s, alpha)`
  - `trials`: The number of independent trials.
  - `probability_s`: The probability of success on each trial.
  - `alpha`: The criterion, a probability threshold in the range of [0, 1].

- **Example Usage:**
  - `=BINOM.INV(10, 0.5, 0.8)` calculates the smallest number of successes for which the cumulative binomial probability
    with 10 trials and a success probability of 0.5 is at least 0.8.
  - `=BINOM.INV(20, 0.3, 0.9)` determines the cutoff for 20 trials and a success probability of 0.3 where the cumulative
    probability reaches 0.9.


## C

### [CHISQ.DIST](./statistical-functions/chisq_dist.md)
Calculates the chi-squared distribution for a given value, degrees of freedom, and cumulative flag.

- **Purpose:** Useful for hypothesis testing or assessing the goodness-of-fit for observed data.

- **Formula:** `CHISQ.DIST(x, degrees_freedom, cumulative)`
  - `x`: The value at which you want to evaluate the distribution.
  - `degrees_freedom`: The degrees of freedom, which must be a positive integer.
  - `cumulative`: A logical value. If `TRUE`, calculates the cumulative distribution; if `FALSE`, calculates the
    probability density function.

- **Example Usage:**
  - `=CHISQ.DIST(2.5, 3, TRUE)` calculates the cumulative distribution function of the chi-squared distribution for
    `x = 2.5` with 3 degrees of freedom.
  - `=CHISQ.DIST(2.5, 3, FALSE)` computes the probability density function for the same inputs.

### [CHISQ.DIST.RT](./statistical-functions/chisq_dist_rt.md)
Calculates the right-tailed probability of the chi-squared distribution for a given value and degrees of freedom. This
is typically used in hypothesis testing.

- **Purpose:** Useful for testing goodness-of-fit, independence in contingency tables, or the right tail of the
  chi-squared distribution in general.

- **Formula:** `CHISQ.DIST.RT(x, degrees_freedom)`
  - `x`: The value at which you want to evaluate the right-tailed distribution (must be greater than or equal to 0).
  - `degrees_freedom`: The degrees of freedom, which must be a positive integer.

- **Example Usage:**
  - `=CHISQ.DIST.RT(5.3, 4)` calculates the right-tailed probability of the chi-squared distribution for `x = 5.3` with
    4 degrees of freedom.
  - `=CHISQ.DIST.RT(10, 8)` computes the same for `x = 10` with 8 degrees of freedom.

### [CHISQ.INV](./statistical-functions/chisq_inv.md)
Calculates the inverse of the left-tailed probability of the chi-squared distribution.

- **Purpose:** Useful for hypothesis testing and statistical analysis where the chi-squared distribution is utilized.

- **Formula:** `CHISQ.INV(probability, degrees_freedom)`
  - `probability`: The probability associated with the chi-squared distribution (must be between 0 and 1).
  - `degrees_freedom`: The degrees of freedom, which must be a positive integer.

- **Example Usage:**
  - `=CHISQ.INV(0.95, 2)` calculates the value of the chi-squared distribution for which the cumulative probability is
    0.95, with 2 degrees of freedom.
  - `=CHISQ.INV(0.05, 5)` computes the chi-squared value corresponding to a cumulative probability of 0.05 with 5
    degrees of freedom.

### [CHISQ.INV.RT](./statistical-functions/chisq_inv_rt.md)
Calculates the inverse of the right-tailed probability of the chi-squared distribution.

- **Purpose:** Useful for hypothesis testing and statistical analysis involving the chi-squared distribution.

- **Formula:** `CHISQ.INV.RT(probability, degrees_freedom)`
  - `probability`: The right-tailed probability associated with the chi-squared distribution (must be between 0 and 1).
  - `degrees_freedom`: The degrees of freedom, which must be a positive integer.

- **Example Usage:**
  - `=CHISQ.INV.RT(0.05, 2)` calculates the value of the chi-squared distribution for which the right-tailed probability
    is `0.05`, with 2 degrees of freedom.
  - `=CHISQ.INV.RT(0.10, 4)` computes the chi-squared value corresponding to a right-tailed probability of `0.10` with 4
    degrees of freedom.

### [CHISQ.TEST](./statistical-functions/chisq_test.md)
Calculates the chi-squared test for independence. This function determines whether two categorical datasets are likely
to be related or independent.

- **Purpose:** Useful for hypothesis testing, particularly for determining relationships between categorical variables.

- **Formula:** `CHISQ.TEST(actual_range, expected_range)`
  - `actual_range`: The range of observed frequency data.
  - `expected_range`: The range of expected frequency data under an independent hypothesis. Must have the same
    dimensions as `actual_range`.

- **Example Usage:**
  - `=CHISQ.TEST(A1:B2, C1:D2)` returns the chi-squared statistic for the observed data in `A1:B2` and the expected data
    in `C1:D2`.
  - `=CHISQ.TEST(A1:A4, B1:B4)` tests for independence based on the observed values in `A1:A4` and the expected values
    in `B1:B4`.

### [CONFIDENCE.NORM](./statistical-functions/confidence_norm.md)
Calculates the confidence interval for a population mean using a normal distribution.

- **Purpose:** Useful for determining the margin of error when estimating a population mean with a known standard
  deviation.

- **Formula:** `CONFIDENCE.NORM(alpha, standard_dev, size)`
  - `alpha`: The significance level used to compute the confidence level (e.g., alpha = 0.05 for a 95% confidence
    level).
  - `standard_dev`: The population standard deviation.
  - `size`: The sample size.

- **Example Usage:**
  - `=CONFIDENCE.NORM(0.05, 1.5, 100)` calculates the margin of error for a 95% confidence level, with a standard
    deviation of 1.5 and a sample size of 100.
  - `=CONFIDENCE.NORM(0.01, 2, 50)` calculates the margin of error for a 99% confidence level with a standard deviation
    of 2 and a sample size of 50.


### [CORREL](./statistical-functions/correl.md)
Calculates the Pearson correlation coefficient between two sets of data.

- **Purpose:** Useful for determining the strength and direction of a linear relationship between two variables.

- **Formula:** `CORREL(array1, array2)`
  - `array1`: The first range of values or array.
  - `array2`: The second range of values or array.

- **Example Usage:**
  - `=CORREL(A1:A10, B1:B10)` calculates the correlation coefficient between the values in the ranges `A1:A10` and
    `B1:B10`.
  - `=CORREL({1, 2, 3}, {4, 5, 6})` computes the correlation coefficient for the two arrays `{1, 2, 3}` and `{4, 5, 6}`.

### [COUNT](./statistical-functions/count.md)
Counts the number of numeric values in a given range or array.

- **Purpose:** Useful for determining how many cells or elements in a specified range contain numeric values.

- **Formula:** `COUNT(array)`
  - `array`: The range or array of values to evaluate.

- **Example Usage:**
  - `=COUNT(A1:A10)` counts the numeric values in the range `A1:A10`.
  - `=COUNT({1, "text", 3, FALSE, 5})` returns `3` because there are 3 numeric values in the array: `1, 3, 5`.

### [COUNTA](./statistical-functions/counta.md)
Counts the number of non-empty cells in a range or list of arguments, including cells containing text, numbers, logical values, and errors.

- **Purpose:** Useful for determining how many cells contain any type of data, not just numeric values.

- **Formula:** `COUNTA(value1, [value2], ...)`
  - `value1`: The first range, cell, or value to count.
  - `[value2], ...` (optional): Additional values, ranges, or cells to include in the count.

- **Example Usage:**
  - `=COUNTA(A1:A10)` counts all non-empty cells in the range `A1:A10`.
  - `=COUNTA({1, "text", TRUE, "", 5})` returns `5` because all values including the empty string are counted.

### [COUNTBLANK](./statistical-functions/count_blank.md)
Counts the number of empty (blank) cells in a specified range.

- **Purpose:** Useful for identifying missing data or gaps in a dataset.

- **Formula:** `COUNTBLANK(range)`
  - `range`: The range of cells in which you want to count blank cells.

- **Example Usage:**
  - `=COUNTBLANK(A1:A10)` counts the number of empty cells in the range `A1:A10`.
  - `=COUNTBLANK(A1:C10)` counts the number of empty cells across a multi-column range from `A1` to `C10`.

### [COUNTIFS](./statistical-functions/count_ifs.md)
Counts the number of cells that meet multiple criteria in a given range or ranges.

- **Purpose:** Useful for conditional analysis where multiple criteria must be satisfied.

- **Formula:** `COUNTIFS(criteria_range1, criteria1, [criteria_range2, criteria2], ...)`
  - `criteria_range1, criteria_range2, ...`: Ranges of values to evaluate against the corresponding criteria.
  - `criteria1, criteria2, ...`: Conditions to apply to the respective ranges.

- **Example Usage:**
  - `=COUNTIFS(A1:A10, ">5", B1:B10, "<10")` counts the number of rows in which the values in `A1:A10` are greater than
    5 and the values in `B1:B10` are less than 10.
  - `=COUNTIFS(A1:A10, "=123", C1:C10, "text")` counts rows where `A1:A10` equals 123 and `C1:C10` contains the word "
    text".

### [COVARIANCE.P](./statistical-functions/covariance_p.md)
Calculates the population covariance between two data sets, which measures the degree to which the two data sets vary
together.

- **Purpose:** Useful for statistical analysis to understand relationships between two variables in a population.

- **Formula:** `COVARIANCE.P(array1, array2)`
  - `array1`: The first range of values or array.
  - `array2`: The second range of values or array (must have the same number of elements as `array1`).

- **Example Usage:**
  - `=COVARIANCE.P(A1:A10, B1:B10)` calculates the population covariance between the values in the ranges `A1:A10` and
    `B1:B10`.
  - `=COVARIANCE.P({1, 2, 3, 4}, {5, 6, 7, 8})` computes the population covariance for the two arrays `{1, 2, 3, 4}` and
    `{5, 6, 7, 8}`.

### [COVARIANCE.S](./statistical-functions/covariance_s.md)
Calculates the sample covariance between two data sets, which measures how two variables vary together in a sample.

- **Purpose:** Useful for statistical analysis to understand relationships between two variables in a sample dataset.

- **Formula:** `COVARIANCE.S(array1, array2)`
  - `array1`: The first range of values or array.
  - `array2`: The second range of values or array (must have the same number of elements as `array1`).

- **Example Usage:**
  - `=COVARIANCE.S(A1:A10, B1:B10)` calculates the sample covariance between the values in the ranges `A1:A10` and
    `B1:B10`.
  - `=COVARIANCE.S({1, 2, 3, 4}, {5, 6, 7, 8})` computes the sample covariance for the two arrays `{1, 2, 3, 4}` and
    `{5, 6, 7, 8}`.

## D

### [DEVSQ](./statistical-functions/devsq.md)
Calculates the sum of squared deviations of data points from their mean.

- **Purpose:** Useful for statistical analysis to measure variability in a dataset.

- **Formula:** `DEVSQ(array)`
  - `array`: The range or array of values to evaluate.

- **Example Usage:**
  - `=DEVSQ(A1:A10)` computes the sum of squared deviations of the values in the range `A1:A10` from their mean.
  - `=DEVSQ({2, 4, 6, 8})` calculates the sum of squared deviations for the array `{2, 4, 6, 8}`.

## E

### [EXPON.DIST](./statistical-functions/expon_dist.md)
Calculates values for the exponential distribution, often used to model the time between events in a Poisson process.

- **Purpose:** Useful for reliability analysis, queue modeling, and time-to-failure analysis in statistics.

- **Formula:** `EXPON.DIST(x, lambda, cumulative)`
  - `x`: The value at which to evaluate the distribution. Must be ≥ 0.
  - `lambda`: The rate parameter of the distribution. Must be > 0.
  - `cumulative`: A boolean indicating whether to calculate the cumulative distribution function (`TRUE`) or the
    probability density function (`FALSE`).

- **Example Usage:**
  - `=EXPON.DIST(1, 0.5, TRUE)` calculates the cumulative distribution function for an exponential distribution where
    `x = 1` and `lambda = 0.5`.
  - `=EXPON.DIST(2, 0.3, FALSE)` computes the probability density function for an exponential distribution where `x = 2`
    and `lambda = 0.3`.

## F

### [F.DIST](./statistical-functions/f_dist.md)
Calculates the F probability distribution, which is used to compare two variances and is commonly applicable in
hypothesis testing like the analysis of variance (ANOVA).

- **Purpose:** Useful for determining if two data sets have significantly different variances.

- **Formula:** `F.DIST(x, degrees_freedom1, degrees_freedom2, cumulative)`
  - `x`: The value at which to evaluate the distribution. Must be ≥ 0.
  - `degrees_freedom1`: The numerator degrees of freedom. Must be ≥ 1.
  - `degrees_freedom2`: The denominator degrees of freedom. Must be ≥ 1.
  - `cumulative`: A boolean indicating whether to calculate the cumulative distribution function (`TRUE`) or the
    probability density function (`FALSE`).

- **Example Usage:**
  - `=F.DIST(2.5, 5, 10, TRUE)` calculates the cumulative F-distribution with `x = 2.5`, `5` numerator degrees of
    freedom, and `10` denominator degrees of freedom.
  - `=F.DIST(1.8, 4, 6, FALSE)` computes the probability density function for an F-distribution where `x = 1.8`, `4`
    numerator degrees of freedom, and `6` denominator degrees of freedom`.

### [F.DIST.RT](./statistical-functions/f_dist_rt.md)
Calculates the right-tailed F probability distribution, which is used to determine the probability that the variances of
two populations are significantly different.

- **Purpose:** Useful for statistical hypothesis testing, such as comparing the variances of two datasets.

- **Formula:** `F.DIST.RT(x, degrees_freedom1, degrees_freedom2)`
  - `x`: The value at which to evaluate the distribution. Must be ≥ 0.
  - `degrees_freedom1`: The numerator degrees of freedom. Must be ≥ 1.
  - `degrees_freedom2`: The denominator degrees of freedom. Must be ≥ 1.

- **Example Usage:**
  - `=F.DIST.RT(2.5, 5, 10)` calculates the right-tailed F-distribution with `x = 2.5`, `5` numerator degrees of
    freedom, and `10` denominator degrees of freedom.
  - `=F.DIST.RT(1.8, 4, 6)` computes the right-tail probability for an F-distribution where `x = 1.8`, `4` numerator
    degrees of freedom, and `6` denominator degrees of freedom`.

### [F.INV](./statistical-functions/f_inv.md)
Calculates the inverse of the left-tailed F probability distribution. Given a probability (`p`), degrees of freedom for
the numerator (`degrees_freedom1`) and denominator (`degrees_freedom2`), this function returns the corresponding F
value.

- **Purpose:** Useful for statistical hypothesis testing and analysis of variance (ANOVA).

- **Formula:** `F.INV(p, degrees_freedom1, degrees_freedom2)`
  - `p`: The probability for which to compute the inverse F-distribution. Must be in the range `0 < p < 1`.
  - `degrees_freedom1`: The numerator degrees of freedom. Must be ≥ 1.
  - `degrees_freedom2`: The denominator degrees of freedom. Must be ≥ 1.

- **Example Usage:**
  - `=F.INV(0.05, 5, 10)` calculates the left-tailed inverse F-distribution with `p = 0.05`, `5` numerator degrees of
    freedom, and `10` denominator degrees of freedom.
  - `=F.INV(0.1, 4, 6)` computes the F value for a probability of `0.1`, with `4` numerator degrees of freedom and `6`
    denominator degrees of freedom.

### [F.INV.RT](./statistical-functions/f_inv_rt.md)
Calculates the inverse of the right-tailed F probability distribution. Given a probability (`p`), degrees of freedom for
the numerator (`degrees_freedom1`) and denominator (`degrees_freedom2`), this function returns the corresponding F
value.

- **Purpose:** Useful for statistical hypothesis testing and analysis of variance (ANOVA).

- **Formula:** `F.INV.RT(p, degrees_freedom1, degrees_freedom2)`
  - `p`: The probability for which to compute the inverse F-distribution. Must be in the range `0 < p < 1`.
  - `degrees_freedom1`: The numerator degrees of freedom. Must be ≥ 1.
  - `degrees_freedom2`: The denominator degrees of freedom. Must be ≥ 1.

- **Example Usage:**
  - `=F.INV.RT(0.05, 5, 10)` calculates the right-tailed inverse F-distribution with `p = 0.05`, `5` numerator degrees
    of freedom, and `10` denominator degrees of freedom.
  - `=F.INV.RT(0.1, 4, 6)` computes the F value for a probability of `0.1`, with `4` numerator degrees of freedom and
    `6` denominator degrees of freedom.

### [F.TEST](./statistical-functions/f_test.md)
Performs an F-test to determine if the variances of two data sets are significantly different. Returns the result of an
F-test as the two-tailed probability that the variances in `array1` and `array2` are not significantly different.

- **Purpose:** Useful for comparing variances in statistical analysis and hypothesis testing.

- **Formula:** `F.TEST(array1, array2)`
  - `array1`: The first range or array of values.
  - `array2`: The second range or array of values.

- **Example Usage:**
  - `=F.TEST(A1:A10, B1:B10)` calculates the two-tailed F-test probability for the variances of the values in the ranges
    `A1:A10` and `B1:B10`.
  - `=F.TEST({3, 6, 9, 12}, {4, 8, 10, 14})` computes the F-test probability for the variances of the two arrays.

### [FISHER](./statistical-functions/fisher.md)
Calculates the Fisher transformation of a correlation coefficient, turning it into a value that can be used for
hypothesis testing or interval estimation. This function is often used in statistics for a more normal-like distribution
of correlation coefficients.

- **Purpose:** Useful for statistical analysis involving correlation coefficients, especially for hypothesis testing and
  confidence intervals.

- **Formula:** `FISHER(x)`
  - `x`: The correlation coefficient to transform, where `-1 < x < 1`.

- **Example Usage:**
  - `=FISHER(0.5)` calculates the Fisher transformation for `x = 0.5`.
  - `=FISHER(-0.3)` computes the Fisher transformation for `x = -0.3`.

### [FISHERINV](./statistical-functions/fisher_inv.md)
Calculates the inverse of the Fisher transformation, which transforms a value from the Fisher Z-transformation back to a
correlation coefficient. This function is useful in statistics for interpreting results of hypothesis testing or
interval estimation.

- **Purpose:** Useful for reversing the Fisher transformation and obtaining the original correlation coefficient.

- **Formula:** `FISHERINV(y)`
  - `y`: The Fisher-transformed value to invert.

- **Example Usage:**
  - `=FISHERINV(0.5)` calculates the inverse Fisher transformation for `y = 0.5`.
  - `=FISHERINV(-0.3)` computes the inverse Fisher transformation for `y = -0.3`.

### [FORECAST](./statistical-functions/forecast.md)
Calculates the future value along a linear trend using existing values. This function uses the least squares method to
predict a data point by fitting a straight line to known data points.

- **Purpose:** Useful for predicting future values based on historical data.

- **Formula:** `FORECAST(x, known_y's, known_x's)`
  - `x`: The data point for which to forecast a value.
  - `known_y's`: The array or range of known dependent values.
  - `known_x's`: The array or range of known independent values.

- **Example Usage:**
  - `=FORECAST(30, {100, 150, 200}, {10, 20, 25})` calculates the forecasted value for `x = 30` based on the given known
    values.
  - `=FORECAST(15, A1:A10, B1:B10)` computes the forecasted value for `x = 15` using the data ranges `A1:A10` for
    `known_y's` and `B1:B10` for `known_x's`.

### [FORECAST.ETS](./statistical-functions/forecast__ets.md)
Calculates or predicts a future value using an exponential smoothing algorithm. This function is useful for time-series
forecasting.

- **Purpose:** Useful for predicting future values based on exponential smoothing in time-series data, particularly with
  seasonal patterns.

- **Formula:** `FORECAST.ETS(target_date, values, timeline, [seasonality], [data_completion], [aggregation])`
  - `target_date`: The data point for which to forecast.
  - `values`: The array or range of historical actual values (dependent values).
  - `timeline`: The array or range of historical time-related data points (independent values).
  - `[seasonality]` (optional): How the algorithm detects seasonality:
    - `0`: No seasonality.
    - `1`: Detect automatically.
    - Positive integer: User-defined length of the seasonal pattern.
  - `[data_completion]` (optional): Indicates how to handle missing data:
    - `0`: Missing data treated as zero.
    - `1` (default): Missing data handled through interpolation.
  - `[aggregation]` (optional): Specifies the function to aggregate data with the same time stamp (default is
    `AVERAGE`).

- **Example Usage:**
  - `=FORECAST.ETS(30, {100, 150, 200}, {1, 2, 3})` calculates the forecasted value at `target_date = 30` based on the
    provided past values and timeline.
  - `=FORECAST.ETS(DATE(2024, 1, 1), A1:A10, B1:B10, 12, 1, "SUM")` computes a forecast for a specific `target_date`
    using a 12-month seasonality factor, handling missing data via interpolation, and aggregating data using the `SUM`
    function.

### [FORECAST.ETS.CONFINT](./statistical-functions/forecast__ets__confint.md)
Returns a confidence interval for a forecast value at a specified target date, using the Exponential Smoothing (ETS)
algorithm. This function quantifies the uncertainty of a `FORECAST.ETS` prediction.

- **Purpose:** Useful for determining the margin of error around a time-series forecast, helping assess the reliability
  of predicted values.

- **Formula:** `FORECAST.ETS.CONFINT(target_date, values, timeline, [confidence_level], [seasonality], [data_completion], [aggregation])`
  - `target_date`: The data point for which to calculate the confidence interval of the forecast.
  - `values`: The array or range of historical actual values (dependent values).
  - `timeline`: The array or range of historical time-related data points (independent values).
  - `[confidence_level]` (optional): A value between 0 and 1 specifying the confidence level (default is `0.95`).
  - `[seasonality]` (optional): How the algorithm detects seasonality:
    - `0`: No seasonality.
    - `1`: Detect automatically.
    - Positive integer: User-defined length of the seasonal pattern.
  - `[data_completion]` (optional): Indicates how to handle missing data:
    - `0`: Missing data treated as zero.
    - `1` (default): Missing data handled through interpolation.
  - `[aggregation]` (optional): Specifies the function to aggregate data with the same time stamp (default is
    `AVERAGE`).

- **Example Usage:**
  - `=FORECAST.ETS.CONFINT(A14, B2:B13, A2:A13)` returns the 95% confidence interval margin for the forecast at the
    date in `A14`.
  - `=FORECAST.ETS.CONFINT(A14, B2:B13, A2:A13, 0.99, 12)` computes a 99% confidence interval with a 12-month
    seasonality factor.

### [FORECAST.ETS.SEASONALITY](./statistical-functions/forecast__ets__seasonality.md)
Returns the length of the seasonal pattern that the Exponential Smoothing (ETS) algorithm detects in the specified time
series data. This function helps you understand the repeating cycle length before forecasting.

- **Purpose:** Useful for identifying and validating seasonal patterns in time-series data before running forecasts.

- **Formula:** `FORECAST.ETS.SEASONALITY(values, timeline, [data_completion], [aggregation])`
  - `values`: The array or range of historical actual values (dependent values).
  - `timeline`: The array or range of historical time-related data points (independent values).
  - `[data_completion]` (optional): Indicates how to handle missing data:
    - `0`: Missing data treated as zero.
    - `1` (default): Missing data handled through interpolation.
  - `[aggregation]` (optional): Specifies the function to aggregate data with the same time stamp (default is
    `AVERAGE`).

- **Example Usage:**
  - `=FORECAST.ETS.SEASONALITY(B2:B25, A2:A25)` returns the detected seasonal period length (e.g., `12` for yearly
    seasonality in monthly data).
  - `=FORECAST.ETS.SEASONALITY(B2:B13, A2:A13, 0, "SUM")` detects the seasonal period with missing data treated as
    zero and duplicate timestamps aggregated by sum.

### [FORECAST.ETS.STAT](./statistical-functions/forecast__ets__stat.md)
Returns a statistical value related to the Exponential Smoothing (ETS) forecast model for a given time series. This
function provides access to internal model parameters and goodness-of-fit metrics used by `FORECAST.ETS`.

- **Purpose:** Useful for evaluating forecast quality, inspecting smoothing parameters, and understanding model behaviour.

- **Formula:** `FORECAST.ETS.STAT(values, timeline, stat_type, [seasonality], [data_completion], [aggregation])`
  - `values`: The array or range of historical actual values (dependent values).
  - `timeline`: The array or range of historical time-related data points (independent values).
  - `stat_type`: An integer (1–8) specifying which statistic to return:
    - `1`: Alpha (level smoothing parameter)
    - `2`: Beta (trend smoothing parameter)
    - `3`: Gamma (seasonal smoothing parameter)
    - `4`: MASE (Mean Absolute Scaled Error)
    - `5`: SMAPE (Symmetric Mean Absolute Percentage Error)
    - `6`: MAE (Mean Absolute Error)
    - `7`: RMSE (Root Mean Squared Error)
    - `8`: Step size (detected time interval)
  - `[seasonality]` (optional): Sets the seasonal period length (`0` = none, `1` = auto-detect (default), or a positive
    integer for a specific period).
  - `[data_completion]` (optional): Indicates how to handle missing data:
    - `0`: Missing data treated as zero.
    - `1` (default): Missing data handled through interpolation.
  - `[aggregation]` (optional): Specifies the function to aggregate data with the same time stamp (default is
    `AVERAGE`).

- **Example Usage:**
  - `=FORECAST.ETS.STAT(B2:B25, A2:A25, 1)` returns the alpha (level) smoothing parameter for the fitted ETS model.
  - `=FORECAST.ETS.STAT(B2:B25, A2:A25, 4, 12)` returns the MASE error metric with a 12-month seasonal cycle.

### [FORECAST.LINEAR](./statistical-functions/forecast_linear.md)
Calculates a future value along a linear trend based on existing values. This function uses the least squares method to
determine a straight line that best fits the input data.

- **Purpose:** Useful for predicting future values along a linear trend in a dataset.

- **Formula:** `FORECAST.LINEAR(x, known_y's, known_x's)`
  - `x`: The value for which to predict.
  - `known_y's`: The array of known dependent values.
  - `known_x's`: The array of known independent values.

- **Example Usage:**
  - `=FORECAST.LINEAR(30, {100, 150, 200}, {10, 20, 25})` calculates the forecasted value for `x = 30` based on the
    provided data.
  - `=FORECAST.LINEAR(15, A1:A10, B1:B10)` applies a linear trend forecasting for an `x` value of `15` using the
    provided ranges `A1:A10` and `B1:B10`.

### [FREQUENCY](./statistical-functions/frequency.md)
Calculates the frequency distribution of a dataset. This function returns an array where each element indicates the
count of values within a specific range (or bin).

- **Purpose:** Useful for statistical analysis to determine data distribution across intervals.

- **Formula:** `FREQUENCY(data_array, bins_array)`
  - `data_array`: The array or range of data values to analyze.
  - `bins_array`: The array or range that specifies the interval boundaries.

- **Example Usage:**
  - `=FREQUENCY({1, 2, 3, 4, 5}, {2, 5})` calculates the frequency of values in the ranges `<= 2` and `3-5`.
  - `=FREQUENCY(A1:A10, B1:B5)` computes the frequency distribution using the dataset in `A1:A10` and the bin ranges
    specified in `B1:B5`.

## G

### [GAMMA](./statistical-functions/gamma.md)
Calculates the Gamma function value for a given input `x`. The Gamma function extends the factorial function to real and
complex numbers, providing a continuous extension of factorials.

- **Purpose:** Useful in statistics, probability, and mathematics for functions involving factorials and integrals.

- **Formula:** `GAMMA(x)`
  - `x`: The input value for which to compute the Gamma function. Must be a positive number (except for non-positive
    integers).

- **Example Usage:**
  - `=GAMMA(5)` calculates the Gamma function for `x = 5`, which is equivalent to `(5-1)! = 4! = 24`.
  - `=GAMMA(2.5)` computes the Gamma function for `x = 2.5`.

### [GAMMADIST](./statistical-functions/gamma_dist.md)
Calculates the Gamma distribution, which is commonly used in statistics to model continuous variables. This function can
compute either the probability density function (PDF) or the cumulative distribution function (CDF), based on the input
parameters.

- **Purpose:** Useful for statistical analysis and probability modeling for continuous distributions.

- **Formula:** `GAMMADIST(x, alpha, beta, cumulative)`
  - `x`: The value at which to evaluate the distribution. Must be a positive number.
  - `alpha`: The shape parameter, often referred to as "k" in the Gamma distribution. Must be a positive number.
  - `beta`: The scale parameter, often referred to as "θ" (theta) in the Gamma distribution. Must be a positive number.
  - `cumulative`: A boolean indicating which type of distribution to compute:
    - `TRUE`: Cumulative distribution function (CDF).
    - `FALSE`: Probability density function (PDF).

- **Example Usage:**
  - `=GAMMADIST(3, 2, 1, TRUE)` calculates the cumulative distribution function for the Gamma distribution with `x = 3`,
    `alpha = 2`, and `beta = 1`.
  - `=GAMMADIST(3, 2, 1, FALSE)` calculates the probability density function for the same parameters.

### [GAMMA.DIST](./statistical-functions/gamma__dist.md)
Calculates the Gamma distribution, widely used in probability and statistics for modeling continuous random variables.
This function supports both the probability density function (PDF) and the cumulative distribution function (CDF) based
on the input parameters.

- **Purpose:** Useful in statistical modeling and simulations for continuous distributions.

- **Formula:** `GAMMA.DIST(x, alpha, beta, cumulative)`
  - `x`: The value at which to evaluate the distribution. Must be a non-negative number.
  - `alpha`: The shape parameter (commonly represented as `k`) of the Gamma distribution. Must be a positive number.
  - `beta`: The inverse scale parameter (commonly represented as `1/θ`, where `θ` is the scale parameter). Must be a
    positive number.
  - `cumulative`: A boolean indicating whether to compute the cumulative distribution (CDF):
    - `TRUE`: Returns the cumulative probability up to `x`.
    - `FALSE`: Returns the probability density (PDF) at `x`.

- **Example Usage:**
  - `=GAMMA.DIST(3, 2, 1, TRUE)` computes the cumulative distribution function at `x = 3`, with `alpha = 2` and
    `beta = 1`.
  - `=GAMMA.DIST(3, 2, 1, FALSE)` computes the probability density function at `x = 3` with the same parameters.

### [GAMMAINV](./statistical-functions/gamma_inv.md)
Calculates the inverse of the Gamma cumulative distribution function (CDF) for a given probability and specified scale
and shape parameters. This function is used to determine the value `x` such that the cumulative probability up to `x`
matches the given probability.

- **Purpose:** Useful for finding values corresponding to a given cumulative probability in the Gamma distribution.

- **Formula:** `GAMMAINV(probability, alpha, beta)`
  - `probability`: The cumulative probability for which to find the inverse. Must be between 0 and 1.
  - `alpha`: The shape parameter ("k") of the Gamma distribution. Must be a positive number.
  - `beta`: The scale parameter ("θ") of the Gamma distribution. Must be a positive number.

- **Example Usage:**
  - `=GAMMAINV(0.5, 2, 1)` calculates the inverse Gamma CDF for a probability of `0.5`, with `alpha = 2` and `beta = 1`.
  - `=GAMMAINV(0.9, 3, 0.5)` computes the value `x` where the cumulative probability is `0.9`, with shape `alpha = 3`
    and scale `beta = 0.5`.

### [GAMMA.INV](./statistical-functions/gamma__inv.md)
Calculates the inverse of the Gamma cumulative distribution function (CDF) for a given probability and specified shape
and scale parameters. This function is used to find the value `x` such that the cumulative probability up to `x` equals
the given probability.

- **Purpose:** Useful for determining the value corresponding to a specific cumulative probability in the Gamma
  distribution.

- **Formula:** `GAMMA.INV(probability, alpha, beta)`
  - `probability`: The cumulative probability for which to calculate the inverse. Must be in the range 0 to 1 (
    exclusive).
  - `alpha`: The shape parameter ("k") of the Gamma distribution. Must be a positive number.
  - `beta`: The scale parameter ("θ") of the Gamma distribution. Must be a positive number.

- **Example Usage:**
  - `=GAMMA.INV(0.5, 2, 1)` computes the inverse Gamma CDF for a probability of `0.5`, with `alpha = 2` and `beta = 1`.
  - `=GAMMA.INV(0.9, 3, 0.5)` calculates the value `x` where the cumulative probability is `0.9`, with `alpha = 3` and
    `beta = 0.5`.

### [GAMMALN](./statistical-functions/gamma_ln.md)
Calculates the natural logarithm of the Gamma function value for a given input `x`. This function is often used in
statistics and mathematics where the logarithm of the Gamma function is required, avoiding direct computation of the
Gamma function itself for large values.

- **Purpose:** Useful in statistical computations, such as likelihood functions, where the natural logarithm of the
  Gamma function is leveraged for numerical stability.

- **Formula:** `GAMMALN(x)`
  - `x`: The input value for which to compute the natural logarithm of the Gamma function. Must be greater than 0.

- **Example Usage:**
  - `=GAMMALN(5)` calculates the natural logarithm of the Gamma function for `x = 5`.
  - `=GAMMALN(2.5)` computes the natural logarithm of the Gamma function for `x = 2.5`.

### [GAMMALN.PRECISE](./statistical-functions/gamma_ln_precise.md)
Calculates the natural logarithm of the Gamma function value for a given input `x`, just like `GAMMALN`, but ensures
higher precision in some scenarios. This function is particularly useful for improved numerical stability in complex
statistical and mathematical computations.

- **Purpose:** Useful in statistical computations where higher precision for the natural logarithm of the Gamma function
  is necessary.

- **Formula:** `GAMMALN.PRECISE(x)`
  - `x`: The input value for which to compute the natural logarithm of the Gamma function. Must be greater than 0.

- **Example Usage:**
  - `=GAMMALN.PRECISE(5)` calculates the natural logarithm of the Gamma function for `x = 5`.
  - `=GAMMALN.PRECISE(2.5)` computes the natural logarithm of the Gamma function for `x = 2.5`.

### [GAUSS](./statistical-functions/gauss.md)
Calculates the probability that a value drawn from a standard normal distribution (mean = 0, standard deviation = 1) is
less than or equal to a given `z`-value. The result represents the area under the standard normal curve from `-∞` to
`z`.

- **Purpose:** Useful in statistics for cumulative probability calculations in the standard normal distribution.

- **Formula:** `GAUSS(z)`
  - `z`: The `z`-score or value from the standard normal distribution.

- **Example Usage:**
  - `=GAUSS(1.5)` calculates the probability that a standard normal variable is less than or equal to `1.5`.
  - `=GAUSS(-0.5)` computes the probability for `z = -0.5`.

### [GEOMEAN](./statistical-functions/geo_mean.md)
Calculates the geometric mean of an array or range of positive numbers. The geometric mean is the nth root of the
product of `n` numbers, and is commonly used in statistics and finance.

- **Purpose:** Useful for calculating averages of ratios or percentages, avoiding the effects of extreme values.

- **Formula:** `GEOMEAN(range)`
  - `range`: The array or range of positive numbers for which to calculate the geometric mean. All values must be
    greater than 0.

- **Example Usage:**
  - `=GEOMEAN({10, 20, 30})` computes the geometric mean of the numbers 10, 20, and 30.
  - `=GEOMEAN(A1:A10)` calculates the geometric mean of the data in the range `A1:A10`.

### [GROWTH](./statistical-functions/growth.md)
Estimates exponential growth based on existing data. This function fits an exponential curve to the data and calculates
values along that curve.

- **Purpose:** Useful in forecasting and modeling exponential trends in datasets.

- **Formula:** `GROWTH(known_y's, known_x's, new_x's, const)`
  - `known_y's`: The array of known dependent values.
  - `known_x's`: (Optional) The array of known independent values. If omitted, it defaults to `{1, 2, 3, ...}`.
  - `new_x's`: (Optional) The array of new x-values for which to predict corresponding y-values. If omitted, it returns
    values for `known_x's`.
  - `const`: (Optional) A boolean value indicating whether to force the y-intercept to equal `1` (`TRUE`) or let it be
    calculated (`FALSE`).

- **Example Usage:**
  - `=GROWTH({2, 4, 8, 16}, {1, 2, 3, 4}, {5, 6}, TRUE)` calculates exponential growth for the new x-values `{5, 6}`.
  - `=GROWTH(A1:A10, B1:B10)` calculates exponential growth using the datasets in `A1:A10` and `B1:B10`.

## H

### [HARMEAN](./statistical-functions/har_mean.md)
Calculates the harmonic mean of a set of positive numbers. The harmonic mean is the reciprocal of the arithmetic mean of
the reciprocals of the data, and is useful for calculating mean rates or ratios.

- **Purpose:** Commonly used in averaging rates, such as speeds or financial ratios, where each data point carries equal
  weight.

- **Formula:** `HARMEAN(range)`
  - `range`: The array or range of positive numbers for which to calculate the harmonic mean. All values must be greater
    than 0.

- **Example Usage:**
  - `=HARMEAN({4, 5, 7, 10})` computes the harmonic mean of 4, 5, 7, and 10.
  - `=HARMEAN(A1:A10)` calculates the harmonic mean of the data in the range `A1:A10`.

### [HYPGEOM.DIST](./statistical-functions/hypgeom_dist.md)
Calculates the hypergeometric distribution, which describes the probability of a given number of successes in a sample
drawn from a finite population without replacement. This function can compute either the probability mass function (PMF)
or the cumulative distribution function (CDF).

- **Purpose:** Useful in probability and statistics problems involving a finite population and no replacement.

- **Formula:** `HYPGEOM.DIST(sample_s, number_population, successes_population, sample_size, cumulative)`
  - `sample_s`: The number of successes in the sample for which to calculate the probability.
  - `number_population`: The total number of items in the population.
  - `successes_population`: The total number of successes in the population.
  - `sample_size`: The size of the sample.
  - `cumulative`: A boolean indicating which type of distribution to compute:
    - `TRUE`: Cumulative distribution function (CDF).
    - `FALSE`: Probability mass function (PMF).

- **Example Usage:**
  - `=HYPGEOM.DIST(3, 50, 10, 5, TRUE)` calculates the cumulative distribution up to 3 successes in a sample size of 5,
    from a population of 50 containing 10 successes.
  - `=HYPGEOM.DIST(2, 100, 20, 10, FALSE)` computes the probability mass function for exactly 2 successes with the same
    parameters.

## I

### [INTERCEPT](./statistical-functions/intercept.md)
Calculates the y-intercept of the linear regression line through a set of data points. The linear regression line is
defined as the best-fit line minimizing the sum of squared differences between observed and predicted values.

- **Purpose:** Useful for finding the starting value (y-intercept) in linear models or understanding the relationship
  between two datasets.

- **Formula:** `INTERCEPT(known_y's, known_x's)`
  - `known_y's`: The dependent data values (y-axis).
  - `known_x's`: The independent data values (x-axis).

- **Example Usage:**
  - `=INTERCEPT({3, 6, 9}, {1, 2, 3})` computes the y-intercept for the given data points.
  - `=INTERCEPT(A1:A10, B1:B10)` calculates the y-intercept for the datasets in `A1:A10` (y values) and `B1:B10` (x
    values).

## K

### [KURT](./statistical-functions/kurt.md)
Calculates the kurtosis of a dataset, which measures the "tailedness" of the data distribution. Kurtosis is a
statistical measure that describes how much of the dataset lies in the tails compared to a normal distribution.

- **Purpose:** Useful for understanding the characteristics of data distribution, particularly the weight of extreme
  values in the dataset.

- **Formula:** `KURT(range)`
  - `range`: The array or range of numeric values for which to calculate the kurtosis. Must include at least four data
    points.

- **Example Usage:**
  - `=KURT({4, 5, 6, 7, 8})` calculates the kurtosis of the numbers 4, 5, 6, 7, and 8.
  - `=KURT(A1:A10)` computes the kurtosis of the data in the range `A1:A10`.

## L

### [LARGE](./statistical-functions/large.md)
Returns the k-th largest value in a dataset. This function is useful for statistical analysis where ranking of values is
needed.

- **Purpose:** Useful for finding specific largest values in a dataset, such as the highest, second-highest, or
  third-highest values.

- **Formula:** `LARGE(array, k)`
  - `array`: The array or range of data values.
  - `k`: The position (from the largest) in the array to return. Must be greater than 0 and less than or equal to the
    number of values in the array.

- **Example Usage:**
  - `=LARGE({3, 5, 1, 7, 9}, 2)` returns `7`, which is the second-largest value in the array.
  - `=LARGE(A1:A10, 1)` returns the largest value in the range `A1:A10`.

### [LINEST](./statistical-functions/linest.md)
Performs linear regression analysis to determine the statistics for a line by fitting the data to the equation
`y = mx + b`.

- **Purpose:** Useful for calculating the slope (`m`), y-intercept (`b`), and other statistics of a linear trend in your
  data.

- **Formula:** `LINEST(known_y's, known_x's, const, stats)`
  - `known_y's`: The dependent data values (y-axis).
  - `known_x's`: (Optional) The independent data values (x-axis). If omitted, defaults to `{1, 2, 3, ...}`.
  - `const`: (Optional) A boolean value indicating whether to force the y-intercept to 0 (`FALSE`) or calculate it (
    `TRUE`).
  - `stats`: (Optional) A boolean value that determines whether to return additional regression statistics (`TRUE`) or
    just slope and intercept (`FALSE`).

- **Example Usage:**
  - `=LINEST({2, 4, 6}, {1, 2, 3}, TRUE, FALSE)` calculates the slope and y-intercept for the given data.
  - `=LINEST(A1:A10, B1:B10, FALSE, TRUE)` performs a linear regression and returns additional statistics, forcing the
    y-intercept to 0.

### [LOGEST](./statistical-functions/logest.md)   
Performs exponential regression analysis to fit data to the equation `y = b * m^x` and returns an array describing the
curve.

- **Purpose:** Useful for determining the values of the exponential curve describing the given data and for analyzing
  exponential trends in a dataset.

- **Formula:** `LOGEST(known_y's, known_x's, const, stats)`
  - `known_y's`: The dependent data values (y-axis).
  - `known_x's`: (Optional) The independent data values (x-axis). If omitted, defaults to `{1, 2, 3, ...}`.
  - `const`: (Optional) A boolean value indicating whether to force the y-intercept to 1 (`TRUE`) or calculate it (
    `FALSE`).
  - `stats`: (Optional) A boolean value that determines whether to return additional regression statistics (`TRUE`) or
    just the coefficient and constant (`FALSE`).

- **Example Usage:**
  - `=LOGEST({1, 2.718, 7.389}, {1, 2, 3}, TRUE, FALSE)` calculates the base and growth for the data points.
  - `=LOGEST(A1:A10, B1:B10, FALSE, TRUE)` performs exponential regression with additional statistics and no forced
    y-intercept.

### [LOGNORMDIST](./statistical-functions/log_norm_dist.md)
Calculates the log-normal distribution of a dataset, which is useful when the logarithm of the dataset is normally
distributed. This function can compute either the probability density function (PDF) or cumulative distribution
function (CDF).

- **Purpose:** Often used in financial and reliability analysis where data is log-normal rather than normal.

- **Formula:** `LOGNORMDIST(x, mean, standard_dev, cumulative)`
  - `x`: The value for which to evaluate the log-normal distribution.
  - `mean`: The mean of the natural logarithm of the dataset.
  - `standard_dev`: The standard deviation of the natural logarithm of the dataset.
 

- **Example Usage:**
  - `=LOGNORMDIST(7, 1.5, 0.75)` calculates the cumulative log-normal distribution for `x = 7`.
  - `=LOGNORMDIST(5, 1.2, 0.6)` computes the probability density function for `x = 5`.

### [LOGNORM.DIST](./statistical-functions/log_norm__dist.md)
Calculates the log-normal distribution of a value, which is useful when the logarithm of the dataset is normally
distributed. This function can compute either the probability density function (PDF) or cumulative distribution
function (CDF).

- **Purpose:** Often used in fields like finance, biology, and reliability analysis where data follows a log-normal
  distribution.

- **Formula:** `LOGNORM.DIST(x, mean, standard_dev, cumulative)`
  - `x`: The value for which to evaluate the log-normal distribution.
  - `mean`: The mean of the natural logarithm.
  - `standard_dev`: The standard deviation of the natural logarithm.
  - `cumulative`: A boolean indicating which type of distribution to compute:
    - `TRUE`: Cumulative distribution function (CDF).
    - `FALSE`: Probability density function (PDF).

- **Example Usage:**
  - `=LOGNORM.DIST(7, 1.5, 0.75, TRUE)` calculates the cumulative log-normal distribution for `x = 7`.
  - `=LOGNORM.DIST(5, 1.2, 0.6, FALSE)` computes the probability density function for `x = 5`.

### [LOGNORM.INV](./statistical-functions/log_norm_inv.md)
Calculates the inverse of the log-normal cumulative distribution function of a value. This function is useful in
scenarios where you need to determine the input for a given cumulative probability under a log-normal distribution.

- **Purpose:** Commonly used in fields like finance, biology, and engineering where log-normal distributions are
  applicable.

- **Formula:** `LOGNORM.INV(probability, mean, standard_dev)`
  - `probability`: A probability associated with the log-normal distribution.
  - `mean`: The mean of the natural logarithm of the dataset.
  - `standard_dev`: The standard deviation of the natural logarithm of the dataset.

- **Example Usage:**
  - `=LOGNORM.INV(0.5, 1.5, 0.75)` computes the value for which the cumulative log-normal distribution is `0.5`.
  - `=LOGNORM.INV(0.9, 2.3, 1.0)` calculates the value corresponding to the 90th percentile of the distribution.

### [LOGINV](./statistical-functions/log_inv.md)
Calculates the inverse of the cumulative normal distribution for a value. This function is useful for determining the
input value associated with a given probability in a standard log-normal distribution.

- **Purpose:** Commonly used in statistics and financial analysis for back-calculating original values from
  probabilities under a log-normal distribution.

- **Formula:** `LOGINV(probability, mean, standard_dev)`
  - `probability`: A probability associated with the log-normal distribution (must be between 0 and 1, inclusive).
  - `mean`: The mean of the natural logarithm of the dataset.
  - `standard_dev`: The standard deviation of the natural logarithm of the dataset.

- **Example Usage:**
  - `=LOGINV(0.5, 1.5, 0.75)` computes the value corresponding to the 50th percentile of the log-normal distribution.
  - `=LOGINV(0.1, 2.3, 1.0)` calculates the value corresponding to the 10th percentile of the distribution.

## M

### [MAXA](./statistical-functions/maxa.md)
Returns the largest value in a set of values, including logical values and text representations of numbers. Unlike
`MAX`, `MAXA` evaluates `TRUE` as `1`, `FALSE` as `0`, and text as `0`.

- **Purpose:** Useful for finding the maximum value in datasets that include logical values or mixed data types.

- **Formula:** `MAXA(value1, [value2], ...)`
  - `value1, [value2], ...`: The values, references, or ranges to evaluate for the maximum.

- **Example Usage:**
  - `=MAXA(10, 20, 30, TRUE)` returns `30`, treating `TRUE` as `1`.
  - `=MAXA(-5, -10, FALSE, "Hello")` returns `0`, treating `FALSE` and text as `0`.

### [MAXIFS](./statistical-functions/max_ifs.md)
Returns the maximum value from a range of numbers based on one or more criteria. This function is useful for finding the
largest value within a subset of data that meets specific conditions.

- **Purpose:** Useful for conditional calculations where you need to determine the maximum value subject to multiple
  criteria.

- **Formula:** `MAXIFS(max_range, criteria_range1, criteria1, [criteria_range2, criteria2], …)`
  - `max_range`: The range of numeric values to be evaluated for the maximum.
  - `criteria_range1`: The range of data to evaluate against the first condition.
  - `criteria1`: The condition that determines which values in `criteria_range1` to include.
  - `[criteria_range2, criteria2]`: Additional optional criteria ranges and conditions.

- **Example Usage:**
  - `=MAXIFS(A1:A10, B1:B10, ">5")` returns the maximum value in `A1:A10` where the corresponding value in `B1:B10` is
    greater than `5`.
  - `=MAXIFS(A1:A10, B1:B10, ">=10", C1:C10, "<20")` finds the maximum value in `A1:A10` where the corresponding values
    in `B1:B10` are `>=10` and in `C1:C10` are `<20`.

### [MINA](./statistical-functions/mina.md)
Returns the smallest value in a set of values, including logical values and text representations of numbers. Unlike
`MIN`, `MINA` evaluates `TRUE` as `1`, `FALSE` as `0`, and text as `0`.

- **Purpose:** Useful for finding the minimum value in datasets that include logical values or mixed data types.

- **Formula:** `MINA(value1, [value2], ...)`
  - `value1, [value2], ...`: The values, references, or ranges to evaluate for the minimum.

- **Example Usage:**
  - `=MINA(10, 20, 30, TRUE)` returns `1`, treating `TRUE` as `1`.
  - `=MINA(5, 10, FALSE, "Hello")` returns `0`, treating `FALSE` and text as `0`.

### [MINIFS](./statistical-functions/min_ifs.md)
Returns the minimum value from a range of numbers based on one or more criteria. This function is useful for finding the
smallest value within a subset of data that meets specific conditions.

- **Purpose:** Useful for conditional calculations where you need to determine the minimum value subject to multiple
  criteria.

- **Formula:** `MINIFS(min_range, criteria_range1, criteria1, [criteria_range2, criteria2], …)`
  - `min_range`: The range of numeric values to be evaluated for the minimum.
  - `criteria_range1`: The range of data to evaluate against the first condition.
  - `criteria1`: The condition that determines which values in `criteria_range1` to include.
  - `[criteria_range2, criteria2]`: Additional optional criteria ranges and conditions.

- **Example Usage:**
  - `=MINIFS(A1:A10, B1:B10, ">5")` returns the minimum value in `A1:A10` where the corresponding value in `B1:B10` is
    greater than `5`.
  - `=MINIFS(A1:A10, B1:B10, ">=10", C1:C10, "<20")` finds the minimum value in `A1:A10` where the corresponding values
    in `B1:B10` are `>=10` and in `C1:C10` are `<20`.

### [MEDIAN](./statistical-functions/median.md)
Returns the median of the given numbers. The median is the middle number in a sorted dataset. If the dataset contains an
even number of values, the median is the average of the two central numbers.

- **Purpose:** Useful for identifying the central tendency of a dataset, especially for non-normal distributions where
  the mean might be skewed by outliers.

- **Formula:** `MEDIAN(range)`
  - `range`: The array or range of numeric values for which to calculate the median.

- **Example Usage:**
  - `=MEDIAN({1, 3, 3, 6, 7, 8, 9})` returns `6`, the middle number in the sorted dataset.
  - `=MEDIAN(A1:A10)` computes the median of the data in the range `A1:A10`.

### [MODE](./statistical-functions/mode.md)
Returns the most frequently occurring value(s) in a dataset. If there are multiple modes, it returns only one of them (
usually the first one encountered). This function is useful when you need a simplified result compared to `MODE.MULT`.

- **Purpose:** Useful for identifying a single most common value in a dataset where you do not need to consider multiple
  modes.

- **Formula:** `MODE(range)`
  - `range`: The array or range of numeric values for which to calculate the mode.

- **Note:** Unlike `MODE.MULT`, this function does not return multiple mode values even if they exist.

- **Example Usage:**
  - `=MODE({1, 2, 2, 3, 3, 4})` returns `2`, the first mode encountered.
  - `=MODE(A1:A10)` calculates the single mode of the dataset in range `A1:A10`.

### [MODE.MULT](./statistical-functions/mode_mult.md)
Returns the vertical array of the most frequently occurring value(s) in a dataset. If there are multiple modes, all are
returned in the order they appear. This function is useful for statistical analysis when identifying frequent values in
a dataset.

- **Purpose:** Useful for finding the modes in a dataset, especially when multiple modes are present.

- **Formula:** `MODE.MULT(range)`
  - `range`: The array or range of numeric values for which to calculate the mode(s).

- **Note:** Since this function returns multiple values, it must be entered as an **array formula** for all modes to
  appear.

- **Example Usage:**
  - `=MODE.MULT({1, 2, 2, 3, 3, 4})` returns `{2, 3}`, as both `2` and `3` are modes.
  - `=MODE.MULT(A1:A10)` calculates the modes of the dataset in range `A1:A10`.

### [MODE.SNGL](./statistical-functions/mode_sngl.md)
Returns the single most frequently occurring value in a dataset. If there are multiple modes, it returns the first mode
it encounters. Useful for identifying the most common value in a dataset.

- **Purpose:** Useful for finding the single most frequent value in a dataset.

- **Formula:** `MODE.SNGL(range)`
  - `range`: The array or range of numeric values for which to calculate the mode.

- **Example Usage:**
  - `=MODE.SNGL({1, 2, 2, 3, 3, 4})` returns `2`, the first mode encountered.
  - `=MODE.SNGL(A1:A10)` calculates the single mode of the dataset in range `A1:A10`.

## N

### [NEGBINOMDIST](./statistical-functions/neg_binom_dist.md)
Calculates the negative binomial distribution, which represents the probability of a specified number of failures
occurring before a given number of successes. This is useful in scenarios like predicting the number of trials required
to achieve a fixed number of successes.

- **Purpose:** Commonly used in statistical modeling and quality control to evaluate probabilities of events in repeated
  independent trials.

- **Formula:** `NEGBINOMDIST(x, r, p)`
  - `x`: The number of failures before the `r`th success.
  - `r`: The number of successes.
  - `p`: The probability of success on a single trial.

- **Example Usage:**
  - `=NEGBINOMDIST(4, 3, 0.6)` calculates the probability of observing 4 failures before 3 successes with a success
    probability of 0.6.
  - `=NEGBINOMDIST(A1, B1, C1)` computes the negative binomial distribution using values from cells `A1`, `B1`, and `C1`.

### [NEGBINOM.DIST](./statistical-functions/neg_binom__dist.md)
Calculates the negative binomial distribution, which represents the probability of a specified number of failures
occurring before a given number of successes. This function allows computation of either the probability mass function (
PMF) or cumulative distribution function (CDF).

- **Purpose:** Commonly used in statistical modeling and quality control to evaluate probabilities of events in repeated
  independent trials.

- **Formula:** `NEGBINOM.DIST(x, r, p, cumulative)`
  - `x`: The number of failures before the `r`th success.
  - `r`: The number of successes.
  - `p`: The probability of success on a single trial.
  - `cumulative`: A boolean indicating which type of distribution to compute:
    - `TRUE`: Cumulative distribution function (CDF).
    - `FALSE`: Probability mass function (PMF).

- **Example Usage:**
  - `=NEGBINOM.DIST(4, 3, 0.6, FALSE)` calculates the probability of observing 4 failures before 3 successes with a
    success probability of 0.6 (PMF).
  - `=NEGBINOM.DIST(4, 3, 0.6, TRUE)` calculates the cumulative probability of observing up to 4 failures before 3
    successes with a success probability of 0.6.
  - `=NEGBINOM.DIST(A1, B1, C1, FALSE)` calculates the negative binomial distribution using values from cells `A1`,
    `B1`, and `C1` (PMF).

### [NORMDIST](./statistical-functions/norm_dist.md)
Calculates the normal distribution for a value using the specified mean and standard deviation. This function can
compute either the probability density function (PDF) or cumulative distribution function (CDF).

- **Purpose:** Useful for analyzing data assumed to follow a normal distribution, such as in probability and statistics.

- **Formula:** `NORMDIST(x, mean, standard_dev, cumulative)`
  - `x`: The value for which to evaluate the distribution.
  - `mean`: The arithmetic mean of the distribution.
  - `standard_dev`: The standard deviation of the distribution.
  - `cumulative`: A boolean indicating which type of distribution to compute:
    - `TRUE`: Cumulative distribution function (CDF).
    - `FALSE`: Probability density function (PDF).

- **Example Usage:**
  - `=NORMDIST(5, 0, 1, TRUE)` calculates the cumulative standard normal distribution at `x = 5`.
  - `=NORMDIST(5, 0, 1, FALSE)` computes the probability density function for `x = 5`.
  - `=NORMDIST(A1, B1, C1, TRUE)` evaluates the cumulative normal distribution for the value in cell `A1`, with mean and
    standard deviation from cells `B1` and `C1`.

### [NORM.DIST](./statistical-functions/norm__dist.md)
Calculates the normal distribution for a given value, using the specified mean and standard deviation. This function can
compute either the probability density function (PDF) or cumulative distribution function (CDF).

- **Purpose:** Useful for analyzing data under a normal distribution assumption, as commonly required in probability and
  statistics.

- **Formula:** `NORM.DIST(x, mean, standard_dev, cumulative)`
  - `x`: The value for which to evaluate the distribution.
  - `mean`: The arithmetic mean of the distribution.
  - `standard_dev`: The standard deviation of the distribution.
  - `cumulative`: A boolean indicating which type of distribution to compute:
    - `TRUE`: Cumulative distribution function (CDF).
    - `FALSE`: Probability density function (PDF).

- **Example Usage:**
  - `=NORM.DIST(5, 0, 1, TRUE)` calculates the cumulative normal distribution at `x = 5`.
  - `=NORM.DIST(5, 0, 1, FALSE)` computes the probability density function for `x = 5`.
  - `=NORM.DIST(A1, B1, C1, TRUE)` evaluates the cumulative normal distribution for the value in cell `A1`, using the
    mean and standard deviation provided in cells `B1` and `C1`.

### [NORMINV](./statistical-functions/norm_inv.md)
Calculates the inverse of the normal cumulative distribution for a specified value. This function is useful for finding
the data point corresponding to a given probability under a normal distribution.

- **Purpose:** Commonly used in fields like statistics and finance to determine values from a normal distribution
  corresponding to a given cumulative probability.

- **Formula:** `NORMINV(probability, mean, standard_dev)`
  - `probability`: A probability associated with the normal distribution (must be between 0 and 1).
  - `mean`: The arithmetic mean of the distribution.
  - `standard_dev`: The standard deviation of the distribution.

- **Example Usage:**
  - `=NORMINV(0.5, 0, 1)` returns `0`, as `0.5` is the cumulative probability for the mean of the standard normal
    distribution.
  - `=NORMINV(0.9, 10, 2)` calculates the value corresponding to the 90th percentile for a normal distribution with a
    mean of `10` and a standard deviation of `2`.
  - `=NORMINV(A1, B1, C1)` computes the inverse of the normal cumulative distribution for the probability in cell `A1`,
    with mean and standard deviation from cells `B1` and `C1`.

### [NORM.INV](./statistical-functions/norm__inv.md)
Calculates the inverse of the normal cumulative distribution for a specified value. This function is useful for finding
the data point corresponding to a given probability under a normal distribution.

- **Purpose:** Commonly used in statistics, finance, and probability to determine values from a normal distribution
  corresponding to a provided cumulative probability.

- **Formula:** `NORM.INV(probability, mean, standard_dev)`
  - `probability`: A probability associated with the normal distribution (must be between 0 and 1).
  - `mean`: The arithmetic mean of the distribution.
  - `standard_dev`: The standard deviation of the distribution.

- **Example Usage:**
  - `=NORM.INV(0.5, 0, 1)` returns `0`, since `0.5` is the cumulative probability for the mean of the standard normal
    distribution.
  - `=NORM.INV(0.9, 10, 2)` calculates the value corresponding to the 90th percentile for a normal distribution with a
    mean of `10` and a standard deviation of `2`.
  - `=NORM.INV(A1, B1, C1)` computes the inverse of the normal cumulative distribution for the probability in cell `A1`,
    with mean and standard deviation from cells `B1` and `C1`.

### [NORMSDIST](./statistical-functions/norm_s_dist.md)
Calculates the cumulative standard normal distribution function for a given value, assuming a mean of 0 and a standard
deviation of 1. This is a specific case of the normal distribution function for standard normal variables.

- **Purpose:** Useful for analyzing probabilities under the standard normal curve.

- **Formula:** `NORMSDIST(z)`
  - `z`: The value for which to calculate the cumulative standard normal distribution.

- **Example Usage:**
  - `=NORMSDIST(1.96)` calculates the cumulative probability of a standard normal variable being less than or equal to
    1.96.
  - `=NORMSDIST(A1)` computes the cumulative standard normal distribution for the value in cell `A1`.

### [NORM.S.DIST](./statistical-functions/norm__s__dist.md)
Calculates the standard normal distribution for a specified value with a mean of 0 and a standard deviation of 1. This
function can compute either the probability density function (PDF) or cumulative distribution function (CDF).

- **Purpose:** Useful for analyzing probabilities and data under the standard normal distribution curve.

- **Formula:** `NORM.S.DIST(z, cumulative)`
  - `z`: The value for which to evaluate the standard normal distribution.
  - `cumulative`: A boolean indicating which type of distribution to compute:
    - `TRUE`: Cumulative distribution function (CDF).
    - `FALSE`: Probability density function (PDF).

- **Example Usage:**
  - `=NORM.S.DIST(1.96, TRUE)` calculates the cumulative standard normal distribution at `z = 1.96`.
  - `=NORM.S.DIST(1.96, FALSE)` computes the probability density function for `z = 1.96`.
  - `=NORM.S.DIST(A1, TRUE)` evaluates the cumulative standard normal distribution for the value in cell `A1`.

### [NORMSINV](./statistical-functions/norm_s_inv.md)
Calculates the inverse of the standard normal cumulative distribution. This function determines the z-value such that
the cumulative standard normal probability corresponds to a specified value.

- **Purpose:** Commonly used in statistics to find the z-value (standard score) for a given cumulative probability under
  the standard normal distribution.

- **Formula:** `NORMSINV(probability)`
  - `probability`: A cumulative probability value (must be between 0 and 1).

- **Example Usage:**
  - `=NORMSINV(0.5)` returns `0`, as `0.5` is the cumulative probability at the mean of the standard normal
    distribution.
  - `=NORMSINV(0.9)` calculates the z-value corresponding to the 90th percentile of the standard normal distribution.
  - `=NORMSINV(A1)` computes the z-value for the cumulative probability in cell `A1`.

### [NORM.S.INV](./statistical-functions/norm__s__inv.md)
Calculates the inverse of the standard normal cumulative distribution. This function determines the z-value such that
the cumulative standard normal probability corresponds to the specified value.

- **Purpose:** Useful in probability and statistics to find the z-value (standard score) for a given cumulative
  probability under a standard normal distribution.

- **Formula:** `NORM.S.INV(probability)`
  - `probability`: A probability value (must be between 0 and 1) representing the cumulative standard normal
    distribution.

- **Example Usage:**
  - `=NORM.S.INV(0.5)` returns `0`, since `0.5` is the cumulative probability for the mean of the standard normal
    distribution.
  - `=NORM.S.INV(0.9)` calculates the z-value corresponding to the 90th percentile under the standard normal
    distribution.
  - `=NORM.S.INV(A1)` computes the z-value for the cumulative probability specified in cell `A1`.

## P

### [PEARSON](./statistical-functions/pearson.md)
Calculates the Pearson product-moment correlation coefficient, which measures the strength and direction of the
linear relationship between two datasets.

- **Purpose:** Commonly used in statistics to determine the correlation between two variables and quantify their
  degree of linear relationship.

- **Formula:** `PEARSON(array1, array2)`
  - `array1`: The first data array or range.
  - `array2`: The second data array or range.

- **Example Usage:**
  - `=PEARSON(A1:A10, B1:B10)` calculates the correlation coefficient between the data in ranges `A1:A10` and `B1:B10`.
  - `=PEARSON({1, 2, 3}, {4, 5, 6})` computes the correlation coefficient for the two given arrays.
  - `=PEARSON(C1:C100, D1:D100)` evaluates the correlation between the datasets represented in columns `C` and `D`.

### [PERCENTILE](./statistical-functions/percentile.md)
Calculates the k-th percentile of a dataset using interpolation between values in the dataset. This function is used to
determine a value below which a specific percentage of data in a dataset falls.

- **Purpose:** Useful in statistical analysis for estimating percentile values.

- **Formula:** `PERCENTILE(array, k)`
  - `array`: The array or range of data for which to determine the k-th percentile.
  - `k`: The percentile to calculate (a number between 0 and 1).

- **Example Usage:**
  - `=PERCENTILE(A1:A10, 0.25)` calculates the 25th percentile of the data in the range `A1:A10`.
  - `=PERCENTILE({1, 2, 3, 4, 5}, 0.5)` computes the 50th percentile (median) of the array `{1, 2, 3, 4, 5}`.
  - `=PERCENTILE(C1:C100, 0.9)` determines the 90th percentile of the dataset in column `C`.

### [PERCENTILE.EXC](./statistical-functions/percentile__exc.md)
Calculates the k-th percentile of a dataset, where k is a value between 0 and 1, exclusive. This function excludes the
percentile values that fall exactly on the endpoints (minimum and maximum) of the data set.

- **Purpose:** Used to determine a value below which a specific percentage of data in a dataset falls, excluding the
  endpoints.

- **Formula:** `PERCENTILE.EXC(array, k)`
  - `array`: The array or range of data for which to determine the k-th percentile.
  - `k`: The percentile to calculate (a number between 0 and 1, excluding 0 and 1).

- **Example Usage:**
  - `=PERCENTILE.EXC(A1:A10, 0.25)` calculates the 25th percentile of the data in range `A1:A10`.
  - `=PERCENTILE.EXC({1, 2, 3, 4, 5}, 0.5)` computes the 50th percentile (median) of the array `{1, 2, 3, 4, 5}`
    excluding the minimum and maximum values.
  - `=PERCENTILE.EXC(C1:C100, 0.9)` determines the 90th percentile of the dataset in column `C`.

### [PERCENTILE.INC](./statistical-functions/percentile__inc.md)
Calculates the k-th percentile of a dataset, where k is a value between 0 and 1, inclusive. This function includes the
percentile values that fall exactly on the endpoints (minimum and maximum) of the data set.

- **Purpose:** Used to determine a value below which a specific percentage of data in a dataset falls, including the
  endpoints.

- **Formula:** `PERCENTILE.INC(array, k)`
  - `array`: The array or range of data for which to determine the k-th percentile.
  - `k`: The percentile to calculate (a number between 0 and 1, inclusive).

- **Example Usage:**
  - `=PERCENTILE.INC(A1:A10, 0.25)` calculates the 25th percentile of the data in range `A1:A10`.
  - `=PERCENTILE.INC({1, 2, 3, 4, 5}, 0.5)` computes the 50th percentile (median) of the array `{1, 2, 3, 4, 5}`
    including the minimum and maximum values.
  - `=PERCENTILE.INC(C1:C100, 0.9)` determines the 90th percentile of the dataset in column `C`.


### [PERCENTRANK.EXC](./statistical-functions/percent_rank__exc.md)
Calculates the rank of a value in a dataset as a percentage (excluding the endpoints). The rank is a value between 0 and
1, exclusive.

- **Purpose:** Useful for determining the relative standing of a value in a dataset, excluding minimum and maximum
  values.

- **Formula:** `PERCENTRANK.EXC(array, x, [significance])`
  - `array`: The array or range of data.
  - `x`: The value for which to calculate the percentile rank.
  - `significance`: (Optional) The number of significant digits for the returned percentage. Default is 3.

- **Example Usage:**
  - `=PERCENTRANK.EXC(A1:A10, 5)` calculates the percentile rank of the value `5` in the dataset `A1:A10`, excluding the
    endpoints.
  - `=PERCENTRANK.EXC({10, 20, 30, 40, 50}, 25)` computes the percentile rank of `25` in the array
    `{10, 20, 30, 40, 50}`.
  - `=PERCENTRANK.EXC(B1:B100, C1, 4)` calculates the percentile rank for the value in cell `C1` within the dataset in
    range `B1:B100`, rounded to four significant digits.

### [PERCENTRANK.INC](./statistical-functions/percent_rank__inc.md)
Calculates the rank of a value in a dataset as a percentage (including the endpoints). The rank is a value between 0 and
1, inclusive.

- **Purpose:** Useful for determining the relative standing of a value in a dataset, including minimum and maximum
  values.

- **Formula:** `PERCENTRANK.INC(array, x, [significance])`
  - `array`: The array or range of data.
  - `x`: The value for which to calculate the percentile rank.
  - `significance`: (Optional) The number of significant digits for the returned percentage. Default is 3.

- **Example Usage:**
  - `=PERCENTRANK.INC(A1:A10, 5)` calculates the percentile rank of the value `5` in the dataset `A1:A10`, including the
    endpoints.
  - `=PERCENTRANK.INC({10, 20, 30, 40, 50}, 25)` computes the percentile rank of `25` in the array
    `{10, 20, 30, 40, 50}`.
  - `=PERCENTRANK.INC(B1:B100, C1, 4)` calculates the percentile rank for the value in cell `C1` within the dataset in
    range `B1:B100`, rounded to four significant digits.

### [PERMUT](./statistical-functions/permut.md)
Returns the number of permutations for a given number of objects that can be selected from a larger set. A permutation
is
an arrangement of objects where the order is significant.

- **Purpose:** Useful in combinatorics and probability to calculate the total arrangements of items in a specific order.

- **Formula:** `PERMUT(number, number_chosen)`
  - `number`: The total number of items available.
  - `number_chosen`: The number of items to select and arrange (must be ≤ `number`, and both `number` and
    `number_chosen` must be non-negative).

- **Example Usage:**
  - `=PERMUT(5, 3)` calculates the number of permutations when selecting and arranging 3 items from a set of 5.
  - `=PERMUT(A1, B1)` computes the number of permutations based on the values in cells `A1` and `B1`.
  - `=PERMUT(10, 2)` returns the number of permutations when choosing 2 items out of 10.

### [PERMUTATIONA](./statistical-functions/permutation_a.md)
Returns the number of permutations for a given number of objects (with repetitions) that can be selected from a larger
set. A permutation with repetitions allows the same object to appear multiple times in an arrangement.

- **Purpose:** Useful in combinatorics and probability to calculate the total arrangements of items when repetitions are
  allowed.

- **Formula:** `PERMUTATIONA(number, number_chosen)`
  - `number`: The total number of items available.
  - `number_chosen`: The number of items to select and arrange (must be non-negative, and `number` must be ≥ 1).

- **Example Usage:**
  - `=PERMUTATIONA(4, 3)` calculates the number of permutations with repetitions when selecting and arranging 3 items
    from a set of 4.
  - `=PERMUTATIONA(A1, B1)` computes the number of permutations with repetitions based on the values in cells `A1` and
    `B1`.
  - `=PERMUTATIONA(10, 2)` returns the number of permutations with repetitions when choosing 2 items out of 10.

### [PHI](./statistical-functions/phi.md)
Returns the value of the probability density function (PDF) for the standard normal distribution at a given value.

- **Purpose:** Commonly used in statistics to calculate the height of the standard normal distribution curve at a
  specific point.

- **Formula:** `PHI(x)`
  - `x`: The value at which to evaluate the standard normal distribution.

- **Example Usage:**
  - `=PHI(0)` returns `0.3989422804`, as this is the height of the standard normal distribution at the mean (0).
  - `=PHI(1)` calculates the probability density at `x = 1` for the standard normal distribution.
  - `=PHI(A1)` computes the PDF value at the number in cell `A1` under the standard normal distribution.

### [POISSON](./statistical-functions/poisson.md)
Calculates the Poisson distribution, which is used to predict the number of events occurring within a fixed interval of
time or space when the events occur with a known constant mean rate and independently of the time since the last event.

- **Purpose:** Useful in probability and statistics for modeling the number of events in a given interval, such as the
  number of occurrences of a specific event in a time frame.

- **Formula:** `POISSON(x, mean, cumulative)`
  - `x`: The number of events (must be a non-negative integer).
  - `mean`: The expected mean number of events (must be a positive number).
  - `cumulative`: A logical value that determines the form of the function.
    - If `TRUE`, returns the cumulative distribution function (CDF), which is the probability that the number of events
      will be ≤ `x`.
    - If `FALSE`, returns the probability mass function (PMF), which is the probability of exactly `x` events occurring.

- **Example Usage:**
  - `=POISSON(2, 4, FALSE)` calculates the probability of exactly 2 events occurring when the mean number of events is
    4.
  - `=POISSON(3, 5, TRUE)` calculates the cumulative probability of observing 3 or fewer events when the mean number of
    events is 5.
  - `=POISSON(A1, B1, FALSE)` computes the probability mass function using the value in cell `A1` for `x` and `B1` for
    the mean.

### [POISSON.DIST](./statistical-functions/poisson__dist.md)
Calculates the Poisson distribution, which is used to predict the number of events occurring within a fixed interval of
time or space when the events occur with a known constant mean rate and independently of the time since the last event.

- **Purpose:** Useful in probability and statistics for modeling the number of events in a given interval, such as the
  number of occurrences of a specific event in a time frame.

- **Formula:** `POISSON.DIST(x, mean, cumulative)`
  - `x`: The number of events (must be a non-negative integer).
  - `mean`: The expected mean number of events (must be a positive number).
  - `cumulative`: A logical value that determines the form of the function.
    - If `TRUE`, returns the cumulative distribution function (CDF), which is the probability that the number of events
      will be ≤ `x`.
    - If `FALSE`, returns the probability mass function (PMF), which is the probability of exactly `x` events occurring.

- **Example Usage:**
  - `=POISSON.DIST(2, 4, FALSE)` calculates the probability of exactly 2 events occurring when the mean number of events
    is 4.
  - `=POISSON.DIST(3, 5, TRUE)` calculates the cumulative probability of observing 3 or fewer events when the mean
    number of events is 5.
  - `=POISSON.DIST(A1, B1, FALSE)` computes the probability mass function using the value in cell `A1` for `x` and `B1`
    for the mean.

### [PROB](./statistical-functions/prob.md)
Calculates the probability that values in a range are between two limits, based on the supplied probabilities for each
value.

- **Purpose:** Useful in statistics for calculating probabilities for a discrete dataset given a custom probability
  distribution.

- **Formula:** `PROB(x_range, prob_range, lower_limit, [upper_limit])`
  - `x_range`: The array or range of numeric values corresponding to the probabilities.
  - `prob_range`: The array or range of probabilities associated with the values in `x_range`. The sum of these
    probabilities must equal 1.
  - `lower_limit`: The lower bound of the range for which to calculate the probability. If omitted, it
    assumes the value of `upper_limit`.
  - `upper_limit`: (Optional) The upper bound of the range for which to calculate the probability. If omitted, it
    calculates the probability for `lower_limit` only.

- **Example Usage:**
  - `=PROB(A1:A10, B1:B10, 3, 6)` calculates the probability that values in the range `A1:A10` are between 3 and 6,
    using the probabilities in `B1:B10`.
  - `=PROB(A1:A10, B1:B10, 4)` calculates the probability that the value in `A1:A10` equals 4, using the probabilities
    from `B1:B10`.
  - `=PROB({1, 2, 3, 4}, {0.1, 0.2, 0.4, 0.3}, 2, 3)` computes the probability that values in `{1, 2, 3, 4}` are between
    2 and 3, with the probabilities `{0.1, 0.2, 0.4, 0.3}`.

### [QUARTILE.EXC](./statistical-functions/quartile__exc.md)
Returns the quartile of a dataset, based on percentile values exclusive of the data set’s minimum and maximum values.

- **Purpose:** Useful in statistical analysis for dividing a data set into exclusive quartile groups (values between
  percentiles 0 and 100), excluding the extremes (0% and 100%).

- **Formula:** `QUARTILE.EXC(array, quart)`
  - `array`: The range or array of numerical data to analyze.
  - `quart`: The quartile to return:
    - `1`: The 1st quartile (25th percentile).
    - `2`: The 2nd quartile (median/50th percentile).
    - `3`: The 3rd quartile (75th percentile).

- **Example Usage:**
  - `=QUARTILE.EXC(A1:A10, 1)` returns the 1st quartile (25th percentile) of the data in range `A1:A10`, excluding the
    minimum and maximum values.
  - `=QUARTILE.EXC({1, 2, 3, 4, 5, 6, 7, 8, 9}, 2)` calculates the median of the dataset `{1, 2, 3, 4, 5, 6, 7, 8, 9}`,
    excluding the extremes.
  - `=QUARTILE.EXC(A1:A10, 3)` computes the 3rd quartile (75th percentile) of the values in range `A1:A10`.

### [QUARTILE.INC](./statistical-functions/quartile__inc.md)
Returns the quartile of a dataset, based on percentile values inclusive of the data set’s minimum and maximum values.

- **Purpose:** Useful in statistical analysis for dividing a data set into quartile groups (values between percentiles 0
  and 100), including the extremes (0% and 100%).

- **Formula:** `QUARTILE.INC(array, quart)`
  - `array`: The range or array of numerical data to analyze.
  - `quart`: The quartile to return:
    - `0`: The minimum value (0th percentile).
    - `1`: The 1st quartile (25th percentile).
    - `2`: The 2nd quartile (median/50th percentile).
    - `3`: The 3rd quartile (75th percentile).
    - `4`: The maximum value (100th percentile).

- **Example Usage:**
  - `=QUARTILE.INC(A1:A10, 1)` returns the 1st quartile (25th percentile) of the data in range `A1:A10`, including the
    minimum and maximum values.
  - `=QUARTILE.INC({1, 2, 3, 4, 5, 6, 7, 8, 9}, 2)` calculates the median (50th percentile) of the dataset
    `{1, 2, 3, 4, 5, 6, 7, 8, 9}`, including the extremes.
  - `=QUARTILE.INC(A1:A10, 4)` computes the maximum value (100th percentile) from the range `A1:A10`.

### [RANK.AVG](./statistical-functions/rank__avg.md)
Returns the rank of a number in a list of numbers. The rank is the average rank of the number in case of ties.

- **Purpose:** Useful in ranking values in a dataset while handling duplicate values by assigning them an average rank.

- **Formula:** `RANK.AVG(number, ref, [order])`
  - `number`: The number whose rank you want to find.
  - `ref`: The array or range of numbers containing the dataset.
  - `order`: (Optional) A number that specifies the ranking order:
    - `0` or omitted: Ranks the numbers in descending order.
    - `1`: Ranks the numbers in ascending order.

- **Example Usage:**
  - `=RANK.AVG(10, A1:A10)` ranks the value `10` in the range `A1:A10` in descending order.
  - `=RANK.AVG(10, A1:A10, 1)` ranks the value `10` in the range `A1:A10` in ascending order.
  - `=RANK.AVG(A1, B1:B10)` computes the rank of the value in cell `A1` within the range `B1:B10` in descending order.

### [RANK.EQ](./statistical-functions/rank__eq.md)
Returns the rank of a number in a list of numbers. The rank of a number is its position relative to other numbers in the
list, and in the case of ties, the top rank is assigned.

- **Purpose:** Useful in ranking values in a dataset where duplicate values share the highest rank.

- **Formula:** `RANK.EQ(number, ref, [order])`
  - `number`: The number whose rank you want to find.
  - `ref`: The array or range of numbers containing the dataset.
  - `order`: (Optional) A number that specifies the ranking order:
    - `0` or omitted: Ranks the numbers in descending order.
    - `1`: Ranks the numbers in ascending order.

- **Example Usage:**
  - `=RANK.EQ(10, A1:A10)` ranks the value `10` in the range `A1:A10` in descending order.
  - `=RANK.EQ(10, A1:A10, 1)` ranks the value `10` in the range `A1:A10` in ascending order.
  - `=RANK.EQ(A1, B1:B10)` computes the rank of the value in cell `A1` within the range `B1:B10` in descending order.

### [RSQ](./statistical-functions/rsq.md)
Calculates the square of the Pearson product-moment correlation coefficient (`R^2`) for two data ranges.

- **Purpose:** Used to determine how well the data in two ranges fit a linear regression line, providing an indication
  of the strength of the linear relationship.

- **Formula:** `RSQ(known_y's, known_x's)`
  - `known_y's`: The range or array of dependent variable data.
  - `known_x's`: The range or array of independent variable data.

- **Example Usage:**
  - `=RSQ(A1:A10, B1:B10)` calculates the R-squared value for the linear relationship between the data in `A1:A10`
    (dependent variables) and `B1:B10` (independent variables).
  - `=RSQ({3, 4, 5}, {1, 2, 3})` computes the R-squared value for the given arrays of dependent and independent data.
  - `=RSQ(C1:C5, D1:D5)` evaluates the R-squared value for the data in ranges `C1:C5` and `D1:D5`.

## S

### [SKEW](./statistical-functions/skew.md)
Measures the skewness of a dataset, which is the degree of asymmetry of the data distribution around its mean.

- **Purpose:** Useful for analyzing the shape of a dataset's distribution. Positive skewness indicates a distribution
  with a tail on the right (longer right tail), and negative skewness indicates a tail on the left (longer left tail).

- **Formula:** `SKEW(array)`
  - `array`: The range or array of numerical data to analyze.

- **Example Usage:**
  - `=SKEW(A1:A10)` calculates the skewness of the data in range `A1:A10`.
  - `=SKEW({3, 7, 8, 1, 9})` computes the skewness of the dataset `{3, 7, 8, 1, 9}`.
  - `=SKEW(B2:B20)` determines the skewness of the numerical values in `B2:B20`.

### [SKEW.P](./statistical-functions/skew__p.md)
Measures the skewness of a population dataset, which quantifies the asymmetry of the distribution of data around its
mean.

- **Purpose:** Useful for analyzing the distribution shape for an entire population. A positive skewness value indicates
  a distribution with a tail on the right (longer right tail), while a negative skewness value indicates a tail on
  the left (longer left tail).

- **Formula:** `SKEW.P(array)`
  - `array`: The range or array of numerical data for the entire population to analyze.

- **Example Usage:**
  - `=SKEW.P(A1:A10)` calculates the skewness of the population data in range `A1:A10`.
  - `=SKEW.P({3, 7, 8, 1, 9})` computes the skewness of the population dataset `{3, 7, 8, 1, 9}`.
  - `=SKEW.P(B2:B20)` determines the skewness of the population numerical values in `B2:B20`.

### [SLOPE](./statistical-functions/slope.md)
Calculates the slope of the linear regression line through a given dataset.

- **Purpose:** Determines the rate of change in the dependent variable (`known_y's`) with respect to the independent
  variable (`known_x's`) in a linear regression model.

- **Formula:** `SLOPE(known_y's, known_x's)`
  - `known_y's`: The range or array of dependent variable data.
  - `known_x's`: The range or array of independent variable data.

- **Example Usage:**
  - `=SLOPE(A1:A10, B1:B10)` calculates the slope of the linear regression line for `A1:A10` (dependent variables) as a
    function of `B1:B10` (independent variables).
  - `=SLOPE({3, 4, 5}, {1, 2, 3})` computes the slope for the given arrays of dependent and independent data.
  - `=SLOPE(C1:C5, D1:D5)` evaluates the slope for the linear regression line for data in ranges `C1:C5` (dependent
    values) and `D1:D5` (independent values).

### [SMALL](./statistical-functions/small.md)
Returns the k-th smallest value in a dataset.

- **Purpose:** Useful for extracting the smallest values from a dataset, such as the minimum value or locating outliers.

- **Formula:** `SMALL(array, k)`
  - `array`: The range or array of numerical data from which to find the k-th smallest value.
  - `k`: The position (from the smallest) in the data to return. For instance, `k=1` returns the smallest value, `k=2`
    returns the second smallest value, and so on.

- **Example Usage:**
  - `=SMALL(A1:A10, 1)` returns the smallest value in the range `A1:A10`.
  - `=SMALL(A1:A10, 3)` returns the 3rd smallest value in the range `A1:A10`.
  - `=SMALL({5, 8, 4, 1, 9}, 2)` computes the 2nd smallest value (i.e., `4`) from the dataset `{5, 8, 4, 1, 9}`.

### [STANDARDIZE](./statistical-functions/standardize.md)
Returns a normalized value (z-score) from a dataset based on the mean and standard deviation.

- **Purpose:** Useful for standardizing data to allow for comparison across different datasets and scales.

- **Formula:** `STANDARDIZE(x, mean, standard_dev)`
  - `x`: The value to be standardized.
  - `mean`: The average (arithmetic mean) of the dataset.
  - `standard_dev`: The standard deviation of the dataset. Must be greater than 0.

- **Example Usage:**
  - `=STANDARDIZE(10, 5, 2)` standardizes the value `10` based on a mean of `5` and a standard deviation of `2`.
  - `=STANDARDIZE(A1, B1, B2)` calculates the z-score of the value in `A1` using the mean in `B1` and the standard
    deviation in `B2`.
  - `=STANDARDIZE(20, 15, 5)` returns the z-score for `20` with a mean of `15` and a standard deviation of `5`.

### [STDEV](./statistical-functions/st_dev.md)
Calculates the standard deviation of a dataset, suitable for both sample and population depending on the context.

- **Purpose:** Measures the dispersion or variability of a dataset relative to the mean. It indicates how spread out the
  values in the dataset are.

- **Formula:** `STDEV(array)`
  - `array`: The range or array of numerical data.

- **Example Usage:**
  - `=STDEV(A1:A10)` calculates the standard deviation for the data in the range `A1:A10` (interpreted as a sample by
    default).
  - `=STDEV({5, 12, 18, 7, 11})` computes the standard deviation for the dataset `{5, 12, 18, 7, 11}`.
  - `=STDEV(C1:C15)` determines the standard deviation for the data in the range `C1:C15`.

### [STDEV.P](./statistical-functions/st_dev__p.md)
Calculates the standard deviation for an entire population dataset.

- **Purpose:** Useful for understanding the variability or dispersion of a population. It measures how spread out the
  values in the population dataset are relative to the mean.

- **Formula:** `STDEV.P(array)`
  - `array`: The range or array of numerical data representing the entire population.

- **Example Usage:**
  - `=STDEV.P(A1:A10)` calculates the standard deviation of the population data in range `A1:A10`.
  - `=STDEV.P({4, 7, 11, 6, 8})` computes the population standard deviation of the values `{4, 7, 11, 6, 8}`.
  - `=STDEV.P(C1:C20)` determines the standard deviation for the data in range `C1:C20`, assuming it represents the
    entire population.

### [STDEV.S](./statistical-functions/st_dev__s.md)
Calculates the standard deviation for a sample dataset.

- **Purpose:** Useful for understanding the variability or dispersion of a sample. It measures how spread out the
  values in the sample dataset are relative to the mean.

- **Formula:** `STDEV.S(array)`
  - `array`: The range or array of numerical data representing the sample.

- **Example Usage:**
  - `=STDEV.S(A1:A10)` calculates the standard deviation of the sample data in range `A1:A10`.
  - `=STDEV.S({4, 7, 11, 6, 8})` computes the sample standard deviation of the values `{4, 7, 11, 6, 8}`.
  - `=STDEV.S(C1:C20)` determines the standard deviation for the data in range `C1:C20`, assuming it represents a
    sample.

### [STDEVA](./statistical-functions/st_dev_a.md)
Calculates the standard deviation of a dataset, considering text and logical values.

- **Purpose:** Useful for determining the variability of a dataset that includes numbers, text, and logical values. Text
  and logical values are handled as follows:
  - Text values are treated as `0`.
  - Logical values are interpreted as `TRUE = 1` and `FALSE = 0`.

- **Formula:** `STDEVA(array)`
  - `array`: The range or array of numerical, text, and logical data.

- **Example Usage:**
  - `=STDEVA(A1:A10)` calculates the standard deviation of the dataset in range `A1:A10`, treating text as `0` and
    logical values (`TRUE`, `FALSE`) as `1` and `0`.
  - `=STDEVA({4, TRUE, "text", 7})` computes the standard deviation of the dataset `{4, TRUE, "text", 7}` where `TRUE`
    is `1` and `"text"` is treated as `0`.
  - `=STDEVA(B1:B20)` calculates the standard deviation in the range `B1:B20`, considering both numerical and
    non-numerical (logical, text) values.

### [STDEVPA](./statistical-functions/st_dev_pa.md)
Calculates the standard deviation of an entire population, considering text and logical values.

- **Purpose:** Useful for determining the variability of a population dataset that includes numbers, text, and logical
  values. Text and logical values are handled as follows:
  - Text values are treated as `0`.
  - Logical values are interpreted as `TRUE = 1` and `FALSE = 0`.

- **Formula:** `STDEVPA(array)`
  - `array`: The range or array of numerical, text, and logical data representing the entire population.

- **Example Usage:**
  - `=STDEVPA(A1:A10)` calculates the population standard deviation of the dataset in range `A1:A10`, treating text as
    `0` and logical values (`TRUE`, `FALSE`) as `1` and `0`.
  - `=STDEVPA({4, TRUE, "text", 7})` computes the population standard deviation of the dataset `{4, TRUE, "text", 7}`
    where `TRUE` is `1` and `"text"` is treated as `0`.
  - `=STDEVPA(B1:B20)` calculates the population standard deviation in the range `B1:B20`, considering both numerical
    and non-numerical (logical, text) values.

### [STEYX](./statistical-functions/steyx.md)
Calculates the standard error of the predicted y-value for each x in a linear regression.

- **Purpose:** Useful for measuring the accuracy of the predictions made by a linear regression model. It quantifies the
  standard error of the predicted values (y) based on the regression line.

- **Formula:** `STEYX(known_y's, known_x's)`
  - `known_y's`: The range or array of dependent variable data.
  - `known_x's`: The range or array of independent variable data.

- **Example Usage:**
  - `=STEYX(A1:A10, B1:B10)` calculates the standard error of the predicted y-values for `A1:A10` (dependent variables)
    based on the independent variables in `B1:B10`.
  - `=STEYX({4, 5, 6}, {1, 2, 3})` computes the standard error for the given arrays of dependent (`{4, 5, 6}`) and
    independent (`{1, 2, 3}`) variables.
  - `=STEYX(C1:C5, D1:D5)` determines the standard error of the y-values for data in ranges `C1:C5` (dependent values)
    and `D1:D5` (independent values).

### [TDIST](./statistical-functions/t_dist.md)
Returns the probability of the t-distribution, often used in hypothesis testing.

- **Purpose:** Useful for determining the probability of observing a value in a t-distribution, given the degrees of
  freedom and type of test (one-tailed or two-tailed).

- **Formula:** `TDIST(x, degrees_freedom, tails)`
  - `x`: The calculated t-statistic value.
  - `degrees_freedom`: The number of degrees of freedom, usually derived from your dataset size.
  - `tails`: The number of tails for the distribution. Use `1` for a one-tailed test and `2` for a two-tailed test.

- **Example Usage:**
  - `=TDIST(2.5, 10, 1)` returns the one-tailed probability for a t-statistic value of `2.5` with `10` degrees of
    freedom.
  - `=TDIST(1.8, 15, 2)` computes the two-tailed probability for a t-statistic value of `1.8` with `15` degrees of
    freedom.
  - `=TDIST(A1, B1, 1)` determines the one-tailed probability using the t-statistic in `A1` and degrees of freedom in
    `B1`.

### [T.DIST](./statistical-functions/t__dist.md)
Returns the probability of the t-distribution based on the input t-statistic, degrees of freedom, and cumulative flag.

- **Purpose:** Useful for calculating the cumulative probability or the probability density function of the
  t-distribution, often applied in hypothesis testing and confidence interval analysis.

- **Formula:** `T.DIST(x, degrees_freedom, cumulative)`
  - `x`: The t-statistic value.
  - `degrees_freedom`: The number of degrees of freedom, which should be a positive number.
  - `cumulative`: A logical value (`TRUE` or `FALSE`). Use `TRUE` for the cumulative distribution function and `FALSE`
    for the probability density function.

- **Example Usage:**
  - `=T.DIST(1.5, 10, TRUE)` returns the cumulative probability for a t-statistic value of `1.5` with `10` degrees of
    freedom.
  - `=T.DIST(2.0, 20, FALSE)` computes the probability density function value for a t-statistic of `2.0` with `20`
    degrees of freedom.
  - `=T.DIST(A1, B1, TRUE)` calculates the cumulative probability using the t-statistic in `A1` and degrees of freedom
    in `B1`.

### [T.DIST.2T](./statistical-functions/t__dist__2t.md)
Returns the two-tailed probability of the t-distribution based on the input t-statistic and degrees of freedom.

- **Purpose:** Useful for hypothesis testing when working with two-tailed tests. This function helps calculate the
  probability of observing a t-statistic equal to or more extreme than the given value, in either tail of the
  distribution.

- **Formula:** `T.DIST.2T(x, degrees_freedom)`
  - `x`: The t-statistic value (must be non-negative).
  - `degrees_freedom`: The number of degrees of freedom, which should be a positive integer.

- **Example Usage:**
  - `=T.DIST.2T(2.5, 10)` returns the two-tailed probability for a t-statistic value of `2.5` with `10` degrees of
    freedom.
  - `=T.DIST.2T(1.8, 15)` computes the two-tailed probability for a t-statistic value of `1.8` with `15` degrees of
    freedom.
  - `=T.DIST.2T(A1, B1)` calculates the two-tailed probability using the t-statistic in `A1` and degrees of freedom in
    `B1`.

### [T.DIST.RT](./statistical-functions/t__dist__rt.md)
Returns the right-tailed probability of the t-distribution based on the input t-statistic and degrees of freedom.

- **Purpose:** Useful for calculating the probability of observing a t-statistic as extreme or more extreme in the right
  tail of the t-distribution. Commonly applied in one-tailed hypothesis testing.

- **Formula:** `T.DIST.RT(x, degrees_freedom)`
  - `x`: The t-statistic value (must be a positive number).
  - `degrees_freedom`: The number of degrees of freedom, which should be a positive integer.

- **Example Usage:**
  - `=T.DIST.RT(2.5, 10)` returns the right-tailed probability for a t-statistic value of `2.5` with `10` degrees of
    freedom.
  - `=T.DIST.RT(1.8, 15)` computes the right-tailed probability for a t-statistic value of `1.8` with `15` degrees of
    freedom.
  - `=T.DIST.RT(A1, B1)` calculates the right-tailed probability using the t-statistic in `A1` and degrees of freedom in
    `B1`.

### [TINV](./statistical-functions/t_inv.md)
Returns the t-value of the Student's t-distribution as a function of the probability and degrees of freedom.

- **Purpose:** Useful for hypothesis testing, this function calculates the critical t-value for a specified probability
  and degrees of freedom. Can be applied in confidence intervals and t-tests.

- **Formula:** `TINV(probability, degrees_freedom)`
  - `probability`: The probability associated with the Student's t-distribution (for a two-tailed test).
  - `degrees_freedom`: The number of degrees of freedom (a positive integer).

- **Example Usage:**
  - `=TINV(0.05, 10)` returns the t-value for a two-tailed probability of `0.05` with `10` degrees of freedom.
  - `=TINV(0.01, 20)` computes the t-value for a two-tailed probability of `0.01` with `20` degrees of freedom.
  - `=TINV(A1, B1)` calculates the t-value using the probability in `A1` and degrees of freedom in `B1`.

### [T.INV](./statistical-functions/t__inv.md)
Returns the left-tailed t-value of the Student's t-distribution as a function of the probability and degrees of freedom.

- **Purpose:** Useful for hypothesis testing, this function calculates the critical t-value for a left-tailed test,
  based on a specified probability and degrees of freedom.

- **Formula:** `T.INV(probability, degrees_freedom)`
  - `probability`: The probability associated with the Student's t-distribution for a left-tailed test (a decimal
    between `0` and `1`).
  - `degrees_freedom`: The number of degrees of freedom (a positive integer).

- **Example Usage:**
  - `=T.INV(0.05, 10)` returns the left-tailed t-value for a probability of `0.05` with `10` degrees of freedom.
  - `=T.INV(0.01, 20)` computes the left-tailed t-value for a probability of `0.01` with `20` degrees of freedom.
  - `=T.INV(A1, B1)` calculates the left-tailed t-value using the probability in `A1` and degrees of freedom in `B1`.

### [T.INV.2T](./statistical-functions/t__inv__2t.md)
Returns the two-tailed t-value of the Student's t-distribution as a function of the probability and degrees of freedom.

- **Purpose:** Useful for hypothesis testing and confidence interval calculations, this function provides the critical
  t-value for a two-tailed test, given a specified probability and degrees of freedom.

- **Formula:** `T.INV.2T(probability, degrees_freedom)`
  - `probability`: The probability associated with the two-tailed Student's t-distribution (a decimal between `0` and
    `1`).
  - `degrees_freedom`: The number of degrees of freedom (a positive integer).

- **Example Usage:**
  - `=T.INV.2T(0.05, 10)` returns the two-tailed t-value for a probability of `0.05` with `10` degrees of freedom.
  - `=T.INV.2T(0.01, 20)` computes the two-tailed t-value for a probability of `0.01` with `20` degrees of freedom.
  - `=T.INV.2T(A1, B1)` calculates the two-tailed t-value using the probability in `A1` and degrees of freedom in `B1`.

### [TTEST](./statistical-functions/t_test.md)
Returns the probability associated with a Student's t-test. This function can be used to determine whether two samples
are likely to have come from the same two underlying populations that have the same mean.

- **Purpose:** Useful for hypothesis testing to determine if there is a significant difference between two datasets.

- **Formula:** `TTEST(array1, array2, tails, type)`
  - `array1`: The first data set, which should be a range of numerical values.
  - `array2`: The second data set, which should be a range of numerical values.
  - `tails`: Specifies the number of distribution tails. Use `1` for a one-tailed distribution, and `2` for a two-tailed
    distribution.
  - `type`: Specifies the type of t-test to perform:
    - `1`: Paired t-test
    - `2`: Two-sample equal variance (homoscedastic)
    - `3`: Two-sample unequal variance (heteroscedastic)

- **Example Usage:**
  - `=TTEST(A1:A10, B1:B10, 2, 1)` performs a two-tailed paired t-test on the data in ranges `A1:A10` and `B1:B10`.
  - `=TTEST(A1:A10, B1:B10, 1, 2)` performs a one-tailed test assuming equal variance between the two data sets.
  - `=TTEST(C1:C15, D1:D15, 2, 3)` performs a two-tailed test assuming unequal variance between the datasets.

### [TREND](./statistical-functions/trend.md)
Returns values along a linear trend based on the given data points. This function can be used for trend extrapolation
and interpolation.

- **Purpose:** Useful for predicting future values along a linear trend by fitting a straight line to the given data
  points.

- **Formula:** `TREND(known_ys, [known_xs], [new_xs], [const])`
  - `known_ys`: The dependent data (y-values) that correspond to the observed data points. It must be an array or range
    of numeric values.
  - `known_xs`: *(Optional)* The independent data points (x-values) for the known y-values. If omitted, it is assumed to
    be a sequence `{1, 2, 3, ...}`.
  - `new_xs`: *(Optional)* New x-values for which the function calculates y-values on the fitted trend line. If omitted,
    the function returns y-values corresponding to `known_xs`.
  - `const`: *(Optional)* A logical value specifying whether to force the constant `b` in the linear equation
    `y = mx + b` to 0.
    - `TRUE` (default): Fits the intercept `b` as a free parameter.
    - `FALSE`: Forces `b = 0`.

- **Example Usage:**
  - `=TREND({2, 4, 6}, {1, 2, 3})` computes y-values for the linear trend based on the provided `known_xs` `{1, 2, 3}`
    and `known_ys` `{2, 4, 6}`.
  - `=TREND({2, 4, 6}, {1, 2, 3}, {4, 5})` extrapolates y-values for the given `new_xs` `{4, 5}` based on the trend from
    the known `x` and `y`.
  - `=TREND(A1:A10, B1:B10, C1:C5, FALSE)` predicts y-values for `new_xs` in `C1:C5` while forcing `b = 0`.

### [TRIMMEAN](./statistical-functions/trim_mean.md)
Returns the mean (average) of a data set, excluding a percentage of data points from the extremes (both top and bottom)
of the dataset.

- **Purpose:** Useful for reducing the effect of extreme values (outliers) on the mean calculation of a data set.

- **Formula:** `TRIMMEAN(array, percent)`
  - `array`: The data set to be operated on, which should be a range of numerical values.
  - `percent`: The percentage (between `0` and `1`) of data points to exclude from the calculation. The function removes
    points evenly from the top and bottom of the data set.

- **Example Usage:**
  - `=TRIMMEAN(A1:A10, 0.1)` calculates the mean of the data in range `A1:A10`, excluding 10% of data points (5% from
    each end).
  - `=TRIMMEAN(B1:B20, 0.2)` computes the trimmed mean of the data in range `B1:B20`, excluding 20% of the data points.
  - `=TRIMMEAN(C1:C15, D1)` calculates the trimmed mean using the data range `C1:C15`, with the percentage to trim
    specified in cell `D1`.

## V

### [VAR](./statistical-functions/var.md)
Calculates the variance of a sample dataset (taking into account sample bias). This function is used when analyzing a
sample rather than the entire population.

- **Purpose:** Useful for statistical analysis to measure how far individual data points are from the mean, for a sample
  dataset.

- **Formula:** `VAR(array)`
  - `array`: The data set to be analyzed, which should be a range of numerical values.

- **Example Usage:**
  - `=VAR(A1:A10)` calculates the variance of the sample represented by the values in range `A1:A10`.
 
### [VARP](./statistical-functions/var_p.md)
Calculates the variance of a population based on the entire dataset (ignoring sample bias). This function is used when
you want to determine the variance of all values in the dataset, not just a sample.

- **Purpose:** Useful for statistical analysis to measure how far individual data points are from the mean, for an
  entire population.

- **Formula:** `VARP(array)`
  - `array`: The data set to be analyzed, which should be a range of numerical values.

- **Example Usage:**
  - `=VARP(A1:A10)` calculates the variance of the population represented by the values in range `A1:A10`.
  - `=VARP(B1:B15)` computes the variance using the population data in range `B1:B15`.
  - `=VARP(C1:C20)` determines the population variance based on the numerical data in range `C1:C20`.

### [VAR.P](./statistical-functions/var__p.md)
Calculates the variance of a population based on the entire dataset (ignoring sample bias). This function is used when
you want to determine the variance of all values in the dataset, not just a sample.

- **Purpose:** Useful for statistical analysis to measure how far individual data points are from the mean, for an
  entire population.

- **Formula:** `VAR.P(array)`
  - `array`: The data set to be analyzed, which should be a range of numerical values.

- **Example Usage:**
  - `=VAR.P(A1:A10)` calculates the variance of the population represented by the values in range `A1:A10`.
  - `=VAR.P(B1:B15)` computes the variance using the population data in range `B1:B15`.
  - `=VAR.P(C1:C20)` determines the population variance based on the numerical data in range `C1:C20`.

### [VAR.S](./statistical-functions/var__s.md)
Calculates the variance of a sample dataset (taking into account sample bias). This function is used when analyzing a
sample rather than the entire population.

- **Purpose:** Useful for statistical analysis to measure how far individual data points are from the mean, for a sample
  dataset.

- **Formula:** `VAR.S(array)`
  - `array`: The data set to be analyzed, which should be a range of numerical values.

- **Example Usage:**
  - `=VAR.S(A1:A10)` calculates the variance of the sample represented by the values in range `A1:A10`.
  - `=VAR.S(B1:B15)` computes the variance using the sample data in range `B1:B15`.
  - `=VAR.S(C1:C20)` determines the sample variance based on the numerical data in range `C1:C20`.

### [VARA](./statistical-functions/var_a.md)
Calculates the variance of a sample, evaluating both numeric and non-numeric data. Unlike `VAR.S`, this function
includes logical values and text in its calculations, treating `TRUE` as `1`, `FALSE` as `0`, and text as `0`.

- **Purpose:** Useful for measuring how spread out sample data is around its mean in datasets that include text or
  logical values.

- **Formula:** `VARA(value1, [value2], …)`
  - `value1`: Required. The first value, cell reference, or range to evaluate.
  - `value2, …`: Optional. Additional values, cell references, or ranges (up to 254 arguments).

- **Example Usage:**
  - `=VARA(A1:A10)` calculates the sample variance of the dataset in range `A1:A10`, treating text as `0` and logicals
    (`TRUE` as `1`, `FALSE` as `0`).
  - `=VARA(B1:B15)` computes the sample variance of the dataset in range `B1:B15`, accounting for text and logical
    values appropriately.
  - `=VARA(C1:C20)` determines the sample variance of the dataset in range `C1:C20`, considering text and logical
    values.

### [VARPA](./statistical-functions/var_pa.md)
Calculates the variance of a dataset, treating text and logical values differently. Text values are treated as `0`, and
logical values `TRUE` and `FALSE` are treated as `1` and `0`, respectively. This function is used when you need to
consider text and logical values explicitly in the variance calculation.

- **Purpose:** Useful for measuring how far individual data points are from the mean in datasets that include text or
  logical values, while accounting for them in the calculation.

- **Formula:** `VARPA(array)`
  - `array`: The data set to be analyzed. It can include numeric values, text, and logical values.

- **Example Usage:**
  - `=VARPA(A1:A10)` calculates the variance of the dataset in range `A1:A10`, treating text as `0` and logical values (
    `TRUE` as `1`, `FALSE` as `0`).
  - `=VARPA(B1:B15)` computes the variance of the dataset in range `B1:B15`, accounting for text and logical values
    appropriately.
  - `=VARPA(C1:C20)` determines the variance of the dataset located in range `C1:C20`, considering text and logical
    values.

## W

### [WEIBULL](./statistical-functions/weibull.md)
Computes the Weibull distribution, often used in reliability analysis, failure analysis, and life data modeling.

- **Purpose:** Evaluates the probability density function (PDF) or cumulative distribution function (CDF) of the Weibull
  distribution.

- **Formula:** `WEIBULL(x, alpha, beta, cumulative)`
  - `x`: The value at which to evaluate the function (must be `≥ 0`).
  - `alpha`: The scale parameter of the Weibull distribution (must be `> 0`).
  - `beta`: The shape parameter of the Weibull distribution (must be `> 0`).
  - `cumulative`: A logical value:
    - `TRUE`: Returns the cumulative distribution function (CDF).
    - `FALSE`: Returns the probability density function (PDF).

- **Example Usage:**
  - `=WEIBULL(3, 1.5, 2, TRUE)` computes the cumulative Weibull distribution where `alpha = 1.5` and `beta = 2` at
    `x = 3`.
  - `=WEIBULL(2, 2.5, 1.2, FALSE)` calculates the probability density value of the Weibull distribution with
    `alpha = 2.5` and `beta = 1.2` at `x = 2`.
  - `=WEIBULL(A1, B1, C1, TRUE)` evaluates the cumulative Weibull distribution dynamically using values from cells `A1`,
    `B1`, and `C1`.

### [WEIBULL.DIST](./statistical-functions/weibull__dist.md)
Calculates the Weibull distribution, which is commonly used in reliability analysis and life data analysis.

- **Purpose:** Evaluate the probability density or cumulative distribution function of the Weibull distribution for a
  dataset.

- **Formula:** `WEIBULL.DIST(x, alpha, beta, cumulative)`
  - `x`: The value at which to evaluate the function (must be `≥ 0`).
  - `alpha`: The scale parameter of the distribution (must be `> 0`).
  - `beta`: The shape parameter of the distribution (must be `> 0`).
  - `cumulative`: A logical value:
    - `TRUE`: Returns the cumulative distribution function.
    - `FALSE`: Returns the probability density function.

- **Example Usage:**
  - `=WEIBULL.DIST(1, 2, 1.5, TRUE)` calculates the cumulative Weibull distribution with `alpha = 2` and `beta = 1.5` at
    `x = 1`.
  - `=WEIBULL.DIST(2, 1, 0.5, FALSE)` computes the probability density Weibull distribution with `alpha = 1` and
    `beta = 0.5` at `x = 2`.
  - `=WEIBULL.DIST(A1, B1, C1, D1)` evaluates the Weibull distribution dynamically using values in cells `A1`, `B1`,
    `C1`, and `D1`.

### [ZTEST](./statistical-functions/z_test.md)
Performs a one-sample *z-test* that returns the probability a sample mean is different from a population mean for a
given dataset and known population standard deviation.

- **Purpose:** Useful for hypothesis testing to determine if the mean of a sample significantly differs from the
  population mean.

- **Formula:** `ZTEST(array, x, [sigma])`
  - `array`: The data set used in the test, which should be a range of numerical values.
  - `x`: The hypothesized population mean to test against.
  - `sigma` (optional): The known population standard deviation. If omitted, the function uses the sample standard
    deviation.

- **Example Usage:**
  - `=ZTEST(A1:A10, 5)` returns the one-tailed probability value for the dataset in range `A1:A10`, testing against a
    hypothesized population mean of `5`.
  - `=ZTEST(B1:B20, 10, 2)` calculates the z-test probability for the data in range `B1:B20`, assuming a population
    standard deviation of `2`.
  - `=ZTEST(C1:C15, D1)` dynamically computes the z-test probability with hypothesized mean from cell `D1` and uses the
    dataset in range `C1:C15`.

### [Z.TEST](./statistical-functions/z__test.md)
Calculates the *Z-test* probability value for a dataset, comparing a sample mean to a population mean, optionally
considering population standard deviation.

- **Purpose:** Useful for statistical hypothesis testing to determine whether a sample mean significantly differs from a
  known or hypothesized population mean.

- **Formula:** `Z.TEST(array, x, [sigma])`
  - `array`: The dataset used for the Z-test; it should be a range of numerical values.
  - `x`: The hypothesized population mean you want to test against.
  - `sigma` (optional): The known population standard deviation. If this is omitted, the formula will use the sample's
    standard deviation.

- **Example Usage:**
  - `=Z.TEST(A1:A10, 5)` calculates the probability value for the dataset in range `A1:A10` compared to the population
    mean of `5`, assuming the population standard deviation is not provided.
  - `=Z.TEST(B1:B20, 10, 2)` computes the Z-test probability for the dataset in range `B1:B20` using a hypothesized
    population mean of `10` and a population standard deviation of `2`.
  - `=Z.TEST(C1:C15, D1)` dynamically evaluates the Z-test value using the dataset in range `C1:C15` and the
    hypothesized mean specified in cell `D1`.