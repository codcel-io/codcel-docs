<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Mathematical Functions

This contains the list of mathematical functions that are currently supported by Codcel.


## Operators

### [+](./mathematical-functions/add.md)
Adds two or more numbers.

- **Example:** `=5 + 3` returns `8`.

### [-](./mathematical-functions/subtract.md)
Subtracts one number from another.

- **Example:** `=10 - 4` returns `6`.

### [*](./mathematical-functions/multiply.md)
Multiplies two or more numbers.

- **Example:** `=3 * 4` returns `12`.

### [/](./mathematical-functions/divide.md)
Divides one number by another.

- **Example:** `=10 / 2` returns `5`.

### [^](./mathematical-functions/exponentiation.md)
Raises a number to the power of another.

- **Example:** `=2 ^ 3` returns `8`.

## A

### [ABS](./mathematical-functions/abs.md)
Returns the absolute value of a number.

- **Example:** `=ABS(-10)` returns `10`.

### [ACOS](./mathematical-functions/acos.md)
Returns the arccosine of a number.

- **Example:** `=ACOS(0.5)` returns `1.047` (in radians).

### [ACOSH](./mathematical-functions/acosh.md)
Returns the inverse hyperbolic cosine of a number.

- **Example:** `=ACOSH(10)` returns `2.993`.
- 
### [ACOT](./mathematical-functions/acot.md)
Returns the arccotangent (inverse cotangent) of a number in radians.

- **Purpose:** Calculates the angle whose cotangent is the specified number.

- **Example Usage:** `=ACOT(1)` returns `0.785398163397448` (which is π/4 radians)

### [ACOTH](./mathematical-functions/acoth.md)
Returns the hyperbolic arccotangent (inverse hyperbolic cotangent) of a number.

- **Purpose:** Calculates the value whose hyperbolic cotangent is the specified number. The input must be greater than 1 or less than -1.

- **Example Usage:** `=ACOTH(2)` returns `0.549306144334055`

### [AGGREGATE](./mathematical-functions/aggregate.md)
Performs a specified aggregate function on a set of data, with options to ignore hidden rows, errors, and other
specified values.

- **Purpose:** Useful for performing aggregate calculations like sum, average, or count with additional options for
  exclusions.

- **Formula:** `AGGREGATE(function_num, options, ref1, [ref2], ...)`
  - `function_num` is the number corresponding to the aggregate function (e.g., 1 for AVERAGE, 2 for COUNT).
  - `options` is a number that determines which values to ignore:
    - `0` – No values are ignored.
    - `1` – Ignores hidden rows, errors, and nested SUBTOTAL or AGGREGATE functions.
    - `2` – Ignores hidden rows only.
    - `3` – Ignores errors only.
    - `4` – Ignores hidden rows and errors.
  - `ref1`, `ref2`, ... are the ranges of data for computation.

- **Example Usage:**
  - `=AGGREGATE(1, 4, A1:A10)` returns the average of the range `A1:A10`, ignoring hidden rows and errors.
  - `=AGGREGATE(9, 2, A1:A10)` returns the sum of the range `A1:A10`, ignoring hidden rows.


### [ARABIC](./mathematical-functions/arabic.md)
Converts a Roman numeral text string to its equivalent Arabic numeral (integer).

- **Purpose:** Transforms Roman numerals (e.g., "X", "IV") into their numeric representations (e.g., 10, 4).

- **Example Usage:** `=ARABIC("X")` returns - **Returns:** `10`


### [ASIN](./mathematical-functions/asin.md)
Returns the arcsine of a number.

- **Example:** `=ASIN(0.5)` returns `0.524` (in radians).

### [ASINH](./mathematical-functions/asinh.md)
Returns the inverse hyperbolic sine of a number.

- **Example:** `=ASINH(1)` returns `0.881`.

### [ATAN](./mathematical-functions/atan.md)
Returns the arctangent of a number.

- **Example:** `=ATAN(1)` returns `0.785` (in radians).

### [ATAN2](./mathematical-functions/atan2.md)
Returns the arctangent of the quotient of its arguments.

- **Example:** `=ATAN2(1, 1)` returns `0.785` (in radians).

### [ATANH](./mathematical-functions/atanh.md)
Returns the inverse hyperbolic tangent of a number.

- **Example:** `=ATANH(0.5)` returns `0.549`.

### [AVERAGE](./mathematical-functions/average.md)
Returns the average (arithmetic mean) of its arguments.

- **Example:** `=AVERAGE(2, 4, 6)` returns `4`.

## B

### [BASE](./mathematical-functions/base.md)
Converts a number into a text representation in a specified base (radix), ranging from base 2 to base 36.

- **Purpose:** Useful for converting numbers into binary, hexadecimal, or other numeral systems.

- **Example Usage:** `=BASE(10, 2)` returns `"1010"` (binary representation of 10)

### [BETADIST](./mathematical-functions/betadist.md)
Returns the beta cumulative distribution function.

- **Example:** `=BETADIST(0.5, 2, 2)` returns `0.75`.

### [BETA.DIST](./mathematical-functions/beta_dist.md)
Returns the beta distribution.

- **Example:** `=BETA.DIST(0.5, 2, 2, TRUE)` returns `0.75`.

## C

### [CEILING](./mathematical-functions/ceiling.md)
Rounds a number up to the nearest multiple of significance.

- **Example:** `=CEILING(4.2, 1)` returns `5`.

