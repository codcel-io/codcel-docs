<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Functions — Alphabetical List

Below is an alphabetical list of all Excel functions documented in this user guide. Each function links to its dedicated page and includes a brief description.

- [ABS](mathematical-functions/abs.md)
  Returns the absolute value of a number. Useful for distance, magnitude, and removing sign without changing magnitude.

- [ACCRINT](financial-functions/accr_int.md)
  Calculates accrued interest for a security that pays periodic interest between issue and settlement dates. Supports day-count bases and an option for including the first period.

- [ACCRINTM](financial-functions/accr_intm.md)
  Calculates interest accrued at maturity for a security from issue to maturity. Supports multiple day-count conventions.

- [ACOS](mathematical-functions/acos.md)
  Returns the arccosine (inverse cosine) of a number in radians. Input must be between −1 and 1.

- [ACOSH](mathematical-functions/acosh.md)
  Returns the inverse hyperbolic cosine of a number (number ≥ 1). Useful in engineering and math contexts.

- [ACOT](mathematical-functions/acot.md)
  Returns the arccotangent of a number in radians (inverse of cotangent). Handles all real inputs.

- [ACOTH](mathematical-functions/acoth.md)
  Returns the inverse hyperbolic cotangent of a number where |number| > 1.

- [ADD](mathematical-functions/add.md)
  In Excel, the `+` symbol is used as an arithmetic operator to add numbers together.

- [ADDRESS](lookup-and-reference-functions/address.md)
  Creates a cell address as a text string from a row and column number. Supports absolute, relative, and mixed references in A1-style or R1C1-style notation, with optional sheet name qualification.

- [AGGREGATE](mathematical-functions/aggregate.md)
  Applies an aggregate like SUM, AVERAGE, COUNT, etc., with options to ignore errors, hidden rows, and nested subtotals.

- [AMORDEGRC](financial-functions/amor_degrc.md)
  Returns depreciation for each accounting period using the French accelerated method with coefficients based on asset life. Useful for financial and tax accounting.

- [AMORLINC](financial-functions/amor_linc.md)
  Returns depreciation for each accounting period using the straight-line method, prorated for partial periods. Useful for fixed‑asset accounting.

- [AND](logical-functions/and.md)
  Returns TRUE if all the arguments evaluate to TRUE; otherwise returns FALSE. Often used with IF to build compound logical tests.

- [ARABIC](mathematical-functions/arabic.md)
  Converts a Roman numeral text string to its Arabic numeral equivalent.

- [AREAS](lookup-and-reference-functions/areas.md)
  Returns the number of areas (distinct contiguous ranges) in a reference. Useful for validating multi-area references and building dynamic formulas.

- [ARRAYTOTEXT](text-functions/array_to_text.md)
  The `ARRAYTOTEXT` function in Excel converts an array (or range) of values into a text string.

- [ASC](text-functions/asc.md)
  The `ASC` function in Excel is used to convert full-width (double-byte) characters in a text string to half-width ( single-byte) characters.

- [ASIN](mathematical-functions/asin.md)
  Returns the arcsine (inverse sine) of a number in radians. Input must be between −1 and 1.

- [ASINH](mathematical-functions/asinh.md)
  Returns the inverse hyperbolic sine of a number.

- [ATAN](mathematical-functions/atan.md)
  Returns the arctangent (inverse tangent) of a number in radians.

- [ATAN2](mathematical-functions/atan2.md)
  Returns the arctangent of the quotient of its arguments, using the signs to determine the correct quadrant.

- [ATANH](mathematical-functions/atanh.md)
  Returns the inverse hyperbolic tangent of a number (−1 < number < 1).

- [AVEDEV](statistical-functions/ave_dev.md)
  Calculates the average of the absolute deviations of data points from their mean. Useful for measuring dispersion without regard to direction.

- [AVERAGE](mathematical-functions/average.md)
  Returns the arithmetic mean of numbers, ranges, or references.

- [AVERAGEA](statistical-functions/average_a.md)
  Calculates the average treating TRUE as 1, FALSE as 0, and text as 0. Helpful when averaging data that includes logical or text values.

- [AVERAGEIF](conditional-functions/average_if.md)
  Calculates the average of cells that meet a specified condition. Optionally averages a separate range when a matching criteria range is provided.

- [AVERAGEIFS](statistical-functions/average_ifs.md)
  Calculates the average for cells specified by multiple criteria across ranges. Useful for multi-condition averaging.

- [BAHTTEXT](text-functions/bahttext.md)
  Converts a number to Thai text and adds the suffix "Baht". Used to express numeric currency values in written Thai for financial documents.

- [BASE](mathematical-functions/base.md)
  Converts a number to text in a specified base (2–36), such as binary or hexadecimal.

- [BESSELI](engineering-functions/bessel_i.md)
  Returns the modified Bessel function of the first kind In(x) for a given value x and order n. Common in engineering and physics for problems with cylindrical symmetry.

- [BESSELJ](engineering-functions/bessel_j.md)
  Returns the Bessel function of the first kind Jn(x) for a given value x and order n. Useful in modeling wave propagation, vibrations, and heat conduction.

- [BESSELK](engineering-functions/bessel_k.md)
  Returns the modified Bessel function of the second kind Kn(x) for a given value x and order n. Used in engineering and applied mathematics for certain differential equations.

- [BESSELY](engineering-functions/bessel_y.md)
  Returns the Bessel function of the second kind Yn(x) for a given value x and order n. Often used in physics and engineering analyses with cylindrical or spherical coordinates.

- [BETA.DIST](mathematical-functions/beta_dist.md)
  Returns the beta distribution (PDF or CDF). Useful in statistics for modeling probabilities.

- [BETA.INV](statistical-functions/beta__inv.md)
  The `BETA.INV` function in Excel calculates the **inverse of the cumulative beta probability density function** for a given probability.

- [BETADIST](mathematical-functions/betadist.md)
  Returns the beta cumulative distribution (compatibility). Superseded by BETA.DIST.

- [BETAINV](statistical-functions/beta_inv.md)
  Returns the inverse of the beta cumulative distribution for a given probability and parameters, optionally bounded between A and B.

- [BIN2DEC](engineering-functions/bin_2_dec.md)
  Converts a binary number to its decimal equivalent. Supports two's complement interpretation for 10-bit negative numbers.

- [BIN2HEX](engineering-functions/bin_2_hex.md)
  Converts a binary number to hexadecimal. Supports two's complement interpretation for up to 10-bit inputs and optional padding.

- [BIN2OCT](engineering-functions/bin_2_oct.md)
  Converts a binary number to octal. Supports two's complement interpretation for up to 10-bit inputs and optional padding.

- [BINOM.DIST](statistical-functions/binom__dist.md)
  Returns the binomial distribution for the number of successes in trials, as either probability mass or cumulative probability.

- [BINOM.DIST.RANGE](statistical-functions/binom__dist__range.md)
  Returns the probability of a number of successes falling within a range for a binomial distribution.

- [BINOMDIST](statistical-functions/binom_dist.md)
  Calculates the individual term binomial probability for a specified number of successes in a series of independent trials.

- [BINOMINV](statistical-functions/binom_inv.md)
  Returns the smallest value for which the cumulative binomial distribution is greater than or equal to a criterion probability.

- [BITAND](engineering-functions/bit_and.md)
  Performs a bitwise AND operation on two non‑negative integers. Returns a decimal number whose bits are 1 only where both inputs have 1s.

- [BITLSHIFT](engineering-functions/bit_l_shift.md)
  Shifts a number's bits left by a specified number of positions. Equivalent to multiplying by 2^shift for non‑negative integers.

- [BITOR](engineering-functions/bit_or.md)
  Performs a bitwise OR operation on two non‑negative integers. Returns a decimal number with 1s where either input has a 1.

- [BITRSHIFT](engineering-functions/bit_r_shift.md)
  Shifts a number's bits right by a specified number of positions. Equivalent to truncating division by powers of two for non‑negative integers.

- [BITXOR](engineering-functions/bit_xor.md)
  Performs a bitwise exclusive OR (XOR) on two non‑negative integers. Bits are 1 where inputs differ.

- [BYCOL](logical-functions/bycol.md)
  Applies a LAMBDA function to each column in an array, returning a single-row array of results. Useful for column-wise aggregations like sums, averages, or custom calculations.

- [BYROW](logical-functions/byrow.md)
  Applies a LAMBDA function to each row in an array, returning a single-column array of results. Useful for row-wise aggregations like sums, averages, or custom calculations.

- [CEILING](mathematical-functions/ceiling.md)
  Rounds a number up to a specified multiple of significance. Consistent for positive values; see CEILING.MATH for extended behavior.

- [CEILING.MATH](mathematical-functions/ceiling_math.md)
  Rounds up to the nearest integer or specified multiple, with options for handling negative numbers.

- [CEILING.PRECISE](mathematical-functions/ceiling_precise.md)
  Rounds up to the nearest integer or specified multiple regardless of sign. Always rounds toward zero for negatives.

- [CELL](information-functions/cell.md)
  Returns information about the formatting, location, or contents of a cell. Accepts an info_type string and an optional cell reference.

- [CHAR](text-functions/char.md)
  The `CHAR` function in Excel returns the character associated with the specified ASCII code.

- [CHIDIST](compatibility-functions/chi_dist.md)
  Returns the right-tailed probability of the chi-squared distribution. Commonly used in goodness-of-fit and independence tests.

- [CHIINV](compatibility-functions/chi_inv.md)
  Returns the inverse of the right-tailed probability of the chi-squared distribution. Use it to obtain critical chi-squared values for a given probability and degrees of freedom.

- [CHISQ.DIST](statistical-functions/chisq_dist.md)
  Returns the chi-squared distribution (PDF or CDF) for a value and degrees of freedom. Used in hypothesis testing and goodness-of-fit analyses.

- [CHISQ.DIST.RT](statistical-functions/chisq_dist_rt.md)
  Returns the right-tailed probability of the chi-squared distribution. Commonly used for hypothesis tests.

- [CHISQ.INV](statistical-functions/chisq_inv.md)
  Returns the inverse of the left‑tailed probability of the chi-squared distribution for a given probability and degrees of freedom.

- [CHISQ.INV.RT](statistical-functions/chisq_inv_rt.md)
  Returns the inverse of the right‑tailed probability of the chi-squared distribution.

- [CHISQ.TEST](statistical-functions/chisq_test.md)
  Performs the chi-squared test for independence between two categorical datasets.

- [CHITEST](compatibility-functions/chi_test.md)
  Returns the p-value associated with the chi-squared test comparing observed and expected frequencies. Often used for goodness-of-fit and tests of independence in contingency tables.

- [CHOOSE](lookup-and-reference-functions/choose.md)
  Returns a value or reference from a list based on an index number. Useful for dynamically selecting values or ranges in formulas.

- [CHOOSECOLS](lookup-and-reference-functions/choosecols.md)
  Returns specified columns from an array or range by index. Supports positive indices from left, negative from right, and column reordering.

- [CHOOSEROWS](lookup-and-reference-functions/chooserows.md)
  Returns specified rows from an array or range by index. Supports positive indices from top, negative from bottom, and row reordering.

- [COLUMN](lookup-and-reference-functions/column.md)
  Returns the column number of a cell reference. If no reference is provided, returns the column number of the cell containing the formula.

- [COLUMNS](lookup-and-reference-functions/columns.md)
  Returns the number of columns in a reference or array. Useful for dynamic formulas and determining array dimensions.

- [CLEAN](text-functions/clean.md)
  The `CLEAN` function in Excel is used to remove all non-printable characters from a given text string.

- [CODE](text-functions/code.md)
  The `CODE` function in Excel returns the numeric code corresponding to the first character of the text string it is given.

- [COMBIN](mathematical-functions/combin.md)
  Returns the number of combinations for a given number of items. Order does not matter.

- [COMBINA](mathematical-functions/combina.md)
  Returns combinations with repetitions allowed. Useful when items can repeat in selections.

- [COMPLEX](engineering-functions/complex.md)
  Creates a complex number from real and imaginary coefficients in the form a+bi or a+bj. Useful for calculations that operate on complex numbers.

- [CONCAT](text-functions/concat.md)
  Introduced in Excel 2016, the `CONCAT` function is used to join multiple text strings into one single string.

- [CONCATENATE](text-functions/concatenate.md)
  The `CONCATENATE` function in Excel is used to join two or more text strings into one single string.

- [CONFIDENCE](compatibility-functions/confidence.md)
  Returns the confidence interval margin of error for a population mean using the normal distribution. Helps construct a mean estimate at a specified significance level.

- [CONFIDENCE.NORM](statistical-functions/confidence_norm.md)
  Calculates the confidence interval for a population mean using a normal distribution, given alpha, standard deviation, and sample size.

- [CONFIDENCE.T](statistical-functions/confidence_t.md)
  The `CONFIDENCE.T` function in Excel calculates the **confidence interval** for a population mean when using a * *t-distribution**.

- [CONVERT](mathematical-functions/convert.md)
  Converts a number from one measurement system to another (e.g., lbm to kg).

- [CORREL](statistical-functions/correl.md)
  Returns the Pearson correlation coefficient between two data sets, indicating the strength and direction of linear relationship.

- [COS](mathematical-functions/cos.md)
  Returns the cosine of an angle given in radians.

- [COSH](mathematical-functions/cosh.md)
  The `COSH` function in Excel returns the hyperbolic cosine of a number.

- [COT](mathematical-functions/cot.md)
  Returns the cotangent of an angle (1/TAN) in radians.

- [COTH](mathematical-functions/coth.md)
  Returns the hyperbolic cotangent of a number.

- [COUNT](statistical-functions/count.md)
  Counts the number of numeric values in a supplied range or array.

- [COUNTA](statistical-functions/counta.md)
  Counts the number of non-empty cells in a range, including cells containing text, numbers, logical values, and errors.

- [COUNTBLANK](statistical-functions/count_blank.md)
  Counts the number of empty (blank) cells in a specified range. Useful for identifying missing data or gaps in a dataset.

- [COUNTIF](conditional-functions/count_if.md)
  Counts the number of cells in a range that meet a single specified criterion. Supports numbers, text, expressions, and wildcards for pattern matching.

- [COUNTIFS](statistical-functions/count_ifs.md)
  The `COUNTIFS` function in Excel is used to count the number of cells that meet multiple criteria across one or more ranges.

- [COUPDAYBS](financial-functions/coup_day_bs.md)
  Returns the number of days from the beginning of the coupon period to the settlement date for a coupon-paying security. Supports various day-count bases.

- [COUPDAYS](financial-functions/coup_days.md)
  Returns the number of days in the coupon period containing the settlement date. Useful for accrued interest and bond timing calculations.

- [COUPDAYSNC](financial-functions/coup_days_nc.md)
  Returns the number of days from the settlement date to the next coupon date. Helps measure time remaining until the next interest payment.

- [COUPNCD](financial-functions/coup_ncd.md)
  Returns the next coupon date after the settlement date for a coupon-paying security. Uses the specified payment frequency and day-count basis.

- [COUPNUM](financial-functions/coup_num.md)
  Returns the number of coupons payable between the settlement and maturity dates. Useful for pricing and yield calculations.

- [COUPPCD](financial-functions/coup_pcd.md)
  Returns the previous coupon date before the settlement date. Assists in determining the current coupon period.

- [COVAR](compatibility-functions/covar.md)
  Returns the covariance of two data sets, indicating how two variables change together. Available for compatibility; newer functions provide improved accuracy.

- [COVARIANCE.P](statistical-functions/covariance_p.md)
  Returns the population covariance between two data sets.

- [COVARIANCE.S](statistical-functions/covariance_s.md)
  Returns the sample covariance between two data sets.

- [CRITBINOM](compatibility-functions/crit_binom.md)
  Returns the smallest value for which the cumulative binomial distribution is greater than or equal to a criterion value. Useful for inverse binomial calculations.

- [CSC](mathematical-functions/csc.md)
  Returns the cosecant of an angle (1/SIN) in radians.

- [CSCH](mathematical-functions/csch.md)
  Returns the hyperbolic cosecant of a number.

- [CUMIPMT](financial-functions/cum_i_pmt.md)
  Returns the cumulative interest paid on a loan over a range of payment periods. Useful for assessing total interest costs across specified payments.

- [CUMPRINC](financial-functions/cum_princ.md)
  Returns the cumulative principal paid on a loan over a range of payment periods. Helps analyze how much of the balance has been reduced.

- [DATE](date-time-functions/date.md)
  Creates a date from year, month, and day numbers. Useful for constructing valid Excel dates from parts.

- [DATEDIF](date-time-functions/date_dif.md)
  Calculates the difference between two dates in specified units (years, months, or days). Useful for age or tenure calculations.

- [DATEVALUE](date-time-functions/date-value.md)
  Converts a date in text format to a serial number representing a date. Helps turn text dates into proper dates.

- [DAY](date-time-functions/day.md)
  Returns the day of the month from a date (1–31).

- [DAYS](date-time-functions/days.md)
  Returns the number of days between two dates.

- [DAYS360](date-time-functions/days-360.md)
  Calculates days between two dates based on a 360-day year. Often used in financial calculations.

- [DB](financial-functions/db.md)
  Returns the depreciation of an asset for a specified period using the fixed-declining balance method. Useful for accelerated depreciation schedules.

- [DBCS](text-functions/dbcs.md)
  Converts half-width (single-byte) characters in a text string to full-width (double-byte) characters. Inverse of the `ASC` function, used for East Asian language text processing.

- [DDB](financial-functions/ddb.md)
  Returns the depreciation of an asset for a specified period using the double-declining balance method or a custom factor. Models faster early-life depreciation.

- [DEC2BIN](engineering-functions/dec_2_bin.md)
  Converts a decimal number to binary with optional padding. Negative numbers are represented using two's complement up to 10 bits.

- [DEC2HEX](engineering-functions/dec_2_hex.md)
  Converts a decimal number to hexadecimal with optional padding. Negative numbers use two's complement representation up to 10 bits.

- [DEC2OCT](engineering-functions/dec_2_oct.md)
  Converts a decimal number to octal with optional padding. Negative numbers use two's complement representation up to 10 bits.

- [DECIMAL](mathematical-functions/decimal.md)
  Converts a text representation of a number in a given base into a decimal number.

- [DEGREES](mathematical-functions/degrees.md)
  Converts radians to degrees.