### [CEILING.MATH](./mathematical-functions/ceiling_math.md)
Rounds a number up to the nearest integer or to the nearest multiple of significance.

- **Example:** `=CEILING.MATH(4.2, 2)` returns `6`.

### [CEILING.PRECISE](./mathematical-functions/ceiling_precise.md)
Always rounds numbers up, regardless of the sign.

- **Example:** `=CEILING.PRECISE(-4.2, 2)` returns `-4`.

### [COMBIN](./mathematical-functions/combin.md)
Returns the number of combinations for a given number of items, selecting a subset without regard to order.

- **Purpose:** Useful for calculating combinations in probability and statistics.

- **Formula:** `COMBIN(n, k)`
    - `n` is the total number of items.
    - `k` is the number of items to choose.

- **Example Usage:** `=COMBIN(5, 2)` returns `10` (the number of ways to choose 2 items from 5).

### [COMBINA](./mathematical-functions/combina.md)
Returns the number of combinations for a given number of items, allowing for repetitions.

- **Purpose:** Useful for calculating combinations in probability and statistics when repetition of items is allowed.

- **Formula:** `COMBINA(n, k)`
    - `n` is the total number of items.
    - `k` is the number of items to choose.

- **Example Usage:** `=COMBINA(5, 2)` returns `15` (the number of ways to choose 2 items from 5 with repetition).

### [CONVERT](./mathematical-functions/convert.md)
Converts a number from one measurement system to another.

- **Example:** `=CONVERT(1, "lbm", "kg")` returns `0.453592`.

### [COS](./mathematical-functions/cos.md)
Returns the cosine of an angle.

- **Example:** `=COS(PI())` returns `-1`.

### [COT](./mathematical-functions/cot.md)
Returns the cotangent of an angle specified in radians.

- **Purpose:** Calculates the cotangent, which is the reciprocal of the tangent (`1 / TAN(angle)`).

- **Formula:** `COT(angle)`
    - `angle` is the angle in radians.

- **Example Usage:** `=COT(PI()/4)` returns `1` (cotangent of 45° or π/4 radians).

### [COTH](./mathematical-functions/coth.md)
Returns the hyperbolic cotangent of a number.

- **Purpose:** Calculates the hyperbolic cotangent, which is the reciprocal of the hyperbolic tangent (`1 / TANH(number)`).

- **Formula:** `COTH(number)`
  - `number` is the value for which to calculate the hyperbolic cotangent.

- **Example Usage:** `=COTH(2)` returns `1.03731472072755`

### [CSC](./mathematical-functions/csc.md)
Returns the cosecant of an angle specified in radians.

- **Purpose:** Calculates the cosecant, which is the reciprocal of the sine (`1 / SIN(angle)`).

- **Formula:** `CSC(angle)`
  - `angle` is the angle in radians.

- **Example Usage:** `=CSC(PI()/2)` returns `1` (cosecant of 90° or π/2 radians).

### [CSCH](./mathematical-functions/csch.md)
Returns the hyperbolic cosecant of a number.

- **Purpose:** Calculates the hyperbolic cosecant, which is the reciprocal of the hyperbolic sine (`1 / SINH(number)`).

- **Formula:** `CSCH(number)`
  - `number` is the value for which to calculate the hyperbolic cosecant.

- **Example Usage:** `=CSCH(2)` returns `0.275720564771784`

### [COUNTIF](./conditional-functions/count_if.md)
Counts the number of cells within a range that meet a given condition.

- **Purpose:** Useful for conditional counting in a range of cells based on specific criteria.

- **Formula:** `COUNTIF(range, criteria)`
  - `range` is the group of cells to evaluate.
  - `criteria` is the condition to count the cells that meet it. This can be a number, expression, cell reference, or
    text.

- **Example Usage:**
  - `=COUNTIF(A1:A10, ">5")` counts the cells in the range `A1:A10` with values greater than `5`.
  - `=COUNTIF(A1:A10, "apple")` counts the occurrences of the text "apple" in the range `A1:A10`.

## D

### [DECIMAL](./mathematical-functions/decimal.md)
Converts a text representation of a number in a given base (radix) into its equivalent decimal (base 10) number.

- **Purpose:** Useful for converting numbers from binary, hexadecimal, or other numeral systems into decimal form.

- **Formula:** `DECIMAL(text, radix)`
  - `text` is the number in text format (e.g., "101" for binary).
  - `radix` is the base of the number system (e.g., 2 for binary, 16 for hexadecimal).

- **Example Usage:** `=DECIMAL("101", 2)` returns `5` (binary "101" converted to decimal).

### [DEGREES](./mathematical-functions/degrees.md)
Converts radians to degrees.

- **Example:** `=DEGREES(PI())` returns `180`.

## E

### [EVEN](./mathematical-functions/even.md)
Rounds a number up to the nearest even integer.

- **Example:** `=EVEN(3.2)` returns `4`.

### [EXP](./mathematical-functions/exp.md)
Returns the value of the mathematical constant **e** raised to the power of a given number.

- **Purpose:** Useful for exponential growth calculations and mathematical equations involving the natural exponential function.

- **Formula:** `EXP(number)`
  - `number` is the exponent to raise **e** to.

- **Example Usage:** `=EXP(1)` returns `2.71828182845904` (value of **e** to the power of 1).

## F

### [FACT](./mathematical-functions/fact.md)
Returns the factorial of a number.

- **Example:** `=FACT(5)` returns `120`.

### [FACTDOUBLE](./mathematical-functions/fact_double.md)
Returns the double factorial of a number. The double factorial of a non-negative integer is the product of all integers from 1 to the number that have the same parity (odd or even) as the number.

- **Purpose:** Useful in advanced mathematical and combinatorial calculations.

- **Formula:** `FACTDOUBLE(number)`
  - `number` is the non-negative integer whose double factorial is calculated.

- **Example Usage:** `=FACTDOUBLE(6)` returns `48` (calculated as `6 × 4 × 2`).

### [FLOOR](./mathematical-functions/floor.md)
Rounds a number down, toward zero, to the nearest multiple of a specified significance.

- **Purpose:** Useful for rounding numbers to a lower boundary, such as currency values or predefined intervals.

- **Formula:** `FLOOR(number, significance)`
  - `number` is the value to be rounded down.
  - `significance` is the multiple to which the number is rounded.

- **Example Usage:** `=FLOOR(10.7, 2)` returns  `10` (rounded down to the nearest multiple of 2).

### [FLOOR.MATH](./mathematical-functions/floor_math.md)
Rounds a number down to the nearest integer or to the nearest specified multiple, regardless of the number's sign.

- **Purpose:** Useful for consistent rounding down in mathematical calculations, including handling both positive and negative numbers with optional direction control.

- **Formula:** `FLOOR.MATH(number, significance, mode)`
  - `number` is the value to be rounded down.
  - `significance` (optional) is the multiple to which the number is rounded. Default is `1`.
  - `mode` (optional) specifies the rounding direction for negative numbers. Default is `0` (round away from zero).

- **Example Usage:** `=FLOOR.MATH(10.7)` returns `10` (rounded down to the nearest integer).

### [FLOOR.PRECISE](./mathematical-functions/floor_precise.md)
Rounds a number down to the nearest integer or specified multiple, regardless of the number's sign. Always rounds toward zero for negative numbers.

- **Purpose:** Useful for precise rounding that is consistent across both positive and negative numbers without considering a mode for direction.

- **Formula:** `FLOOR.PRECISE(number, significance)`
  - `number` is the value to be rounded down.
  - `significance` (optional) is the multiple to which the number is rounded. Default is `1`.

- **Example Usage:** `=FLOOR.PRECISE(10.7)` returns `10` (rounded down to the nearest integer).

## G

### [GCD](./mathematical-functions/gcd.md)
Calculates the greatest common divisor (GCD) of two or more integers. The GCD is the largest integer that can evenly divide all the given numbers without leaving a remainder.

- **Purpose:** Useful for simplifying fractions, reducing ratios, or finding common factors in mathematical and computational tasks.

- **Formula:** `GCD(number1, [number2], ...)`
  - `number1` is the first number for which to calculate the GCD.
  - `number2` (optional) is an additional number or series of numbers. Up to 255 numbers can be included.

- **Example Usage:** `=GCD(28, 35, 42)` returns `7` (the largest number that divides all three values).


## I

### [IF](./conditional-functions/if.md)
Performs a logical test and returns different values based on the result.

- **Example:** `=IF(A1 > 10, "Yes", "No")`.

### [IFS](./conditional-functions/ifs.md)
Tests multiple conditions and returns a value corresponding to the first TRUE condition.

- **Example:** `=IFS(A1 > 10, "High", A1 > 5, "Medium", TRUE, "Low")`.

### [IFERROR](./conditional-functions/if_error.md)
Returns a value if there is no error; otherwise, returns an alternative value.

- **Example:** `=IFERROR(A1/B1, 0)`.

### [INT](./mathematical-functions/int.md)
Rounds a number down to the nearest integer.

- **Example:** `=INT(4.8)` returns `4`.


### [ISNUMBER](./mathematical-functions/is_number.md)
Checks whether a value is a number and returns TRUE if it is, or FALSE otherwise.

- **Example:** `=ISNUMBER(123)` returns `TRUE`.
               `=ISNUMBER("123")` returns `FALSE`.

### [ISO.CEILING](./mathematical-functions/iso_ceiling.md)
Rounds a number up to the nearest multiple of a specified significance, following the ISO standard for rounding. This ensures consistent behavior for both positive and negative numbers.

- **Purpose:** Useful for rounding values to a specified interval, such as standardizing numbers for reporting, aligning data to increments, or ensuring consistent rounding in mathematical and financial calculations.

- **Formula:** `ISO.CEILING(number, [significance])`
  - `number` is the value to be rounded.
  - `significance` (optional) is the multiple to which the `number` is rounded. If omitted, it defaults to `1`.

- **Example Usage:**
  - `=ISO.CEILING(4.3, 2)` returns `6` (the nearest multiple of 2 greater than or equal to 4.3).
  - `=ISO.CEILING(-4.3, 2)` returns `-4` (the nearest multiple of 2 greater than or equal to -4.3, ensuring consistent handling of negative values).

## L

### [LCM](./mathematical-functions/lcm.md)   
Calculates the least common multiple of two or more integers. The least common multiple is the smallest positive integer that is a multiple of all the specified numbers.

- **Purpose:** Useful in problems involving fractions, ratios, or periodic events, such as finding a common cycle in schedules or aligning repeating patterns.

- **Formula:** `LCM(number1, [number2], …)`
  - `number1, number2, …` are the integers for which to calculate the least common multiple. At least one value is required.

- **Example Usage:**
  - `=LCM(4, 6)` returns `12` (the smallest number divisible by both 4 and 6).
  - `=LCM(3, 5, 7)` returns `105` (the smallest number divisible by 3, 5, and 7).