- [DELTA](engineering-functions/delta.md)
  Tests whether two numbers are equal (Kronecker delta). Returns 1 if equal, 0 otherwise; useful for filtering or comparisons.

- [DEVSQ](statistical-functions/devsq.md)
  The `DEVSQ` function in Excel calculates the **sum of the squared deviations** of data points from their sample mean.

- [DISC](financial-functions/disc.md)
  Returns the discount rate of a security, given settlement and maturity dates, price, and redemption value. Useful for discount yield calculations.

- [DIVIDE](mathematical-functions/divide.md)
  In Excel, the `/` symbol is used as an arithmetic operator to divide one number by another.

- [DROP](information-functions/drop.md)
  Excludes a specified number of rows or columns from the beginning or end of an array. Positive values drop from the start; negative values drop from the end.

- [DOLLAR](text-functions/dollar.md)
  The `DOLLAR` function in Excel is used to convert a number to text in a currency format, using the formatting style "$ #,##0.00".

- [DOLLARDE](financial-functions/dollar_de.md)
  Converts a dollar price expressed as a fraction to a decimal. Helpful for converting securities prices quoted in fractional form.

- [DOLLARFR](financial-functions/dollar_fr.md)
  Converts a dollar price expressed as a decimal to a fraction. Useful for formatting and converting bond prices to fractional notation.

- [DURATION](financial-functions/duration.md)
  Returns the Macauley duration of a security with periodic interest payments. Measures sensitivity of price to interest rate changes.

- [EDATE](date-time-functions/e-date.md)
  Returns a date a specified number of months before or after a start date.

- [EFFECT](financial-functions/effect.md)
  Returns the effective annual interest rate given a nominal rate and compounding periods per year. Converts nominal rates to effective rates for comparisons.

- [EOMONTH](date-time-functions/eo-month.md)
  Returns the last day of the month a given number of months before or after a start date.

- [ERF](engineering-functions/erf.md)
  Returns the error function ERF integrated between limits; with one argument integrates from 0 to x. Used in statistics, probability, and engineering.

- [ERF.PRECISE](engineering-functions/erf_precise.md)
  Returns the error function ERF from 0 to x with improved precision. Useful for accurate probability and error analyses.

- [ERFC](engineering-functions/erfc.md)
  Returns the complementary error function, 1 − ERF(x). Common in statistics and signal processing.

- [ERFC.PRECISE](engineering-functions/erfc_precise.md)
  Returns the complementary error function with improved precision. Useful for high‑accuracy probability and error calculations.

- [EVEN](mathematical-functions/even.md)
  Rounds a number up to the nearest even integer.

- [EXACT](text-functions/exact.md)
  The `EXACT` function in Excel is used to compare two text strings to determine if they are exactly the same.

- [EXP](mathematical-functions/exp.md)
  Returns e raised to a given power. Useful for continuous growth and natural exponentials.

- [EXPON.DIST](statistical-functions/expon_dist.md)
  The `EXPONDIST` (or `EXP.DIST` in newer versions of Excel) function calculates values for the **exponential distribution **, which is a continuous probability distribution used to model the time between events in a Poisson process.

- [EXPONDIST](compatibility-functions/expon_dist.md)
  Returns the exponential distribution, modeling the time between events. Can return the probability density or cumulative distribution.

- [EXPONENTIATION](mathematical-functions/exponentiation.md)
  In Excel, the `^` symbol is used as an arithmetic operator for exponentiation, allowing one number to be raised to the power of another.

- [EXPAND](lookup-and-reference-functions/expand.md)
  Expands an array to specified dimensions by adding rows and/or columns, filling new positions with a customizable pad value (or #N/A by default).

- [F.DIST](statistical-functions/f_dist.md)
  The `FDIST` (or `F.DIST` in newer versions of Excel) function calculates values for the **F-distribution**, which is a continuous probability distribution.

- [F.DIST.RT](statistical-functions/f_dist_rt.md)
  The `F.DIST.RT` function in Excel calculates the **right-tailed F-distribution**, which is used to determine the probability that the observed F-statistic value (or a more extreme value) would occur under the null hypothesis.

- [F.INV](statistical-functions/f_inv.md)
  The `F.INV` function in Excel calculates the **inverse of the F-distribution**.

- [F.INV.RT](statistical-functions/f_inv_rt.md)
  The `F.INV.RT` function in Excel calculates the **inverse of the (right-tailed) F-distribution**.

- [F.TEST](statistical-functions/f_test.md)
  The `F.TEST` function in Excel calculates the **two-tailed probability** that the variances between two data sets are significantly different.

- [FACT](mathematical-functions/fact.md)
  Returns the factorial of a number (n!), the product of all positive integers up to n.

- [FACTDOUBLE](mathematical-functions/fact_double.md)
  Returns the double factorial (n!!), the product of every other integer down to 1 or 2.

- [FDIST](compatibility-functions/f_dist.md)
  Returns the right-tailed F probability distribution. Used in analyses that compare variances, such as ANOVA.

- [FILTER](table-functions/filter.md)
  Filters a range or array based on one or more criteria and returns the matching rows. Supports an optional value to return when no matches are found.

- [FIND](text-functions/find.md)
  The `FIND` function in Excel is used to find the position of a specific substring within a text string.

- [FINDB](text-functions/findb.md)
  Locates one text string within another and returns the starting position in bytes. Equivalent to `FIND` in single-byte character set languages; counts each double-byte character as 2 bytes in DBCS languages such as Japanese, Chinese, and Korean.

- [FINV](compatibility-functions/f_inv.md)
  Returns the inverse of the right-tailed F probability distribution. Useful for finding critical F values for given probabilities.

- [FISHER](statistical-functions/fisher.md)
  The `FISHER` function in Excel calculates the **Fisher transformation** of a given number.

- [FISHERINV](statistical-functions/fisher_inv.md)
  The `FISHERINV` function in Excel calculates the **inverse Fisher transformation** of a given number.

- [FIXED](text-functions/fixed.md)
  The `FIXED` function in Excel is used to round a number to a specified number of decimal places and format it as text.

- [FLOOR](mathematical-functions/floor.md)
  Rounds a number down toward zero to the nearest multiple of significance.

- [FLOOR.MATH](mathematical-functions/floor_math.md)
  Rounds down to the nearest integer or multiple, with options for handling negatives.

- [FLOOR.PRECISE](mathematical-functions/floor_precise.md)
  Rounds down to the nearest integer or multiple regardless of sign.

- [FORECAST](statistical-functions/forecast.md)
  The `FORECAST` function in Excel predicts a future value based on existing values by utilizing **linear regression**.

- [FORECAST.ETS](statistical-functions/forecast__ets.md)
  The `FORECAST.ETS` function in Excel is used to predict a future value using the **Exponential Smoothing (ETS)** algorithm.

- [FORECAST.ETS.CONFINT](statistical-functions/forecast__ets__confint.md)
  The `FORECAST.ETS.CONFINT` function in Excel returns a **confidence interval** for a forecast value at a specified target date, using the **Exponential Smoothing (ETS)** algorithm.

- [FORECAST.ETS.SEASONALITY](statistical-functions/forecast__ets__seasonality.md)
  The `FORECAST.ETS.SEASONALITY` function in Excel returns the length of the **seasonal pattern** detected by the **Exponential Smoothing (ETS)** algorithm in the specified time series data.

- [FORECAST.ETS.STAT](statistical-functions/forecast__ets__stat.md)
  The `FORECAST.ETS.STAT` function in Excel returns a **statistical value** related to the **Exponential Smoothing (ETS)** forecast model, providing access to smoothing parameters and goodness-of-fit metrics.

- [FORECAST.LINEAR](statistical-functions/forecast_linear.md)
  The `FORECAST.LINEAR` function in Excel is similar to the `FORECAST` function and is used to predict or estimate a future value along a linear trend.

- [FORMULATEXT](lookup-and-reference-functions/formula_text.md)
  Returns the formula from a referenced cell as text. Helpful for auditing, documentation, and troubleshooting.

- [FREQUENCY](statistical-functions/frequency.md)
  The `FREQUENCY` function in Excel is used to calculate the **frequency distribution** of a dataset within specified intervals or bins.

- [FTEST](compatibility-functions/f_test.md)
  Returns the result of an F-test as a probability that two arrays have equal variances. Commonly used to compare variability between two data sets.

- [FV](financial-functions/fv.md)
  Returns the future value of an investment based on periodic, constant payments and a constant interest rate.

- [FVSCHEDULE](financial-functions/fv_schedule.md)
  Returns the future value of an initial principal after applying a schedule of interest rates. Useful for varying-rate growth.

- [GAMMA](statistical-functions/gamma.md)
  Returns the Gamma function value for a specified number; generalizes factorial to real numbers.

- [GAMMA.DIST](statistical-functions/gamma__dist.md)
  The `GAMMA.DIST` function in Excel is used to calculate the **Gamma probability density function or cumulative distribution function** for a specified set of parameters.

- [GAMMA.INV](statistical-functions/gamma__inv.md)
  The `GAMMA.INV` function in Excel is used to calculate the **inverse of the Gamma cumulative distribution function** for a given probability and specified parameters.

- [GAMMADIST](statistical-functions/gamma_dist.md)
  The `GAMMADIST` function in Excel is used to calculate the **Gamma distribution** for a given set of values.

- [GAMMAINV](statistical-functions/gamma_inv.md)
  The `GAMMAINV` function in Excel is used to calculate the **inverse of the Gamma cumulative distribution** for a given probability.

- [GAMMALN](statistical-functions/gamma_ln.md)
  Returns the natural logarithm of the Gamma function for a specified value.

- [GAMMALN.PRECISE](statistical-functions/gamma_ln_precise.md)
  Returns the natural logarithm of the Gamma function with improved precision.

- [GAUSS](statistical-functions/gauss.md)
  Returns 0.5 minus the standard normal cumulative distribution for the given z, i.e., probability between 0 and z.

- [GCD](mathematical-functions/gcd.md)
  Returns the greatest common divisor of two or more integers.

- [GEOMEAN](statistical-functions/geo_mean.md)
  Returns the geometric mean of positive numbers, useful for growth rates and ratios.

- [GESTEP](engineering-functions/ge_step.md)
  Returns 1 if a number is greater than or equal to a step value; otherwise returns 0. Handy for threshold tests and step-based logic.

- [GROWTH](statistical-functions/growth.md)
  The `GROWTH` function in Excel is used to calculate **exponential growth** by predicting future values based on existing data.

- [GROUPBY](lookup-and-reference-functions/groupby.md)
  Groups data by one or more row fields and aggregates values using a specified function such as SUM, AVERAGE, or COUNT. Produces pivot-table-style summaries directly in a formula with options for headers, totals, sorting, and filtering.

- [HARMEAN](statistical-functions/har_mean.md)
  Returns the harmonic mean of positive numbers, emphasizing smaller values; useful for rates and ratios.

- [HEX2BIN](engineering-functions/hex_2_bin.md)
  Converts a hexadecimal number to binary with optional padding. Supports two's complement for negative values within range.

- [HEX2DEC](engineering-functions/hex_2_dec.md)
  Converts a hexadecimal number to decimal. Interprets negative values using two's complement.

- [HEX2OCT](engineering-functions/hex_2_oct.md)
  Converts a hexadecimal number to octal with optional padding. Supports two's complement for negative values within range.

- [HLOOKUP](table-functions/hlookup.md)
  Searches for a value in the top row of a table and returns a value in the same column from a specified row. Horizontal equivalent of VLOOKUP.

- [HOUR](date-time-functions/hour.md)
  Returns the hour component of a time value as an integer from 0 to 23.

- [HSTACK](lookup-and-reference-functions/h_stack.md)
  Horizontally stacks values or arrays into a single array, aligning rows and concatenating columns. Useful for combining ranges side by side.

- [HYPGEOM.DIST](statistical-functions/hypgeom_dist.md)
  Returns the hypergeometric distribution (PDF or CDF), modeling successes in draws without replacement from a finite population.

- [HYPGEOMDIST](compatibility-functions/hypgeom_dist.md)
  Returns the hypergeometric distribution. Models successes in draws without replacement from a finite population.

- [IF](conditional-functions/if.md)
  Checks a condition and returns one value if TRUE and another if FALSE. Often nested to handle multiple conditions.

- [IFERROR](conditional-functions/if_error.md)
  Returns a specified value if a formula evaluates to an error; otherwise returns the result of the formula. Useful for handling errors like #DIV/0! or #N/A.

- [IFNA](logical-functions/ifna.md)
  Returns a specified value if a formula evaluates to #N/A; otherwise returns the formula result. Useful for handling lookup misses while preserving other error types.

- [IFS](conditional-functions/ifs.md)
  Evaluates multiple conditions and returns the value for the first condition that is TRUE. Simplifies complex nested IF statements.

- [IMABS](engineering-functions/im_abs.md)
  Returns the absolute value (modulus) of a complex number in text form. Useful for magnitude calculations in complex arithmetic.

- [IMAGINARY](engineering-functions/imaginary.md)
  Returns the imaginary coefficient of a complex number. If the number has no imaginary part, returns 0.

- [IMARGUMENT](engineering-functions/im_argument.md)
  Returns the argument (phase angle) of a complex number in radians. Useful for polar representation.

- [IMCONJUGATE](engineering-functions/im_conjugate.md)
  Returns the complex conjugate of a complex number by changing the sign of the imaginary part.

- [IMCOS](engineering-functions/im_cos.md)
  Returns the cosine of a complex number expressed as text.

- [IMCOSH](engineering-functions/im_cosh.md)
  Returns the hyperbolic cosine of a complex number expressed as text.

- [IMCOT](engineering-functions/im_cot.md)
  Returns the cotangent of a complex number expressed as text.

- [IMCSC](engineering-functions/im_csc.md)
  Returns the cosecant of a complex number expressed as text.

- [IMCSCH](engineering-functions/im_csch.md)
  Returns the hyperbolic cosecant of a complex number expressed as text.

- [IMDIV](engineering-functions/im_div.md)
  Returns the quotient of two complex numbers.

- [IMEXP](engineering-functions/im_exp.md)
  Returns the exponential of a complex number.

- [IMLN](engineering-functions/im_ln.md)
  Returns the natural logarithm of a complex number.

- [IMLOG10](engineering-functions/im_log10.md)
  Returns the base‑10 logarithm of a complex number.

- [IMLOG2](engineering-functions/im_log2.md)
  Returns the base‑2 logarithm of a complex number.

- [IMPOWER](engineering-functions/im_power.md)
  Returns a complex number raised to a power.

- [IMPRODUCT](engineering-functions/im_product.md)
  Returns the product of complex numbers.

- [IMREAL](engineering-functions/im_real.md)
  Returns the real coefficient of a complex number.

- [IMSEC](engineering-functions/im_sec.md)
  Returns the secant of a complex number expressed as text.

- [IMSECH](engineering-functions/im_sech.md)
  Returns the hyperbolic secant of a complex number expressed as text.

- [IMSIN](engineering-functions/im_sin.md)
  Returns the sine of a complex number expressed as text.

- [IMSINH](engineering-functions/im_sinh.md)
  Returns the hyperbolic sine of a complex number expressed as text.

- [IMSQRT](engineering-functions/im_sqrt.md)
  Returns the square root of a complex number.

- [IMSUB](engineering-functions/im_sub.md)
  Returns the difference of two complex numbers.

- [IMSUM](engineering-functions/im_sum.md)
  Returns the sum of complex numbers.

- [IMTAN](engineering-functions/im_tan.md)
  Returns the tangent of a complex number expressed as text.

- [INDEX](table-functions/index.md)
  The `INDEX` function in Excel returns a value or the reference to a value from within a table or range.

- [INT](mathematical-functions/int.md)
  Rounds a number down to the nearest integer.

- [INTERCEPT](statistical-functions/intercept.md)
  The `INTERCEPT` function in Excel is used to calculate the **y-intercept** of the linear regression line for a given set of data points.

- [INTRATE](financial-functions/int_rate.md)
  Returns the interest rate for a fully invested security given settlement, maturity, investment, and redemption, using a specified day-count basis.

- [IPMT](financial-functions/i_pmt.md)
  Returns the interest payment for a specific period of an annuity based on constant periodic payments and a constant interest rate.

- [IRR](financial-functions/irr.md)
  Returns the internal rate of return for a series of cash flows. Requires at least one negative and one positive value.

- [ISBLANK](information-functions/isblank.md)
  Returns TRUE if a cell is empty; otherwise FALSE. Useful for input validation and detecting missing data.

- [ISERR](information-functions/iserr.md)
  Returns TRUE if a value is any error except #N/A. Useful for handling calculation errors while allowing #N/A to propagate for separate lookup-failure handling.

- [ISERROR](information-functions/iserror.md)
  Returns TRUE if a value is any error, including #N/A, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, and #NULL!. Useful for universal error handling in formulas.

- [ISNUMBER](mathematical-functions/is_number.md)
  Returns TRUE if a value is numeric; otherwise FALSE.

- [ISO.CEILING](mathematical-functions/iso_ceiling.md)
  Rounds a number up to the nearest multiple of significance using ISO-compliant rules.

- [ISOWEEKNUM](date-time-functions/iso_week_num.md)
  Returns the ISO week number of a date (1–53) according to ISO 8601 rules.

- [ISPMT](financial-functions/is_pmt.md)
  Returns the interest paid for a given period of an investment using simple interest. Useful for straight-line interest on principal.

- [JIS](text-functions/jis.md)
  Converts half-width (single-byte) characters in a text string to full-width (double-byte) characters. Equivalent to the `DBCS` function, named after the Japanese Industrial Standard (JIS) character encoding. Inverse of `ASC`.

- [KURT](statistical-functions/kurt.md)
  The `KURT` function in Excel is used to calculate the **kurtosis** of a dataset, which measures the sharpness or " tailedness" of the data distribution.

- [LARGE](statistical-functions/large.md)
  The `LARGE` function in Excel is used to **return the k-th largest value** in a dataset.

- [LAMBDA](logical-functions/lambda.md)
  Creates custom, reusable functions by defining parameters and a calculation formula. Note: Codcel supports inline LAMBDA only; named LAMBDAs are not currently supported.

- [LET](logical-functions/let.md)
  Assigns names to calculation results within a formula, reducing repetition and improving readability. Similar to variable assignment in programming.

- [LCM](mathematical-functions/lcm.md)
  Returns the least common multiple of integers. Useful for aligning cycles or denominators.

- [LEFT](text-functions/left.md)
  The `LEFT` function in Excel is a text function that allows users to extract a specified number of characters from the beginning (left side) of a text string.

- [LEFTB](text-functions/leftb.md)
  Returns the first character or characters in a text string, based on the number of bytes you specify. Equivalent to `LEFT` in single-byte character set languages; counts each double-byte character as 2 bytes in DBCS languages such as Japanese, Chinese, and Korean.

- [LENB](text-functions/lenb.md)
  Returns the number of bytes in a text string rather than characters. Equivalent to `LEN` in single-byte character set languages; counts each double-byte character as 2 bytes in DBCS languages such as Japanese, Chinese, and Korean.

- [LEN](text-functions/len.md)
  Returns the number of characters in a text string, including spaces, punctuation, and numbers.

- [LINEST](statistical-functions/linest.md)
  The `LINEST` function in Excel is used to calculate the **statistics for a line by fitting a straight line (using the linear regression method)** to your dataset.

- [LN](mathematical-functions/ln.md)
  Returns the natural logarithm (base e) of a positive number.

- [LOG](mathematical-functions/log.md)
  Returns the logarithm of a number to a specified base. Defaults to base 10 if omitted.

- [LOG10](mathematical-functions/log10.md)
  Returns the base‑10 logarithm of a positive number.

- [LOGEST](statistical-functions/logest.md)
  The `LOGEST` function in Excel is used to **calculate an exponential curve that best fits your data**, and returns an array of values that describe the curve.

- [LOGINV](statistical-functions/log_inv.md)
  The `LOGINV` function in Excel is used to calculate the **inverse of the log-normal cumulative distribution** for a given probability.

- [LOGNORM.DIST](statistical-functions/log_norm__dist.md)
  The `LOGNORM.DIST` function in Excel is used to **return values from a log-normal distribution**, which is a probability distribution of a random variable whose logarithm is normally distributed.

- [LOGNORM.INV](statistical-functions/log_norm_inv.md)
  The `LOGNORM.INV` function in Excel is used to calculate the inverse of the lognormal cumulative distribution function ( CDF) for a given probability, mean, and standard deviation of a dataset.

- [LOGNORMDIST](statistical-functions/log_norm_dist.md)
  The `LOGNORMDIST` function in Excel is used to return the cumulative lognormal distribution of a value `x`.

- [LOOKUP](table-functions/lookup.md)
  The `LOOKUP` function in Excel is used to search for a value in a row or column range and returns a corresponding value from a different row or column.

- [LOWER](text-functions/lower.md)
  The `LOWER` function in Excel is used to convert all uppercase letters in a text string to lowercase letters.

- [MAKEARRAY](logical-functions/makearray.md)
  Creates an array of a specified size by applying a LAMBDA function to generate each element based on its row and column position.

- [MAP](logical-functions/map.md)
  Applies a LAMBDA function to each element in one or more arrays, returning a new array of transformed results.

- [MATCH](table-functions/match.md)
  The `MATCH` function in Excel searches for a specified value in a range and returns the relative position of that item within the range.

- [MAX](mathematical-functions/max.md)
  Returns the largest value among numbers, ranges, or references.

- [MAXA](statistical-functions/maxa.md)
  Returns the largest value in a set of values, including logical values and text. Unlike `MAX`, it treats `TRUE` as `1`, `FALSE` as `0`, and text as `0`.

- [MAXIFS](statistical-functions/max_ifs.md)
  The `MAXIFS` function in Excel is used to **find the maximum value in a range that meets one or more conditions ( criteria)**.

- [MDETERM](mathematical-functions/m_determ.md)
  Returns the matrix determinant of a square array or cell range.

- [MDURATION](financial-functions/m_duration.md)
  Returns the modified duration of a security with periodic interest. Measures interest rate sensitivity adjusted for yield compounding.

- [MEDIAN](statistical-functions/median.md)
  The `MEDIAN` function in Excel is used to **calculate the median or the middle value** of a set of numbers.

- [MID](text-functions/mid.md)
  The `MID` function in Excel is used to extract a specific number of characters from a text string, starting at a specified position.

- [MIDB](text-functions/midb.md)
  Returns a specific number of characters from a text string, starting at a specified position, based on the number of bytes rather than characters. Equivalent to `MID` in single-byte character set languages; counts each double-byte character as 2 bytes in DBCS languages such as Japanese, Chinese, and Korean.

- [MIN](mathematical-functions/min.md)
  Returns the smallest value among numbers, ranges, or references.

- [MINA](statistical-functions/mina.md)
  Returns the smallest value in a set of values, including logical values and text. Unlike `MIN`, it treats `TRUE` as `1`, `FALSE` as `0`, and text as `0`.

- [MINIFS](statistical-functions/min_ifs.md)
  The `MINIFS` function in Excel is used to **find the minimum value in a range that meets one or more conditions ( criteria)**.

- [MINUTE](date-time-functions/minute.md)
  Returns the minute component of a time value as an integer from 0 to 59.

- [MINVERSE](mathematical-functions/m_inverse.md)
  Returns the inverse matrix of a square array or cell range.

- [MIRR](financial-functions/m_irr.md)
  Returns the modified internal rate of return for a series of cash flows, considering the cost of investment and reinvestment rate.

- [MMULT](mathematical-functions/m_mult.md)
  Returns the matrix product of two arrays, with inner dimensions matching.

- [MOD](mathematical-functions/mod.md)
  Returns the remainder after division; sign follows the divisor.

- [MODE](statistical-functions/mode.md)
  The `MODE` function in Excel is used to **find the most frequently occurring value** in a dataset.

- [MODE.MULT](statistical-functions/mode_mult.md)
  The `MODE.MULT` function in Excel is used to **find one or more modes (most frequently occurring values)** in a dataset.

- [MODE.SNGL](statistical-functions/mode_sngl.md)
  The `MODE.SNGL` function in Excel is used to **find the single most frequently occurring value (mode)** in a dataset.

- [MONTH](date-time-functions/month.md)
  Returns the month of a date as an integer from 1 to 12.

- [MROUND](mathematical-functions/mround.md)
  Rounds a number to the nearest multiple of a given significance.

- [MULTINOMIAL](mathematical-functions/multinomial.md)
  Returns (sum of inputs)! divided by the product of each input's factorial.

- [MULTIPLY](mathematical-functions/multiply.md)
  In Excel, the `*` symbol is used as an arithmetic operator to multiply numbers together.

- [MUNIT](mathematical-functions/m_unit.md)
  Returns an identity matrix of a specified dimension.

- [N](information-functions/n.md)
  Converts values to numbers. Returns the numeric value for numbers, dates, or logicals; returns 0 for text.

- [NEGBINOM.DIST](statistical-functions/neg_binom__dist.md)
  The `NEGBINOM.DIST` function in Excel is used to **calculate the negative binomial distribution**, which represents the probability of a certain number of failures occurring before a specified number of successes is achieved in a series of independent trials.

- [NEGBINOMDIST](statistical-functions/neg_binom_dist.md)
  The `NEGBINOMDIST` function in Excel is used to **calculate the negative binomial distribution**.

- [NETWORKDAYS](date-time-functions/network-days.md)
  Returns the number of whole working days between two dates, excluding weekends and optionally specified holidays.

- [NETWORKDAYS.INTL](date-time-functions/network-days-intl.md)
  Returns the number of whole working days between two dates, with the ability to specify custom weekend days and optionally exclude holidays. Extends `NETWORKDAYS` for non-standard work-week configurations.

- [NOMINAL](financial-functions/nominal.md)
  Returns the nominal annual interest rate given the effective rate and number of compounding periods per year.

- [NORM.DIST](statistical-functions/norm__dist.md)
  The `NORM.DIST` function in Excel is used to **calculate the normal distribution for a given value**.

- [NORM.INV](statistical-functions/norm__inv.md)
  The `NORM.INV` function in Excel is used to **calculate the inverse of the normal cumulative distribution** for a specified probability, mean, and standard deviation.

- [NORM.S.DIST](statistical-functions/norm__s__dist.md)
  Calculates the standard normal distribution for a z-score. Returns the cumulative distribution when cumulative is TRUE, or the probability density when FALSE.

- [NORM.S.INV](statistical-functions/norm__s__inv.md)
  Returns the inverse of the standard normal cumulative distribution, giving the z-score for a given probability between 0 and 1.

- [NORMDIST](statistical-functions/norm_dist.md)
  The `NORMDIST` function in Excel is used to **calculate the normal distribution** for a given value.

- [NORMINV](statistical-functions/norm_inv.md)
  The `NORMINV` function in Excel is used to **calculate the inverse of the cumulative normal distribution** for a given probability.

- [NORMSDIST](statistical-functions/norm_s_dist.md)
  Calculates the standard normal cumulative distribution for a given z-score (mean 0, standard deviation 1).

- [NORMSINV](statistical-functions/norm_s_inv.md)
  Returns the inverse of the standard normal cumulative distribution (mean 0, standard deviation 1). Useful for converting probabilities to z-scores.

- [NOT](mathematical-functions/not.md)
  Returns the logical negation of a value; TRUE becomes FALSE and vice versa.

- [NOW](date-time-functions/now.md)
  Returns the current date and time as a serial number; updates when the worksheet recalculates.

- [NPER](financial-functions/n_per.md)
  Returns the number of periods for an investment based on periodic, constant payments and a constant interest rate.

- [NPV](financial-functions/npv.md)
  Returns the net present value of an investment based on a discount rate and a series of cash flows.

- [NUMBERVALUE](text-functions/number_value.md)
  The `NUMBERVALUE` function in Excel converts a text representation of a number into an actual numeric value.

- [OCT2BIN](engineering-functions/oct_2_bin.md)
  Converts an octal number to binary with optional padding. Supports two's complement for negative values within range.

- [OCT2DEC](engineering-functions/oct_2_dec.md)
  Converts an octal number to decimal. Interprets negatives using two's complement within the valid range.

- [OCT2HEX](engineering-functions/oct_2_hex.md)
  Converts an octal number to hexadecimal with optional padding. Supports two's complement for negative values within range.

- [ODD](mathematical-functions/odd.md)
  Rounds a number up to the nearest odd integer.

- [ODDFPRICE](financial-functions/odd_f_price.md)
  Returns the price per $100 face value of a security with an odd (irregular) first coupon period.

- [ODDFYIELD](financial-functions/odd_f_yield.md)
  Returns the yield of a security with an odd (irregular) first coupon period.

- [ODDLPRICE](financial-functions/odd_l_price.md)
  Returns the price per $100 face value of a security with an odd (irregular) last coupon period.

- [ODDLYIELD](financial-functions/odd_l_yield.md)
  Returns the yield of a security with an odd (irregular) last coupon period.

- [OFFSET](lookup-and-reference-functions/offset.md)
  Returns a reference to a range that is offset from a starting cell by a specified number of rows and columns. Useful for creating dynamic ranges and sliding window calculations.

- [OR](logical-functions/or.md)
  Returns TRUE if any of the arguments evaluate to TRUE; otherwise returns FALSE. Useful when only one of several conditions needs to be met.

- [PDURATION](financial-functions/p_duration.md)
  Returns the number of periods required for an investment to reach a specified value at a given rate.

- [PEARSON](statistical-functions/pearson.md)
  The `PEARSON` function in Excel is used to **calculate the Pearson correlation coefficient** between two sets of data.

- [PERCENTILE](statistical-functions/percentile.md)
  The `PERCENTILE` function in Excel is used to calculate the **k-th percentile of a dataset**, where `k` is a value between 0 and 1.

- [PERCENTILE.EXC](statistical-functions/percentile__exc.md)
  The `PERCENTILE.EXC` function in Excel is used to **return the k-th percentile of a data set**, where `k` is a percentile value between 0 and 1 (exclusive).

- [PERCENTILE.INC](statistical-functions/percentile__inc.md)
  The `PERCENTILE.INC` function in Excel is used to **return the k-th percentile of a data set**, where `k` is a percentile value between 0 and 1 (inclusive).

- [PERCENTRANK](compatibility-functions/percent_rank.md)
  Returns the rank of a value in a data set as a percentage from 0 to 1. Useful for percentile-based comparisons.

- [PERCENTRANK.EXC](statistical-functions/percent_rank__exc.md)
  The `PERCENTRANK.EXC` function in Excel calculates the **rank of a value as a percentage** of a range of values ( excluding the boundaries).

- [PERCENTRANK.INC](statistical-functions/percent_rank__inc.md)
  The `PERCENTRANK.INC` function in Excel calculates the **rank of a value as a percentage** of a range of values (including the boundaries).

- [PERMUT](statistical-functions/permut.md)
  The `PERMUT` function in Excel is used to **calculate the number of permutations for a given number of objects chosen from a larger set**.

- [PERMUTATIONA](statistical-functions/permutation_a.md)
  The `PERMUTATIONA` function in Excel is used to **return the number of permutations for a given number of objects (with repetition allowed)** from a total number of objects.

- [PHI](statistical-functions/phi.md)
  The `PHI` function in Excel is used to **return the value of the density function for a standard normal distribution** at a given value.

- [PHONETIC](text-functions/phonetic.md)
  Extracts the furigana (phonetic guide) characters from a Japanese text string. Returns the phonetic reading stored by the Input Method Editor (IME), or the original text if no furigana data is present.

- [PI](mathematical-functions/pi.md)
  Returns the constant π (pi) ≈ 3.14159.

- [PMT](financial-functions/pmt.md)
  Returns the periodic payment for a loan or investment based on constant payments and a constant interest rate.

- [POISSON](statistical-functions/poisson.md)
  The `POISSON` function in Excel is used to **calculate the Poisson probability mass function or the cumulative Poisson probability** for a given number of events.

- [POISSON.DIST](statistical-functions/poisson__dist.md)
  The `POISSON.DIST` function in Excel is used to **calculate the Poisson probability mass function or the cumulative Poisson probability** for a given number of events.

- [POWER](mathematical-functions/power.md)
  Raises a number to a power (number^power). Equivalent to using the ^ operator.

- [PPMT](financial-functions/p_pmt.md)
  Returns the principal portion of a payment for a given period of an investment.

- [PRICE](financial-functions/price.md)
  Returns the price per $100 face value of a security that pays periodic interest, based on yield and day count basis.

- [PRICEDISC](financial-functions/price_disc.md)
  Returns the price per $100 face value of a discounted security.

- [PRICEMAT](financial-functions/price_mat.md)
  Returns the price per $100 face value of a security that pays interest at maturity.

- [PROB](statistical-functions/prob.md)
  The `PROB` function in Excel is used to **calculate the probability associated with a range of values between upper and lower limits**, given a set of corresponding probabilities.

- [PRODUCT](mathematical-functions/product.md)
  Multiplies all the given numbers and returns the product.

- [PROPER](text-functions/proper.md)
  The `PROPER` function in Excel capitalizes the first letter of each word in a given text string while converting the remaining letters to lowercase.

- [PV](financial-functions/pv.md)
  Returns the present value of an investment based on a series of future payments and a discount rate.

- [QUARTILE](compatibility-functions/quartile.md)
  Returns the quartile of a data set. Identifies values at the 0th, 25th, 50th, 75th, and 100th percentiles.

- [QUARTILE.EXC](statistical-functions/quartile__exc.md)
  The `QUARTILE.EXC` function in Excel is used to **return the quartile of a given data set, excluding the smallest and largest values**.

- [QUARTILE.INC](statistical-functions/quartile__inc.md)
  The `QUARTILE.INC` function in Excel is used to **return the quartile of a given dataset, including all data points**.

- [QUOTIENT](mathematical-functions/quotient.md)
  Returns the integer portion of a division, discarding the remainder.

- [RADIANS](mathematical-functions/radians.md)
  Converts degrees to radians.

- [RAND](mathematical-functions/rand.md)
  Returns a random decimal number in [0,1). Recalculates on workbook updates.

- [RANDARRAY](mathematical-functions/rand_array.md)
  Returns an array of random numbers with configurable dimensions and bounds.

- [RANDBETWEEN](mathematical-functions/rand_between.md)
  Returns a random integer between the specified inclusive bounds.

- [RANK](compatibility-functions/rank.md)
  Returns the rank of a number in a list of numbers. Supports ranking in descending or ascending order.

- [RANK.AVG](statistical-functions/rank__avg.md)
  The `RANK.AVG` function in Excel is used to **determine the rank of a number in a dataset**, but unlike the `RANK.EQ` function, it assigns an average rank if multiple numbers have the same value (i.e., ties).

- [RANK.EQ](statistical-functions/rank__eq.md)
  The `RANK.EQ` function in Excel is used to **determine the rank of a number in a dataset**, ensuring that tied values receive the same rank.

- [RATE](financial-functions/rate.md)
  Returns the interest rate per period of an annuity given payment amount, number of periods, present value, and future value.

- [RECEIVED](financial-functions/received.md)
  Returns the amount received at maturity for a fully invested security.

- [REDUCE](logical-functions/reduce.md)
  Reduces an array to a single accumulated value by applying a LAMBDA function cumulatively to each element, starting from an initial value.

- [REGEXEXTRACT](text-functions/regexextract.md)
  Extracts the first substring that matches a regular expression pattern from a text string. Returns the first capture group if one exists, or the entire match otherwise. Useful for parsing numbers, emails, codes, and other patterns from free-form text.

- [REGEXTEST](text-functions/regextest.md)
  Tests whether a text string matches a regular expression pattern, returning `TRUE` or `FALSE`. Useful for data validation, filtering, and conditional logic based on text patterns.

- [REGEXREPLACE](text-functions/regexreplace.md)
  Replaces all substrings matching a regular expression pattern with a replacement string. Supports capture group backreferences for advanced text reformatting. Useful for cleaning, restructuring, and transforming text patterns.

- [REPLACE](text-functions/replace.md)
  The `REPLACE` function in Excel is used to replace part of a text string based on the position and length of the substring you want to replace.

- [REPLACEB](text-functions/replaceb.md)
  The `REPLACEB` function in Excel replaces part of a text string based on byte positions rather than character positions, which is important for double-byte character set (DBCS) languages such as Japanese, Chinese, and Korean.

- [REPT](text-functions/rept.md)
  The `REPT` function in Excel is used to repeat a text string a specified number of times.

- [RIGHT](text-functions/right.md)
  The `RIGHT` function in Excel is a text function that allows users to extract a specified number of characters from the end (right side) of a text string.

- [RIGHTB](text-functions/rightb.md)
  Returns the last character or characters in a text string, based on the number of bytes you specify. Equivalent to `RIGHT` in single-byte character set languages; counts each double-byte character as 2 bytes in DBCS languages such as Japanese, Chinese, and Korean.

- [ROMAN](mathematical-functions/roman.md)
  Converts an Arabic numeral to a Roman numeral string.

- [ROUND](mathematical-functions/round.md)
  Rounds a number to a specified number of digits.

- [ROUNDDOWN](mathematical-functions/round_down.md)
  Rounds a number down toward zero.

- [ROUNDUP](mathematical-functions/round_up.md)
  Rounds a number up, away from zero.

- [ROW](lookup-and-reference-functions/row.md)
  Returns the row number of a cell reference. If no reference is provided, returns the row number of the cell containing the formula.

- [ROWS](lookup-and-reference-functions/rows.md)
  Returns the number of rows in a reference or array. Useful for dynamic formulas and determining array dimensions.

- [RRI](financial-functions/rri.md)
  Returns the equivalent interest rate for the growth of an investment over a number of periods.

- [RSQ](statistical-functions/rsq.md)
  The `RSQ` function in Excel is used to **return the square of the Pearson product moment correlation coefficient (r)** between two sets of data points.

- [SEARCH](text-functions/search.md)
  The `SEARCH` function in Excel is used to find the position of a specific substring within a text string.

- [SEARCHB](text-functions/searchb.md)
  Locates one text string within another and returns the starting position in bytes. Case-insensitive and supports wildcards. Equivalent to `SEARCH` in single-byte character set languages; counts each double-byte character as 2 bytes in DBCS languages such as Japanese, Chinese, and Korean.

- [SCAN](logical-functions/scan.md)
  Applies a LAMBDA function cumulatively to each element of an array, returning an array of all intermediate accumulated values. Useful for running totals, cumulative products, and step-by-step aggregations.

- [SEC](mathematical-functions/sec.md)
  Returns the secant of an angle (in radians), the reciprocal of COS. Converts degrees with RADIANS; returns #DIV/0! when COS(number) = 0.

- [SECH](mathematical-functions/sech.md)
  Returns the hyperbolic secant of a number, defined as 2/(e^x + e^-x). Approaches zero as the magnitude of the input grows.

- [SECOND](date-time-functions/second.md)
  Returns the second component of a time value as an integer from 0 to 59.

- [SEQUENCE](mathematical-functions/sequence.md)
  Generates an array of sequential numbers with configurable rows, columns, start value, and step.

- [SERIESSUM](mathematical-functions/series_sum.md)
  Calculates the sum of a power series at x using an initial power n, step m, and a list of coefficients. Useful for evaluating polynomials and series approximations.

- [SIGN](mathematical-functions/sign.md)
  Returns 1 for positive numbers, -1 for negative numbers, and 0 if the number is zero. Indicates the sign of a value.

- [SIN](mathematical-functions/sin.md)
  Returns the sine of an angle specified in radians. Convert degrees to radians with the RADIANS function.

- [SINH](mathematical-functions/sinh.md)
  Returns the hyperbolic sine of a number, (e^x − e^−x)/2. Grows rapidly in magnitude for large positive or negative inputs.

- [SKEW](statistical-functions/skew.md)
  The `SKEW` function in Excel is used to **return the skewness of a distribution**.

- [SKEW.P](statistical-functions/skew__p.md)
  The `SKEW.P` function in Excel is used to **return the population skewness of a distribution**.

- [SLN](financial-functions/sln.md)
  Returns the straight-line depreciation of an asset for one period given cost, salvage, and life.

- [SLOPE](statistical-functions/slope.md)
  The `SLOPE` function in Excel is used to **calculate the slope of the linear regression line** based on a set of dependent (`y`) and independent (`x`) data points.

- [SMALL](statistical-functions/small.md)
  The `SMALL` function in Excel is used to **return the k-th smallest value** in a dataset.

- [SORT](lookup-and-reference-functions/sort.md)
  Sorts the contents of a range or array in ascending or descending order based on a specified row or column.

- [SORTBY](lookup-and-reference-functions/sortby.md)
  Sorts a range or array according to values in one or more other ranges or arrays, supporting multiple sort keys and orders.

- [SQRT](mathematical-functions/sqrt.md)
  Returns the positive square root of a non‑negative number. Returns #NUM! for negative inputs.

- [SQRTPI](mathematical-functions/sqrt_pi.md)
  Returns the square root of (number × π). Accepts non‑negative numbers only.

- [STANDARDIZE](statistical-functions/standardize.md)
  The `STANDARDIZE` function in Excel is used to **return a normalized value (z-score)** from a given distribution.

- [STDEV](statistical-functions/st_dev.md)
  The `STDEV` function in Excel is used to **estimate the standard deviation** of a set of numerical data.

- [STDEV.P](statistical-functions/st_dev__p.md)
  The `STDEV.P` function in Excel is used to **calculate the standard deviation of an entire population** based on numerical data.

- [STDEV.S](statistical-functions/st_dev__s.md)
  The `STDEV.S` function in Excel is used to **calculate the standard deviation of a sample** based on numerical data.

- [STDEVA](statistical-functions/st_dev_a.md)
  The `STDEVA` function in Excel is used to **calculate the standard deviation of a sample**, but it evaluates both numeric and non-numeric data.

- [STDEVPA](statistical-functions/st_dev_pa.md)
  The `STDEVPA` function in Excel is used to **calculate the standard deviation of an entire population**, evaluating both numeric and non-numeric data.

- [STDEVP](compatibility-functions/st_dev_p.md)
  Calculates the standard deviation for an entire population. Provided for compatibility with earlier Excel versions.

- [STEYX](statistical-functions/steyx.md)
  The `STEYX` function in Excel is used to **calculate the standard error of the predicted y-value in a linear regression ** for a given set of dependent and independent variables.

- [SUBSTITUTE](text-functions/substitute.md)
  The `SUBSTITUTE` function in Excel replaces occurrences of a specific text string (`old_text`) in a given text (`text`) with another text string (`new_text`).

- [SUBTOTAL](mathematical-functions/sub_total.md)
  Returns a subtotal for a range using a specified function number, with options to include or ignore hidden rows. Ideal for calculations on filtered data.

- [SUBTRACT](mathematical-functions/subtract.md)
  Represents the subtraction operator (-) used to subtract numbers, cell references, or expressions. Excel treats text or empty cells as 0 in arithmetic contexts.

- [SUM](mathematical-functions/sum.md)
  Adds numbers together across values, ranges, or references and returns their total. Ignores text and empty cells in ranges.

- [SUMIF](conditional-functions/sum_if.md)
  Sums values in a range that meet a specified condition. Supports an optional separate sum_range and criteria with numbers, expressions, text, or references.

- [SUMIFS](mathematical-functions/sum_ifs.md)
  Sums values that meet multiple criteria across one or more ranges. Conditions are combined with AND logic; wildcards and comparison operators are supported.

- [SUMPRODUCT](mathematical-functions/sum_product.md)
  Multiplies corresponding elements in arrays and returns the sum of products. Useful for weighted calculations and conditional aggregations.

- [SUMSQ](mathematical-functions/sum_sq.md)
  Returns the sum of the squares of the arguments. Helpful in statistical and mathematical computations.

- [SUMX2MY2](mathematical-functions/sum_x2my2.md)
  Returns the sum of the difference of squares for corresponding elements in two arrays. Arrays must be the same size.

- [SUMX2PY2](mathematical-functions/sum_x2py2.md)
  Returns the sum of the sum of squares for corresponding elements in two arrays. Arrays must be the same size.

- [SUMXMY2](mathematical-functions/sum_xmy2.md)
  Returns the sum of squares of differences between corresponding elements in two arrays. Arrays must be the same size.

- [SWITCH](logical-functions/switch.md)
  Evaluates an expression against a list of values and returns the result for the first match; if none match, returns an optional default. Simplifies formulas that would otherwise require multiple nested IF statements.

- [SYD](financial-functions/syd.md)
  Returns the sum-of-years' digits depreciation of an asset for a specified period, accelerating depreciation in earlier years.

- [T](text-functions/t.md)
  The `T` function in Excel checks whether a value is text and returns it if true.

- [TAKE](information-functions/take.md)
  Extracts a specified number of rows or columns from the beginning or end of an array. Positive values take from the start; negative values take from the end.

- [T.DIST](statistical-functions/t__dist.md)
  The `T.DIST` function in Excel is used to **return the probability density (p-value) of the left-tailed Student's t-distribution**, which is widely utilized in hypothesis testing and statistical significance analysis.

- [T.DIST.2T](statistical-functions/t__dist__2t.md)
  The `T.DIST.2T` function in Excel is used to **return the two-tailed Student's t-distribution probability**, which is widely utilized in hypothesis testing to evaluate the significance of a t-value for both tails of the distribution.

- [T.DIST.RT](statistical-functions/t__dist__rt.md)
  The `T.DIST.RT` function in Excel is used to **return the one-tailed probability of the Student's t-distribution**, which is commonly applied in hypothesis testing, particularly for evaluating the significance of a t-value in the right tail of the distribution.

- [T.INV](statistical-functions/t__inv.md)
  The `T.INV` function in Excel is used to **return the t-value associated with a given probability and degrees of freedom **, based on the Student's t-distribution.

- [T.INV.2T](statistical-functions/t__inv__2t.md)
  The `T.INV.2T` function in Excel is used to **return the t-value for the two-tailed Student's t-distribution**, given a probability and degrees of freedom.

- [T.TEST](statistical-functions/t__test.md)
  The `T.TEST` function in Excel is used to **calculate the probability associated with a Student's t-test**.

- [TAN](mathematical-functions/tan.md)
  Returns the tangent of an angle given in radians.

- [TANH](mathematical-functions/tanh.md)
  Returns the hyperbolic tangent of a number.

- [TBILLEQ](financial-functions/t_bill_eq.md)
  Returns the bond-equivalent yield for a Treasury bill based on its discount rate and maturity.

- [TBILLPRICE](financial-functions/t_bill_price.md)
  Returns the price per $100 face value for a Treasury bill given its discount rate and settlement/maturity dates.

- [TBILLYIELD](financial-functions/t_bill_yield.md)
  Returns the yield for a Treasury bill based on its price and settlement/maturity dates.

- [TDIST](statistical-functions/t_dist.md)
  The `TDIST` function in Excel is used to **return the probability (p-value) of the Student's t-distribution**, which is commonly used to test hypotheses and evaluate statistical significance in data analysis.

- [TEXT](text-functions/text.md)
  The `TEXT` function in Excel is used to format numbers, dates, and times as text in a specific format.

- [TEXTAFTER](text-functions/text-after.md)
  The `TEXTAFTER` function in Excel extracts the portion of a text string that appears after a specified delimiter.

- [TEXTBEFORE](text-functions/text-before.md)
  The `TEXTBEFORE` function in Excel extracts the portion of a text string that appears before a specified delimiter.

- [TEXTJOIN](text-functions/text-join.md)
  Introduced in Excel 2016, the `TEXTJOIN` function allows users to concatenate (or join) multiple text strings from a range of cells using a specified delimiter.

- [TEXTSPLIT](text-functions/text-split.md)
  The `TEXTSPLIT` function in Excel is used to split a text string into multiple cells based on a specified column delimiter, row delimiter, or both.

- [TIME](date-time-functions/time.md)
  Returns a time value given hours, minutes, and seconds. Use it to construct valid Excel times from components.

- [TIMEVALUE](date-time-functions/time-value.md)
  Converts a time in text format to a decimal number representing the time. Useful for turning text times into proper time values.

- [TINV](statistical-functions/t_inv.md)
  The `TINV` function in Excel is used to **return the critical t-value (inverse of the Student's t-distribution)** based on a given probability and the degrees of freedom.

- [TODAY](date-time-functions/today.md)
  Returns the current date as a serial number; updates when the worksheet recalculates.

- [TRANSPOSE](lookup-and-reference-functions/transpose.md)
  Rotates the orientation of a range or array, converting rows to columns and columns to rows. Useful for restructuring data layouts.

- [TREND](statistical-functions/trend.md)
  The `TREND` function in Excel is used to **return values along a linear trend** that fits your data points.

- [TRIM](text-functions/trim.md)
  The `TRIM` function in Excel removes all extra spaces from a text string, leaving only single spaces between words.

- [TRIMRANGE](lookup-and-reference-functions/trimrange.md)
  Removes empty rows and columns from the edges of an array or range. Useful for cleaning up data before further processing.

- [TRIMMEAN](statistical-functions/trim_mean.md)
  The `TRIMMEAN` function in Excel is used to **calculate the mean (average) of a data set excluding a specified percentage of data points from the top and bottom**.

- [TRUNC](mathematical-functions/trunc.md)
  Truncates a number to an integer by removing the fractional part.

- [TTEST](statistical-functions/t_test.md)
  The `TTEST` function in Excel is used to **calculate the probability (p-value) associated with a Student's t-test**.

- [UNICHAR](text-functions/uni_char.md)
  The `UNICHAR` function in Excel returns the Unicode character that corresponds to the given numeric value.

- [UNICODE](text-functions/unicode.md)
  The `UNICODE` function in Excel returns the numeric Unicode value of the first character in a text string.

- [UNIQUE](lookup-and-reference-functions/unique.md)
  Returns the distinct values from a range or array, with options to compare by rows or columns and to return values that occur exactly once.

- [UPPER](text-functions/upper.md)
  The `UPPER` function in Excel converts all lowercase letters in a given text string to their uppercase equivalents.

- [VALUE](text-functions/value.md)
  The `VALUE` function in Excel converts a text string that represents a number into an actual numeric value.

- [VALUETOTEXT](text-functions/value-to-text.md)
  The `VALUETOTEXT` function in Excel is used to convert a value into text.

- [VAR](statistical-functions/var.md)
  The `VAR` function in Excel is used to **estimate the variance based on a sample of data provided**.

- [VAR.P](statistical-functions/var__p.md)
  The `VAR.P` function in Excel is used to **calculate the variance of an entire population based on the data provided**.

- [VAR.S](statistical-functions/var__s.md)
  The `VAR.S` function in Excel is used to **calculate the variance of a sample** from a dataset.

- [VARA](statistical-functions/var_a.md)
  The `VARA` function in Excel is used to **calculate the variance of a sample**, evaluating both numeric and non-numeric data including logical values and text.

- [VARP](compatibility-functions/var_p.md)
  Returns the variance of an entire population. Provided for compatibility with earlier Excel versions.

- [VARPA](statistical-functions/var_pa.md)
  The `VARPA` function in Excel is used to **calculate the variance of an entire population considering all values, including numbers, text, and logical values**.

- [VDB](financial-functions/vdb.md)
  Returns the depreciation of an asset for a specified or partial period using the variable declining balance method.

- [VLOOKUP](table-functions/vlookup.md)
  The `VLOOKUP` function in Excel is used to search for a value in the first column of a table range and return a value in the same row from a specified column.

- [VSTACK](lookup-and-reference-functions/v_stack.md)
  Vertically stacks values or arrays into a single array, aligning columns and concatenating rows. Useful for combining ranges top to bottom.

- [WEEKDAY](date-time-functions/week_day.md)
  Returns the day of the week as a number, with return_type controlling the numbering scheme. Useful for scheduling and weekday-based logic.

- [WEEKNUM](date-time-functions/week_num.md)
  Returns the week number of a date, supporting different week numbering systems.

- [WEIBULL](statistical-functions/weibull.md)
  The `WEIBULL` function in Excel is used to **compute the Weibull probability density function or Weibull cumulative distribution function**, which is commonly used in reliability analysis and failure rate modeling.

- [WEIBULL.DIST](statistical-functions/weibull__dist.md)
  The `WEIBULL.DIST` function in Excel is used to **calculate the Weibull distribution**.

- [WORKDAY](date-time-functions/work-day.md)
  Returns the date a given number of working days before or after a start date, excluding weekends and optionally holidays.

- [WORKDAY.INTL](date-time-functions/workday-intl.md)
  Returns the date a given number of working days before or after a start date, with the ability to specify custom weekend days and optionally exclude holidays. Extends `WORKDAY` for non-standard work-week configurations.

- [WRAPCOLS](lookup-and-reference-functions/wrapcols.md)
  Wraps a row or column of values into a two-dimensional array by columns. Useful for reshaping data into multi-column layouts.

- [WRAPROWS](lookup-and-reference-functions/wraprows.md)
  Wraps a row or column of values into a two-dimensional array by rows. Useful for reshaping data into multi-row layouts.

- [XIRR](financial-functions/x_irr.md)
  Returns the internal rate of return for a schedule of cash flows that occur at irregular intervals.

- [XLOOKUP](table-functions/xlookup.md)
  > **Note**: The lookup_array must not contain functions.

- [XMATCH](table-functions/xmatch.md)
  The `XMATCH` function searches for a specified item in an array or range of cells, and then returns the relative position of that item.

- [XNPV](financial-functions/x_npv.md)
  Returns the net present value for a schedule of cash flows that occur at irregular intervals.

- [XOR](logical-functions/xor.md)
  Returns TRUE if an odd number of the arguments evaluate to TRUE; otherwise returns FALSE. Implements exclusive OR logic across multiple conditions.

- [YEAR](date-time-functions/year.md)
  Returns the year component of a date as a four-digit number.

- [YEARFRAC](date-time-functions/year-frac.md)
  Calculates the fraction of the year between two dates using a specified day-count basis.

- [YIELD](financial-functions/yield.md)
  Returns the yield of a security that pays periodic interest based on price, rate, and day count basis.

- [YIELD.DISC](financial-functions/yield_disc.md)
  Returns the annual yield of a discounted security, such as a Treasury bill, based on price and redemption value.

- [YIELD.MAT](financial-functions/yield_mat.md)
  Returns the annual yield of a security that pays interest at maturity based on price and day count basis.

- [Z.TEST](statistical-functions/z__test.md)
  The `Z.TEST` function in Excel is used to **calculate the one-tailed probability value of a z-test**.

- [ZTEST](statistical-functions/z_test.md)
  The `ZTEST` function in Excel is used to **calculate the one-tailed probability-value of a z-test**.