### [LOG](./mathematical-functions/log.md)
Calculates the logarithm of a given positive number for a specified base. The logarithm is the power to which the base must be raised to produce the given number.

- **Purpose:** Useful in scientific, engineering, and financial tasks involving logarithmic calculations, such as analyzing growth, scaling data, or solving exponential equations.

- **Formula:** `LOG(number, [base])`
  - `number` is the positive numeric value for which to calculate the logarithm.
  - `base` (optional) is the base of the logarithm. If omitted, it defaults to 10.

- **Example Usage:**
  - `=LOG(100, 10)` returns `2` (as `10² = 100`).
  - `=LOG(16, 2)` returns `4` (as `2⁴ = 16`).
  - `=LOG(1000)` returns `3` (default base 10: `10³ = 1000`).

### [LOG10](./mathematical-functions/log10.md)
Calculates the base-10 logarithm of a given positive number. The result is the power to which 10 must be raised to equal the specified number.

- **Purpose:** Useful in scientific, engineering, and financial tasks that involve logarithmic calculations, such as growth rates, decibel levels, or pH values.

- **Formula:** `LOG10(number)`
  - `number` is the positive numeric value for which to calculate the base-10 logarithm.

- **Example Usage:** `=LOG10(1000)` returns `3` (as `10^3 = 1000`).


### [LN](./mathematical-functions/ln.md)
Calculates the natural logarithm of a given positive number. The natural logarithm is the logarithm to the base *e* (Euler's number, approximately 2.718).

- **Purpose:** Useful in mathematical, scientific, and financial applications, such as calculating growth rates, decay, or solving equations involving exponential functions.

- **Formula:** `LN(number)`
  - `number` is the positive numeric value for which to calculate the natural logarithm.

- **Example Usage:**
  - `=LN(7.389)` returns `2` (as *e² ≈ 7.389`).
  - `=LN(1)` returns `0` (as *e⁰ = 1`).

## M

### [MAX](./mathematical-functions/max.md)
Returns the largest value in a set of values.

- **Example:** `=MAX(1, 2, 3)` returns `3`.

### [MDETERM](./mathematical-functions/m_determ.md)
Calculates the determinant of a square matrix provided as an array or cell range. The determinant is a scalar value that is a key property of matrices, useful in linear algebra for solving systems of equations, finding inverses, and analyzing transformations.

- **Purpose:** Useful for mathematical, engineering, and statistical tasks involving matrix operations, such as solving linear systems or transformations.

- **Formula:** `MDETERM(array)`
  - `array` is a square matrix (an array or cell range with equal rows and columns).

- **Example Usage:** `=MDETERM({2, 3; 4, 5})` returns `-2` (as `(2*5) - (3*4) = -2`).

### [MIN](./mathematical-functions/min.md)
Returns the smallest value in a set of values.

- **Example:** `=MIN(1, 2, 3)` returns `1`.

### [MINVERSE](./mathematical-functions/m_inverse.md)
Calculates the inverse of a square matrix provided as an array or cell range. The inverse matrix, when multiplied by the original matrix, results in an identity matrix.

- **Purpose:** Useful for solving systems of linear equations, performing linear algebraic operations, and analyzing matrix transformations.

- **Formula:** `MINVERSE(array)`
  - `array` is a square matrix (an array or cell range with equal rows and columns).

- **Example Usage:** `=MINVERSE({1, 2; 3, 4})` returns `{ -2, 1; 1.5, -0.5 }`. (The inverse of the input matrix).

### [MMULT](./mathematical-functions/m_mult.md)
Calculates the matrix product of two arrays. The resulting matrix has dimensions based on the number of rows in the first array and the number of columns in the second array.

- **Purpose:** Useful for multiplying matrices in linear algebra, solving systems of equations, and performing complex transformations.

- **Formula:** `MMULT(array1, array2)`
  - `array1` is the first matrix (array or cell range).
  - `array2` is the second matrix (array or cell range). The number of columns in `array1` must match the number of rows in `array2`.

- **Example Usage:** `=MMULT({1, 2; 3, 4}, {2; 1})` returns `{4; 10}` (as the matrix product of the inputs).

### [MOD](./mathematical-functions/mod.md)
Returns the remainder after a number is divided by a divisor.

- **Example:** `=MOD(10, 3)` returns `1`.

### [MROUND](./mathematical-functions/mround.md)
Rounds a number to the nearest multiple of a specified value.

- **Purpose:** Useful for rounding values to the nearest desired multiple, such as rounding to the nearest 5, 10, or any custom interval.

- **Formula:** `MROUND(number, multiple)`
  - `number` is the value you want to round.
  - `multiple` is the multiple to which you want to round the `number`. It must be a positive or negative numeric value.

- **Example Usage:** `=MROUND(23, 5)` returns `25` (rounds 23 to the nearest multiple of 5).

### [MULTINOMIAL](./mathematical-functions/multinomial.md)  
Calculates the ratio of the factorial of a sum of values to the product of the factorials of those values.

- **Purpose:** Useful for probability, statistics, and combinatorics, particularly when working with multinomial distributions.

- **Formula:** `MULTINOMIAL(number1, [number2], ...)`
  - `number1, number2, ...` are the numbers you want to include in the calculation. These must be non-negative values.

- **Example Usage:** `=MULTINOMIAL(2, 3, 4)` returns `1260` (calculated as `(2+3+4)! / (2! * 3! * 4!)`).

### [MUNIT](./mathematical-functions/m_unit.md)
Generates a unit matrix (identity matrix) of a specified dimension.

- **Purpose:** Useful for creating identity matrices, which are square matrices with ones on the main diagonal and zeros elsewhere. Identity matrices are commonly used in linear algebra and matrix operations.

- **Formula:** `MUNIT(dimension)`
  - `dimension` is the number of rows and columns in the identity matrix. It must be a positive integer.

- **Example Usage:** `=MUNIT(3)` returns the following 3x3 identity matrix:
  ```
  1  0  0
  0  1  0
  0  0  1


## N

### [NOT](./mathematical-functions/not.md)
Reverses the logic of its argument.

- **Example:** `=NOT(TRUE)` returns `FALSE`.

## O

### [ODD](./mathematical-functions/odd.md)
Rounds a number up to the nearest odd integer.

- **Purpose:** Ensures a number is rounded up to the next odd integer, regardless of whether the input is positive or negative.

- **Formula:** `ODD(number)`
  - `number` is the value you want to round up to the nearest odd integer.
  - If `number` is already an odd integer, no rounding occurs.

- **Example Usage:**
  - `=ODD(3.2)` returns `5` (rounds up 3.2 to the next odd integer).
  - `=ODD(-2.5)` returns `-3` (rounds up -2.5 to the next odd integer in the negative direction).

## P

### [PI](./mathematical-functions/pi.md)
Returns the mathematical constant π (pi), approximately `3.14159265358979`.

- **Example:** `=PI()` returns `3.14159265358979``

### [POWER](./mathematical-functions/power.md)
Raises a number to a specified power.

- **Purpose:** Calculates the result of a number raised to a given exponent.

- **Formula:** `POWER(number, power)`
  - `number` is the base value to be raised to a power.
  - `power` is the exponent to which the base number is raised.

- **Example Usage:**
  - `=POWER(2, 3)` returns `8` (2 raised to the power of 3).
  - `=POWER(5, 2)` returns `25` (5 squared).
  - `=POWER(9, 0.5)` returns `3` (the square root of 9).

### [PRODUCT](./mathematical-functions/product.md)
Multiplies all the numbers given as arguments.

- **Example:** `=PRODUCT(2, 3, 4)` returns `24`.

## Q

### [QUOTIENT](./mathematical-functions/quotient.md)
Returns the integer portion of a division.

- **Purpose:** Calculates the integer result of dividing two numbers, ignoring the remainder.

- **Formula:** `QUOTIENT(numerator, denominator)`
  - `numerator` is the number to be divided.
  - `denominator` is the number by which the numerator is divided.

- **Example Usage:**
  - `=QUOTIENT(10, 3)` returns `3` (10 divided by 3 equals 3 with a remainder of 1).
  - `=QUOTIENT(7, 2)` returns `3` (7 divided by 2 equals 3 with a remainder of 1).
  - `=QUOTIENT(-10, 3)` returns `-3` (integer division handles negative numbers).


## R

### [RADIANS](./mathematical-functions/radians.md)
Converts degrees to radians.

- **Example:** `=RADIANS(180)` returns `PI()`.

### [RAND](./mathematical-functions/rand.md)
Generates a random number between 0 and 1.

- **Example:** `=RAND()` returns a random number like `0.374`.

### [RANDARRAY](./mathematical-functions/rand_array.md)
Generates an array of random numbers.

- **Purpose:** Creates an array of random numbers within a specified range, optionally allowing for whole numbers or
  decimals, and defining the dimensions of the array. Useful for simulations, statistical analysis, and testing
  scenarios.

- **Formula:** `RANDARRAY(rows, columns, [min], [max], [whole_number])`
  - `rows` is the number of rows in the resulting random array. Must be a positive integer.
  - `columns` is the number of columns in the resulting random array. Must be a positive integer.
  - `min` (optional) is the minimum value for the generated numbers. Defaults to `0` if omitted.
  - `max` (optional) is the maximum value for the generated numbers. Defaults to `1` if omitted.
  - `whole_number` (optional) is a logical value that determines the type of numbers generated:
    - `TRUE` generates whole numbers.
    - `FALSE` (default) generates decimal numbers.

- **Example Usage:**
  - `=RANDARRAY(2, 3)` returns a 2x3 array of random decimal numbers between `0` and `1`.
  - `=RANDARRAY(3, 3, 1, 10, TRUE)` returns a 3x3 array of random whole numbers between `1` and `10`.
  - `=RANDARRAY(4, 2, -5, 5, FALSE)` returns a 4x2 array of random decimal numbers between `-5` and `5`.

### [RANDBETWEEN](./mathematical-functions/rand_between.md)
Generates a random integer between two specified values.

- **Purpose:** Calculates a random integer between a given minimum and maximum value, inclusive.

- **Formula:** `RANDBETWEEN(min, max)`
  - `min` is the lower bound of the random integer range.
  - `max` is the upper bound of the random integer range.

- **Example Usage:**
  - `=RANDBETWEEN(1, 10)` returns a random integer between `1` and `10`.
  - `=RANDBETWEEN(-5, 5)` returns a random integer between `-5` and `5`.
  - `=RANDBETWEEN(100, 200)` returns a random integer between `100` and `200`.

### [ROMAN](./mathematical-functions/roman.md)
Converts an Arabic numeral to a Roman numeral.

- **Purpose:** Converts a given number into its Roman numeral representation.

- **Formula:** `ROMAN(number, [form])`
  - `number` is the Arabic numeral you want to convert (must be between 1 and 3999).
  - `form` (optional) specifies the type of Roman numeral to use:
    - `0` or omitted: Classic format (e.g., IV for 4).
    - `1-4`: Specifies progressively simplified formats (e.g., IIII instead of IV).

- **Example Usage:**
  - `=ROMAN(499)` returns `CDXCIX` (classic format).

### [ROUND](./mathematical-functions/round.md)
Rounds a number to a specified number of digits.

- **Example:** `=ROUND(2.15, 1)` returns `2.2`.

### [ROUNDDOWN](./mathematical-functions/round_down.md)
Rounds a number down toward zero.

- **Example:** `=ROUNDDOWN(2.15, 1)` returns `2.1`.

### [ROUNDUP](./mathematical-functions/round_up.md)
Rounds a number up, away from zero.

- **Example:** `=ROUNDUP(2.15, 1)` returns `2.2`.

## S

### [SEC](./mathematical-functions/sec.md)
Returns the secant of an angle.

- **Purpose:** Calculates the secant of a given angle in radians.

- **Formula:** `SEC(number)`
  - `number` is the angle in radians for which you want the secant.

- **Example Usage:**
  - `=SEC(PI()/3)` returns `2` (secant of 60 degrees or \( \pi/3 \) radians).
  - `=SEC(PI()/4)` returns approximately `1.414213` (secant of 45 degrees or \( \pi/4 \) radians).
  - `=SEC(0)` returns `1` (secant of 0 radians).

### [SECH](./mathematical-functions/sech.md)
Returns the hyperbolic secant of a given angle.

- **Purpose:** Calculates the hyperbolic secant of an angle provided in radians.

- **Formula:** SECH(number)
  - **number** is the angle in radians for which you want the hyperbolic secant.

- **Example Usage:**
  - =SECH(0) returns 1 (the hyperbolic secant of 0 radians is 1).
  - =SECH(1) returns approximately 0.648 (the hyperbolic secant of 1 radian).
  - =SECH(-1) returns approximately 0.648 (the hyperbolic secant of -1 radian).

### [SEQUENCE](./mathematical-functions/sequence.md)
Generates a list of sequential numbers in an array.

- **Purpose:** Creates an array of sequential numbers with configurable rows, columns, start value, and step increment.

- **Formula:** `SEQUENCE(rows, [columns], [start], [step])`
  - `rows` is the number of rows to fill with sequential numbers.
  - `columns` (optional) is the number of columns to fill. Defaults to 1.
  - `start` (optional) is the first number in the sequence. Defaults to 1.
  - `step` (optional) is the increment for each subsequent number. Defaults to 1.

- **Example Usage:**
  - `=SEQUENCE(4)` generates an array with four rows filled with the numbers 1 to 4.
  - `=SEQUENCE(3, 2)` creates a 3x2 array: {{1, 2}, {3, 4}, {5, 6}}.
  - `=SEQUENCE(5, 1, 10, 2)` produces a column of five numbers starting from 10, incrementing by 2: {10, 12, 14, 16, 18}.

### [SERIESSUM](./mathematical-functions/series_sum.md)
Returns the sum of a power series based on the provided coefficients and exponents.

- **Purpose:** Calculates the result of a power series expansion using the given x value, coefficients, and exponents.

- **Formula:** SERIESSUM(x, n, m, coefficients)
  - **x** is the input value to be used in the power series.
  - **n** is the initial power to which x is raised.
  - **m** is the increment by which the power increases in each term.
  - **coefficients** is an array of numbers representing the coefficients for each term in the series.

- **Example Usage:**
  - =SERIESSUM(2, 1, 1, {1, 2, 3}) returns 2^1 \* 1 + 2^2 \* 2 + 2^3 \* 3 = 2 + 8 + 24 = 34.
  - =SERIESSUM(3, 0, 2, {4, 5, 6}) returns 3^0 \* 4 + 3^2 \* 5 + 3^4 \* 6 = 4 + 45 + 486 = 535.
  - =SERIESSUM(1, 1, 1, {1, 1, 1}) returns 1^1 \* 1 + 1^2 \* 1 + 1^3 \* 1 = 1 + 1 + 1 = 3.

### [SIGN](./mathematical-functions/sign.md)
Returns the sign of a number.

- **Purpose:** Determines whether a number is positive, negative, or zero and returns the corresponding sign indicator.

- **Formula:** SIGN(number)
  - number is the value for which the sign will be determined.

- **Example Usage:**
  - =SIGN(10) returns 1 (positive number).
  - =SIGN(-7) returns -1 (negative number).
  - =SIGN(0) returns 0 (zero has no sign).

### [SIN](./mathematical-functions/sin.md)
Returns the sine of a given angle.

- **Purpose:** Calculates the sine of an angle provided in radians.

- **Formula:** SIN(angle)
  - angle is the angle in radians for which you want the sine.

- **Example Usage:**
  - =SIN(PI()/2) returns 1 (sine of 90 degrees or \( \frac{\pi}{2} \) radians).
  - =SIN(0) returns 0 (sine of 0 radians).
  - =SIN(PI()) returns approximately 0 (sine of 180 degrees or \( \pi \) radians).

### [SINH](./mathematical-functions/sinh.md)
Returns the hyperbolic sine of a number.

- **Purpose:** Calculates the hyperbolic sine of a given number.

- **Formula:** SINH(number)
  - number is the value for which you want to calculate the hyperbolic sine.

- **Example Usage:**
  - =SINH(0) returns 0 (the hyperbolic sine of 0 is 0).
  - =SINH(1) returns approximately 1.175201 (the hyperbolic sine of 1).
  - =SINH(-2) returns approximately -3.626860 (the hyperbolic sine of -2).

### [SQRT](./mathematical-functions/sqrt.md)
Calculates the square root of a number.

- **Purpose:** Returns the positive square root of a given number.

- **Formula:** SQRT(number)
  - number is the value for which you want the square root. It must be a non-negative number.

- **Example Usage:**
  - =SQRT(16) returns 4 (the square root of 16 is 4).
  - =SQRT(25) returns 5 (the square root of 25 is 5).
  - =SQRT(0) returns 0 (the square root of 0 is 0).

### [SQRTPI](./mathematical-functions/sqrt_pi.md)
Returns the square root of a number multiplied by pi (π).

- **Purpose:** Computes the square root of the product of a given number and π (pi).

- **Formula:** SQRTPI(number)
  - number is the value to be multiplied by π before taking the square root.

- **Example Usage:**
  - =SQRTPI(1) returns 1.772453 (the square root of π).
  - =SQRTPI(2) returns 2.506628 (the square root of 2π).
  - =SQRTPI(0) returns 0 (the square root of 0π is 0).

### [SUBTOTAL](./mathematical-functions/sub_total.md)
Returns a subtotal in a list or database.

- **Purpose:** Performs a calculation on a range of data, allowing for filtered or hidden data to be included or excluded based on the function used.

- **Formula:** SUBTOTAL(function_num, ref1, [ref2], ...)
  - **function_num** specifies the type of subtotal to be performed (e.g., AVERAGE, COUNT, SUM, etc.).
    - Values 1-11 include hidden rows.
    - Values 101-111 ignore hidden rows.
  - **ref1, ref2, ...** are the ranges or references on which the calculation is performed.

- **Example Usage:**
  - =SUBTOTAL(9, A1:A10) returns the sum of the range A1:A10, including hidden rows.
  - =SUBTOTAL(109, A1:A10) returns the sum of the range A1:A10, excluding hidden rows.
  - =SUBTOTAL(1, A1:A10) calculates the average of the range A1:A10, including hidden rows.

### [SUM](./mathematical-functions/sum.md)
Adds all the numbers in a range of cells.

- **Example:** `=SUM(1, 2, 3)` returns `6`.

### [SUMIF](./conditional-functions/sum_if.md)
Returns the sum of cells that meet a specified condition.

- **Purpose:** Adds the values in a range that meet a specified condition or criteria.

- **Formula:** SUMIF(range, criteria, [sum_range])
  - **range** is the range of cells that you want to evaluate against the criteria.
  - **criteria** is the condition that must be met. It can be a number, expression, cell reference, or text.
  - **sum_range** is the actual set of cells to sum. If omitted, the cells in the range are summed.

- **Example Usage:**
  - =SUMIF(A1:A10, ">5") returns the sum of all values in the range A1:A10 that are greater than 5.
  - =SUMIF(A1:A10, "apple", B1:B10) sums the values from B1:B10 where corresponding cells in A1:A10 are equal to "
    apple".
  - =SUMIF(A1:A10, "<=3") returns the sum of all values in the range A1:A10 that are less than or equal to 3.

### [SUMIFS](./mathematical-functions/sum_ifs.md)
Returns the sum of cells that meet multiple specified conditions.

- **Purpose:** Adds the values in a range that meet multiple criteria.

- **Formula:** SUMIFS(sum_range, criteria_range1, criteria1, [criteria_range2, criteria2], ...)
  - **sum_range** is the actual set of cells to sum.
  - **criteria_range1, criteria_range2, ...** are the ranges to be evaluated against the criteria.
  - **criteria1, criteria2, ...** are the conditions that must be met in the corresponding criteria ranges.

- **Example Usage:**
  - `=SUMIFS(B1:B10, A1:A10, ">5")` returns the sum of values in `B1:B10` where the corresponding cells in `A1:A10` are
    greater than 5.
  - `=SUMIFS(B1:B10, A1:A10, "apple", C1:C10, "<10")` returns the sum of values in `B1:B10` where the corresponding
    cells in `A1:A10` are "apple" **and** the corresponding cells in `C1:C10` are less than 10.
  - `=SUMIFS(B1:B10, A1:A10, ">=3", C1:C10, "<5")` returns the sum of values in `B1:B10` where the corresponding cells
    in `A1:A10` are greater than or equal to 3 **and** the corresponding cells in `C1:C10` are less than 5.

### [SUMPRODUCT](./mathematical-functions/sum_product.md)
Returns the sum of the products of corresponding ranges or arrays.

- **Purpose:** Multiplies corresponding elements in the given arrays and returns the sum of those products.

- **Formula:** SUMPRODUCT(array1, [array2], ...)
  - **array1, array2, ...** are the ranges or arrays to be multiplied. All arrays must have the same dimensions;
    otherwise, an error is returned.

- **Example Usage:**
  - `=SUMPRODUCT(A1:A3, B1:B3)` multiplies each pair of corresponding elements from the ranges `A1:A3` and `B1:B3`, then
    sums the results:
    - Formula breaks down as: `(A1*B1) + (A2*B2) + (A3*B3)`.
  - `=SUMPRODUCT(A1:A3, B1:B3, C1:C3)` calculates the product of corresponding elements across three ranges (`A1*A2*C1`,
    `A2*B2*C2`, etc.) and sums the results.
  - `=SUMPRODUCT(A1:A3^2, B1:B3)` squares each element in `A1:A3`, then multiplies with the corresponding elements in
    `B1:B3`, and sums up the results.

### [SUMSQ](./mathematical-functions/sum_sq.md)
Returns the sum of the squares of a series of numbers and/or cells.

- **Purpose:** Calculates the sum of the squares of the provided values or cell ranges.

- **Formula:** SUMSQ(value1, [value2], ...)
  - **value1, value2, ...** are numbers, arrays, or ranges that you want to square and then sum.

- **Example Usage:**
  - `=SUMSQ(3, 4)` returns `25` (since `3^2 + 4^2 = 9 + 16 = 25`).
  - `=SUMSQ(A1:A3)` squares each value in `A1:A3` and sums the results.
  - `=SUMSQ(2, 5, 6)` returns `65` (since `2^2 + 5^2 + 6^2 = 4 + 25 + 36 = 65`).

### [SUMX2MY2](./mathematical-functions/sum_x2my2.md)
Calculates the sum of differences between the squares of numbers in two corresponding arrays.

- **Purpose:** For two arrays of the same size, this function computes the sum of
  `(x1^2 - y1^2) + (x2^2 - y2^2) + ... + (xn^2 - yn^2)`.

- **Formula:** `SUMX2MY2(array_x, array_y)`
  - **array_x, array_y** are the two arrays or ranges with the same number of elements to be used in the calculation.

- **Example Usage:**
  - `=SUMX2MY2(A1:A3, B1:B3)` computes the sum of squared differences between corresponding elements in ranges `A1:A3`
    and `B1:B3`:
    - Formula breaks down as: `(A1^2 - B1^2) + (A2^2 - B2^2) + (A3^2 - B3^2)`.
  - `=SUMX2MY2({2, 3, 4}, {1, 5, 2})` performs `(2^2 - 1^2) + (3^2 - 5^2) + (4^2 - 2^2)` and returns `-3`.

### [SUMX2PY2](./mathematical-functions/sum_x2py2.md)
Calculates the sum of the sums of the squares of numbers in two corresponding arrays.

- **Purpose:** For two arrays of the same size, this function computes the sum of
  `(x1^2 + y1^2) + (x2^2 + y2^2) + ... + (xn^2 + yn^2)`.

- **Formula:** `SUMX2PY2(array_x, array_y)`
  - **array_x, array_y** are the two arrays or ranges with the same number of elements to be used in the calculation.

- **Example Usage:**
  - `=SUMX2PY2(A1:A3, B1:B3)` computes the sum of squared sums between corresponding elements in ranges `A1:A3` and
    `B1:B3`:
    - Formula breaks down as: `(A1^2 + B1^2) + (A2^2 + B2^2) + (A3^2 + B3^2)`.
  - `=SUMX2PY2({2, 3, 4}, {1, 5, 2})` performs `(2^2 + 1^2) + (3^2 + 5^2) + (4^2 + 2^2)` and returns `59`.

### [SUMXMY2](./mathematical-functions/sum_xmy2.md)
Calculates the sum of the squares of differences of numbers in two corresponding arrays.

- **Purpose:** For two arrays of the same size, this function computes the sum of
  `(x1 - y1)^2 + (x2 - y2)^2 + ... + (xn - yn)^2`.

- **Formula:** `SUMXMY2(array_x, array_y)`
  - **array_x, array_y** are the two arrays or ranges with the same number of elements to be used in the calculation.

- **Example Usage:**
  - `=SUMXMY2(A1:A3, B1:B3)` computes the sum of squared differences for corresponding elements in ranges `A1:A3` and
    `B1:B3`:
    - Formula breaks down as: `(A1 - B1)^2 + (A2 - B2)^2 + (A3 - B3)^2`.
  - `=SUMXMY2({2, 3, 4}, {1, 5, 2})` performs `(2 - 1)^2 + (3 - 5)^2 + (4 - 2)^2` and returns `14`.

## T

### [TAN](./mathematical-functions/tan.md)
Returns the tangent of an angle.

- **Purpose:** Calculates the tangent of a given angle expressed in radians.

- **Formula:** TAN(angle)
  - angle is the angle in radians for which you want the tangent.

- **Example Usage:**
  - =TAN(PI()/4) returns 1 (the tangent of 45 degrees, or \u03c0/4 radians).
  - =TAN(0) returns 0 (the tangent of 0 radians).
  - =TAN(PI()/3) returns 1.732 (the tangent of 60 degrees, or \u03c0/3 radians).

### [TANH](./mathematical-functions/tanh.md)
Returns the hyperbolic tangent of a number.

- **Purpose:** Computes the hyperbolic tangent of a given number, which is a mathematical function used in various fields including engineering and statistics.

- **Formula:** TANH(number)
  - number is the value for which you want the hyperbolic tangent.

- **Example Usage:**
  - =TANH(0) returns 0 (the hyperbolic tangent of 0 is 0).
  - =TANH(1) returns 0.761594 (the hyperbolic tangent of 1).
  - =TANH(-1) returns -0.761594 (the hyperbolic tangent of -1).

### [TRUNC](./mathematical-functions/trunc.md)
Truncates a number to an integer by removing the fractional part.

- **Example:** `=TRUNC(4.9)` returns `4`.