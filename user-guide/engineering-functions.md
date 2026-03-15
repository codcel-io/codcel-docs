<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Engineering Functions

This contains the list of engineering functions that are currently supported by Codcel.

## B

### [BESSELI](./engineering-functions/bessel_i.md)
Calculates the modified Bessel function of the first kind.

- **Purpose:** This function is used in engineering and mathematical computations to solve problems involving modified
  Bessel differential equations of the first kind.

- **Formula:** `BESSELI(x, n)`
    - `x` is the value at which to evaluate the Bessel function.
    - `n` is the order of the Bessel function.

- **Example Usage:**
    - `=BESSELI(3.5, 2)` calculates the modified Bessel function of the first kind for `x = 3.5` and order `n = 2`.
    - `=BESSELI(A1, A2)` computes the modified Bessel function using cell references, where `A1` is the value for `x`
      and `A2` is the order `n`.

### [BESSELJ](./engineering-functions/bessel_j.md)
Calculates the Bessel function of the first kind.

- **Purpose:** This function is used in engineering and mathematical computations to solve problems involving
  Bessel differential equations of the first kind.

- **Formula:** `BESSELJ(x, n)`
  - `x` is the value at which to evaluate the Bessel function.
  - `n` is the order of the Bessel function.

- **Example Usage:**
  - `=BESSELJ(3.5, 2)` calculates the Bessel function of the first kind for `x = 3.5` and order `n = 2`.
  - `=BESSELJ(A1, A2)` computes the Bessel function using cell references, where `A1` is the value for `x`
    and `A2` is the order `n`.

### [BESSELK](./engineering-functions/bessel_k.md)
Calculates the modified Bessel function of the second kind.

- **Purpose:** This function is used in engineering and mathematical computations to solve problems involving modified
  Bessel differential equations of the second kind.

- **Formula:** `BESSELK(x, n)`
  - `x` is the value at which to evaluate the Bessel function.
  - `n` is the order of the Bessel function.

- **Example Usage:**
  - `=BESSELK(3.5, 2)` calculates the modified Bessel function of the second kind for `x = 3.5` and order `n = 2`.
  - `=BESSELK(A1, A2)` computes the modified Bessel function using cell references, where `A1` is the value for `x`
    and `A2` is the order `n`.

### [BESSELY](./engineering-functions/bessel_y.md)
Calculates the Bessel function of the second kind.

- **Purpose:** This function is used in engineering and mathematical computations to solve problems involving
  Bessel differential equations of the second kind.

- **Formula:** `BESSELY(x, n)`
  - `x` is the value at which to evaluate the Bessel function.
  - `n` is the order of the Bessel function.

- **Example Usage:**
  - `=BESSELY(3.5, 2)` calculates the Bessel function of the second kind for `x = 3.5` and order `n = 2`.
  - `=BESSELY(A1, A2)` computes the Bessel function using cell references, where `A1` is the value for `x`
    and `A2` is the order `n`.

### [BIN2DEC](./engineering-functions/bin_2_dec.md)
Converts a binary number to its decimal equivalent.

- **Purpose:** This function is used to convert a binary (base-2) number into its decimal (base-10) equivalent, which is
  commonly used in engineering, mathematics, and computing.

- **Formula:** `BIN2DEC(text)`
  - `text` is the binary string that you want to convert to a decimal number. The binary string can have up to 10
    characters (0s and 1s) and may represent either positive or negative numbers using two's complement representation.

- **Example Usage:**
  - `=BIN2DEC("1101")` converts the binary number `1101` into the decimal value `13`.
  - `=BIN2DEC("1111111111")` converts the binary number `1111111111` into the decimal value `-1` (two's complement).

### [BIN2HEX](./engineering-functions/bin_2_hex.md)
Converts a binary number to its hexadecimal equivalent.

- **Purpose:** This function is used to convert a binary (base-2) number into its hexadecimal (base-16) equivalent,
  commonly used in computing and engineering.

- **Formula:** `BIN2HEX(text, [places])`
  - `text` is the binary string that you want to convert to a hexadecimal number. The binary string can have up to 10
    characters (0s and 1s).
  -  `places` (optional): Specifies the number of characters in the hexadecimal result.
   If the result has fewer characters than the value specified, leading zeroes are added.
   If omitted, Excel uses the minimum number of characters necessary.

- **Example Usage:**
  - `=BIN2HEX("1101")` converts the binary number `1101` into the hexadecimal value `D`.
  - `=BIN2HEX("1111111101")` converts the binary number `1111111101` into the hexadecimal value `3FD` (two's complement
    for negative numbers).

### [BIN2OCT](./engineering-functions/bin_2_oct.md)
Converts a binary number to its octal equivalent.

- **Purpose:** This function is used to convert a binary (base-2) number into its octal (base-8) equivalent,
  commonly used in computing and engineering.

- **Formula:** `BIN2OCT(text, [places])`
  - `text` is the binary string that you want to convert to an octal number. The binary string can have up to 10
    characters (0s and 1s).
  - `places` (optional): Specifies the number of characters in the octal result.
    If the result has fewer characters than the value specified, leading zeroes are added.
    If omitted, Excel uses the minimum number of characters necessary.

- **Example Usage:**
  - `=BIN2OCT("1101")` converts the binary number `1101` into the octal value `15`.
  - `=BIN2OCT("1111111101")` converts the binary number `1111111101` into the octal value `7775` (two's complement
    for negative numbers).

### [BITAND](./engineering-functions/bit_and.md)
Performs a bitwise AND operation on two numbers.

- **Purpose:** This function is used to perform a bitwise AND operation, often used in engineering, computing, and
  digital logic design.

- **Formula:** `BITAND(number1, number2)`
  - `number1` is the first non-negative integer.
  - `number2` is the second non-negative integer.

- **Example Usage:**
  - `=BITAND(5, 3)` computes the bitwise AND of the numbers `5` (`101` in binary) and `3` (`011` in binary), resulting
    in `1` (`001` in binary).
  - `=BITAND(A1, A2)` computes the bitwise AND operation using cell references, where `A1` and `A2` are non-negative
    integers.

### [BITLSHIFT](./engineering-functions/bit_l_shift.md)
Performs a bitwise left shift operation on a number.

- **Purpose:** This function is used to perform a bitwise left shift operation, often applied in engineering, computing,
  and digital logic.

- **Formula:** `BITLSHIFT(number, shift_amount)`
  - `number` is the non-negative integer to be shifted.
  - `shift_amount` is the number of positions to shift the bits to the left. Non-negative integer values are expected.
    If the `shift_amount` is 0, the function returns the original number.

- **Example Usage:**
  - `=BITLSHIFT(5, 2)` computes a bitwise left shift of the number `5` (`101` in binary), shifting it `2` positions to
    the left, resulting in `20` (`10100` in binary).
  - `=BITLSHIFT(A1, A2)` computes the bitwise left shift operation using cell references, where `A1` is the number to
    shift, and `A2` is the shift amount.

### [BITOR](./engineering-functions/bit_or.md)
Performs a bitwise OR operation on two numbers.

- **Purpose:** This function is used to perform a bitwise OR operation, often used in engineering, computing, and
  digital logic design.

- **Formula:** `BITOR(number1, number2)`
  - `number1` is the first non-negative integer.
  - `number2` is the second non-negative integer.

- **Example Usage:**
  - `=BITOR(5, 3)` computes the bitwise OR of the numbers `5` (`101` in binary) and `3` (`011` in binary), resulting in
    `7` (`111` in binary).
  - `=BITOR(A1, A2)` computes the bitwise OR operation using cell references, where `A1` and `A2` are non-negative
    integers.

### [BITRSHIFT](./engineering-functions/bit_r_shift.md)
Performs a bitwise right shift operation on a number.

- **Purpose:** This function is used to perform a bitwise right shift operation, often applied in engineering,
  computing,
  and digital logic.

- **Formula:** `BITRSHIFT(number, shift_amount)`
  - `number` is the non-negative integer to be shifted.
  - `shift_amount` is the number of positions to shift the bits to the right. Non-negative integer values are expected.
    If the `shift_amount` is 0, the function returns the original number.

- **Example Usage:**
  - `=BITRSHIFT(20, 2)` computes a bitwise right shift of the number `20` (`10100` in binary), shifting it `2` positions
    to
    the right, resulting in `5` (`101` in binary).
  - `=BITRSHIFT(A1, A2)` computes the bitwise right shift operation using cell references, where `A1` is the number to
    shift, and `A2` is the shift amount.

### [BITXOR](./engineering-functions/bit_xor.md)
Performs a bitwise XOR operation on two numbers.

- **Purpose:** This function is used to perform a bitwise XOR operation, often used in engineering, computing, and
  digital logic design.

- **Formula:** `BITXOR(number1, number2)`
  - `number1` is the first non-negative integer.
  - `number2` is the second non-negative integer.

- **Example Usage:**
  - `=BITXOR(5, 3)` computes the bitwise XOR of the numbers `5` (`101` in binary) and `3` (`011` in binary), resulting
    in `6` (`110` in binary).
  - `=BITXOR(A1, A2)` computes the bitwise XOR operation using cell references, where `A1` and `A2` are non-negative
    integers.

### [DEC2BIN](./engineering-functions/dec_2_bin.md)
Converts a decimal number to its binary equivalent.

- **Purpose:** This function is used to convert a decimal (base-10) number into its binary (base-2) equivalent, commonly
  used in computing and digital logic.

- **Formula:** `DEC2BIN(number, [places])`
  - `number` is the decimal integer you want to convert to binary. It can be a positive or negative value.
  - `places` (optional): Specifies the number of characters in the binary result.  
    If the result has fewer characters than the value specified, leading zeroes are added.  
    If omitted, the function uses the minimum number of characters necessary.

- **Example Usage:**
  - `=DEC2BIN(13)` converts the decimal number `13` into the binary value `1101`.
  - `=DEC2BIN(-1)` converts the decimal number `-1` into the binary value `1111111111` (two's complement representation
    with a width of 10 bits).
  - `=DEC2BIN(13, 8)` converts the decimal number `13` into the binary value `00001101`, ensuring the result has 8
    characters.

### [DEC2HEX](./engineering-functions/dec_2_hex.md)
Converts a decimal number to its hexadecimal equivalent.

- **Purpose:** This function is used to convert a decimal (base-10) number into its hexadecimal (base-16) equivalent,
  commonly used in computing and engineering.

- **Formula:** `DEC2HEX(number, [places])`
  - `number` is the decimal integer you want to convert to hexadecimal. It can be a positive or negative value.
  - `places` (optional): Specifies the number of characters in the hexadecimal result.  
    If the result has fewer characters than the value specified, leading zeroes are added.  
    If omitted, the function uses the minimum number of characters necessary.

- **Example Usage:**
  - `=DEC2HEX(255)` converts the decimal number `255` into the hexadecimal value `FF`.
  - `=DEC2HEX(-1)` converts the decimal number `-1` into the hexadecimal value `FFFFFFFF` (two's complement
    representation with a width of 32 bits by default).
  - `=DEC2HEX(255, 4)` converts the decimal number `255` into the hexadecimal value `00FF`, ensuring the result has 4
    characters.

### [DEC2OCT](./engineering-functions/dec_2_oct.md)
Converts a decimal number to its octal equivalent.

- **Purpose:** This function is used to convert a decimal (base-10) number into its octal (base-8) equivalent, commonly
  used in computing and engineering.

- **Formula:** `DEC2OCT(number, [places])`
  - `number` is the decimal integer you want to convert to octal. It can be a positive or negative value.
  - `places` (optional): Specifies the number of characters in the octal result.  
    If the result has fewer characters than the value specified, leading zeroes are added.  
    If omitted, the function uses the minimum number of characters necessary.

- **Example Usage:**
  - `=DEC2OCT(10)` converts the decimal number `10` into the octal value `12`.
  - `=DEC2OCT(-1)` converts the decimal number `-1` into the octal value `7777777777` (two's complement representation
    with a width of 10 bits).
  - `=DEC2OCT(8, 4)` converts the decimal number `8` into the octal value `0010`, ensuring the result has 4 characters.

### [DELTA](./engineering-functions/delta.md)
Checks whether two numbers are equal, returning 1 if they are equal and 0 otherwise.

- **Purpose:** This function is used to compare two numbers and check if they are equal, commonly used in engineering,
  computing, and mathematical calculations.

- **Formula:** `DELTA(number1, number2)`
  - `number1` is the first number to compare.
  - `number2` is the second number to compare. If omitted, the default value is `0`.

- **Behavior:**
  - Returns `1` if `number1` equals `number2`.
  - Returns `0` otherwise.

- **Example Usage:**
  - `=DELTA(5, 5)` returns `1` because the numbers are equal.
  - `=DELTA(5, 3)` returns `0` because the numbers are not equal.
  - `=DELTA(5)` returns `0` because `5` is not equal to the default value of `0`.

### [ERF](./engineering-functions/erf.md)
Calculates the error function (ERF) of a number.

- **Purpose:** This function is used to compute the error function, which is commonly used in probability, statistics,
  and partial differential equations.

- **Formula:** `ERF(lower_limit, [upper_limit])`
  - `lower_limit` is the lower bound of the integral for calculating the error function.
  - `upper_limit` (optional) is the upper bound of the integral.  
    If omitted, the error function is calculated from `0` to `lower_limit`.

- **Behavior:**
  - If both `lower_limit` and `upper_limit` are provided, the function calculates the integral of the Gaussian
    probability density function between the two bounds.
  - If `upper_limit` is omitted, the function defaults to calculating `ERF` from `0` to `lower_limit`.

- **Example Usage:**
  - `=ERF(1)` calculates the error function from `0` to `1`, resulting in approximately `0.8427`.
  - `=ERF(1, 2)` calculates the error function from `1` to `2`, resulting in approximately `0.1359`.
  - `=ERF(-1)` calculates the error function from `0` to `-1`, resulting in approximately `-0.8427`.

### [ERFPRECISE](./engineering-functions/erf_precise.md)
Calculates the precise error function (ERF) of a number with a higher degree of accuracy.

- **Purpose:** This function is used to compute the error function with higher precision, commonly used in probability,
  statistics, and mathematical calculations requiring greater accuracy.

- **Formula:** `ERF.PRECISE(number)`
  - `number` is the point at which the error function needs to be evaluated.

- **Example Usage:**
  - `=ERF.PRECISE(1)` calculates the error function at `1`, resulting in approximately `0.8427` with higher precision.
  - `=ERF.PRECISE(-1)` calculates the error function at `-1`, resulting in approximately `-0.8427` with higher precision.
  - `=ERF.PRECISE(2)` calculates the error function at `2`, resulting in approximately `0.9953` with higher precision.

### [ERFC](./engineering-functions/erfc.md)
Calculates the complementary error function (ERFC) of a number.

- **Purpose:** This function is used to compute the complementary error function, which is commonly used in probability,
  statistics, and mathematical calculations.

- **Formula:** `ERFC(number)`
  - `number` is the point at which the complementary error function needs to be evaluated.

- **Behavior:**
  - The complementary error function is defined as `1 - ERF(number)`.

- **Example Usage:**
  - `=ERFC(1)` calculates the complementary error function at `1`, resulting in approximately `0.1573`.
  - `=ERFC(-1)` calculates the complementary error function at `-1`, resulting in approximately `1.8427`.
  - `=ERFC(2)` calculates the complementary error function at `2`, resulting in approximately `0.0047`.

### [ERFC.PRECISE](./engineering-functions/erfc_precise.md)
Calculates the complementary error function (ERFC) of a number with a higher degree of accuracy.

- **Purpose:** This function is used to compute the complementary error function with higher precision, commonly used in
  probability, statistics, and mathematical calculations requiring greater accuracy.

- **Formula:** `ERFC.PRECISE(number)`
  - `number` is the point at which the complementary error function needs to be evaluated.

- **Example Usage:**
  - `=ERFC.PRECISE(1)` calculates the complementary error function at `1`, resulting in approximately `0.1573` with
    higher precision.
  - `=ERFC.PRECISE(-1)` calculates the complementary error function at `-1`, resulting in approximately `1.8427` with
    higher precision.
  - `=ERFC.PRECISE(2)` calculates the complementary error function at `2`, resulting in approximately `0.0047` with
    higher precision.

## G

### [GESTEP](./engineering-functions/ge_step.md)
Returns 1 if a number is greater than or equal to a step value, and 0 otherwise.

- **Purpose:** This function is used to test whether a number is greater than or equal to a specified step value. It is
  commonly used in logical comparisons and engineering calculations.

- **Formula:** `GESTEP(number, [step])`
  - `number` is the value to test.
  - `step` (optional) is the threshold value for comparison. If omitted, the default value is `0`.

- **Behavior:**
  - Returns `1` if `number` is greater than or equal to `step`.
  - Returns `0` otherwise.

- **Example Usage:**
  - `=GESTEP(5, 3)` returns `1` because `5` is greater than or equal to `3`.
  - `=GESTEP(2, 5)` returns `0` because `2` is not greater than or equal to `5`.
  - `=GESTEP(0)` returns `1` because `0` is greater than or equal to the default `step` value of `0`.

## H

### [HEX2BIN](./engineering-functions/hex_2_bin.md)
Converts a hexadecimal number to its binary equivalent.

- **Purpose:** This function is used to convert a hexadecimal (base-16) number into its binary (base-2) equivalent,
  commonly used in computing and engineering.

- **Formula:** `HEX2BIN(number, [places])`
  - `number` is the hexadecimal value you want to convert to binary. It can be a positive or negative value.
  - `places` (optional): Specifies the number of characters in the binary result.  
    If the result has fewer characters than the value specified, leading zeroes are added.  
    If omitted, the function uses the minimum number of characters necessary.

- **Example Usage:**
  - `=HEX2BIN("F")` converts the hexadecimal value `F` into the binary value `1111`.
  - `=HEX2BIN("F", 8)` converts the hexadecimal value `F` into the binary value `00001111`, ensuring the result has 8
    characters.
  - `=HEX2BIN("2A", 16)` converts the hexadecimal value `2A` into the binary value `0000000000101010`, ensuring the
    result has 16 characters.

### [HEX2DEC](./engineering-functions/hex_2_dec.md)
Converts a hexadecimal number to its decimal equivalent.

- **Purpose:** This function is used to convert a hexadecimal (base-16) number into its decimal (base-10) equivalent,
  commonly used in computing and engineering.

- **Formula:** `HEX2DEC(number)`
  - `number` is the hexadecimal value you want to convert to decimal. It can be a positive or negative value.

- **Example Usage:**
  - `=HEX2DEC("F")` converts the hexadecimal value `F` into the decimal value `15`.
  - `=HEX2DEC("2A")` converts the hexadecimal value `2A` into the decimal value `42`.
  - `=HEX2DEC("-1F")` converts the hexadecimal value `-1F` into the decimal value `-31`.

### [HEX2OCT](./engineering-functions/hex_2_oct.md)
Converts a hexadecimal number to its octal equivalent.

- **Purpose:** This function is used to convert a hexadecimal (base-16) number into its octal (base-8) equivalent,
  commonly used in computing and engineering.

- **Formula:** `HEX2OCT(number, [places])`
  - `number` is the hexadecimal value you want to convert to octal. It can be a positive or negative value.
  - `places` (optional): Specifies the number of characters in the octal result.  
    If the result has fewer characters than the value specified, leading zeroes are added.  
    If omitted, the function uses the minimum number of characters necessary.

- **Example Usage:**
  - `=HEX2OCT("F")` converts the hexadecimal value `F` into the octal value `17`.
  - `=HEX2OCT("F", 4)` converts the hexadecimal value `F` into the octal value `0017`, ensuring the result has 4
    characters.
  - `=HEX2OCT("2A", 6)` converts the hexadecimal value `2A` into the octal value `000052`, ensuring the result has 6
    characters.

### [IMABS](./engineering-functions/im_abs.md)
Calculates the absolute value (modulus) of a complex number.

- **Purpose:** This function is used to return the absolute value (or modulus) of a complex number, helpful in complex
  number arithmetic.

- **Formula:** `IMABS(inumber)`
  - `inumber` is the complex number for which you want the absolute value. It can be in the form `x+yi` or `x+yj`.

- **Example Usage:**
  - `=IMABS("3+4i")` returns `5`, since the modulus of `3 + 4i` is `√(3² + 4²) = 5`.
  - `=IMABS("-3-4i")` returns `5` because the modulus depends only on the magnitude, not the sign.
  - `=IMABS("0+2i")` returns `2`, as it's the distance of `2i` from `0`.

### [IMARGUMENT](./engineering-functions/im_argument.md)
Calculates the argument (angle in radians) of a complex number.

- **Purpose:** This function is used to calculate the angle (in radians) formed by a complex number in the complex plane
  with respect to the positive real axis. It is commonly used in engineering, physics, and mathematics when working with
  complex numbers.

- **Formula:** `IMARGUMENT(inumber)`
  - `inumber` is the complex number for which you want to calculate the argument. It can be in the form `x+yi` or
    `x+yj`.

- **Example Usage:**
  - `=IMARGUMENT("1+i")` returns approximately `0.7854`, which is `π/4`, as it forms a 45-degree angle.
  - `=IMARGUMENT("-1-i")` returns approximately `-2.3562`, which is `-3π/4`.
  - `=IMARGUMENT("0+1i")` returns `1.5708`, which is `π/2` as it lies on the positive imaginary axis.
  - `=IMARGUMENT("3")` returns `0`, as it lies on the positive real axis.

### [IMCONJUGATE](./engineering-functions/im_conjugate.md)
Calculates the complex conjugate of a complex number.

- **Purpose:** This function is used to return the complex conjugate of a complex number, where the sign of the
  imaginary
  part is reversed. Useful in various applications involving complex number arithmetic.

- **Formula:** `IMCONJUGATE(inumber)`
  - `inumber` is the complex number for which you want the conjugate. It can be in the form `x+yi` or `x+yj`.

- **Example Usage:**
  - `=IMCONJUGATE("3+4i")` returns `3-4i`, as the conjugate of `3+4i` is `3-4i`.
  - `=IMCONJUGATE("-2-5j")` returns `-2+5j`, reversing the sign of the imaginary part.
  - `=IMCONJUGATE("0+2i")` returns `-2i`, where only the imaginary part changes.
  - `=IMCONJUGATE("5")` returns `5`, as real numbers are unchanged when conjugated.

### [IMCOS](./engineering-functions/im_cos.md)
Calculates the cosine of a complex number.

- **Purpose:** This function is used to return the cosine of a complex number, helpful in engineering and mathematical
  calculations involving trigonometric functions of complex numbers.

- **Formula:** `IMCOS(inumber)`
  - `inumber` is the complex number for which you want to calculate the cosine. It can be in the form `x+yi` or `x+yj`.

- **Example Usage:**
  - `=IMCOS("0")` returns `1`, as the cosine of `0` is `1`.
  - `=IMCOS("i")` returns approximately `1.5431`, as the cosine of `i` is `cosh(1)`.
  - `=IMCOS("1+i")` returns approximately `0.83373 - 0.9889i`, as the cosine is calculated using both the real and
    imaginary components.
  - `=IMCOS("-1-2i")` returns approximately `-1.5656 - 3.2979i`.

### [IMCOSH](./engineering-functions/im_cosh.md)
Calculates the hyperbolic cosine of a complex number.

- **Purpose:** This function is used to return the hyperbolic cosine of a complex number, which is helpful in
  engineering and mathematical calculations involving hyperbolic functions of complex numbers.

- **Formula:** `IMCOSH(inumber)`
  - `inumber` is the complex number for which you want to calculate the hyperbolic cosine. It can be in the form
    `x+yi` or `x+yj`.

- **Example Usage:**
  - `=IMCOSH("0")` returns `1`, as the hyperbolic cosine of `0` is `1`.
  - `=IMCOSH("i")` returns approximately `0.5403 + 0.0i`, as the hyperbolic cosine of `i` is `cos(1)`.
  - `=IMCOSH("1+i")` returns approximately `0.83373 + 0.9889i`, as the hyperbolic cosine is calculated using both the
    real and imaginary components.
  - `=IMCOSH("-1-2i")` returns approximately `-0.6421 - 1.0688i`.

### [IMCOT](./engineering-functions/im_cot.md)
Calculates the cotangent of a complex number.

- **Purpose:** This function is used to return the cotangent of a complex number, helpful in engineering and
  mathematical
  calculations involving trigonometric functions of complex numbers.

- **Formula:** `IMCOT(inumber)`
  - `inumber` is the complex number for which you want to calculate the cotangent. It can be in the form `x+yi` or
    `x+yj`.

- **Example Usage:**
  - `=IMCOT("1")` returns approximately `0.6421 - 0.0i`, as cotangent is the reciprocal of tangent.
  - `=IMCOT("i")` returns approximately `0.0 - 0.7616i`.
  - `=IMCOT("1+i")` returns approximately `0.2176 - 0.8680i`, as cotangent is calculated using both the real and
    imaginary components.
  - `=IMCOT("-1-2i")` returns approximately `-0.0338 + 0.0753i`.

### [IMCSC](./engineering-functions/im_csc.md)
Calculates the cosecant of a complex number.

- **Purpose:** This function is used to return the cosecant (reciprocal of sine) of a complex number, helpful in
  engineering and mathematical calculations involving trigonometric functions of complex numbers.

- **Formula:** `IMCSC(inumber)`
  - `inumber` is the complex number for which you want to calculate the cosecant. It can be in the form `x+yi` or
    `x+yj`.

- **Example Usage:**
  - `=IMCSC("1")` returns approximately `1.1884 + 0.0i`, as cosecant is the reciprocal of sine.
  - `=IMCSC("i")` returns approximately `0.0 - 0.8509i`.
  - `=IMCSC("1+i")` returns approximately `0.6215 - 0.3039i`, as the cosecant is calculated using the reciprocal of sine
    for both the real and imaginary components.
  - `=IMCSC("-1-2i")` returns approximately `-0.2284 - 0.1414i`.

### [IMCSCH](./engineering-functions/im_csch.md)
Calculates the hyperbolic cosecant of a complex number.

- **Purpose:** This function is used to return the hyperbolic cosecant (reciprocal of hyperbolic sine) of a complex
  number, helpful in engineering and mathematical calculations involving hyperbolic functions of complex numbers.

- **Formula:** `IMCSCH(inumber)`
  - `inumber` is the complex number for which you want to calculate the hyperbolic cosecant. It can be in the form
    `x+yi` or `x+yj`.

- **Example Usage:**
  - `=IMCSCH("1")` returns approximately `0.8509 - 0.0i`, as hyperbolic cosecant is the reciprocal of hyperbolic sine.
  - `=IMCSCH("i")` returns approximately `0.0 - 1.1884i`.
  - `=IMCSCH("1+i")` returns approximately `0.3039 - 0.6215i`, calculated as the reciprocal of the hyperbolic sine of
    both real and imaginary components.
  - `=IMCSCH("-1-2i")` returns approximately `-0.1414 - 0.2284i`.

### [IMDIV](./engineering-functions/im_div.md)
Calculates the quotient of two complex numbers.

- **Purpose:** This function is used to divide one complex number by another, useful in various engineering, physics, and mathematics applications involving complex number arithmetic.

- **Formula:** `IMDIV(inumber1, inumber2)`
  - `inumber1` is the complex number you want to divide (numerator). It can be in the form `x+yi` or `x+yj`.
  - `inumber2` is the complex number you want to divide by (denominator). It can be in the form `x+yi` or `x+yj`.
  - The formula for dividing complex numbers is:
    ```
    (a + bi) / (c + di) = [(a*c + b*d) + (b*c - a*d)i] / (c² + d²)
    ```

- **Example Usage:**
  - `=IMDIV("3+4i", "1+i")` returns `3.5 + 0.5i`, dividing `3+4i` by `1+i`.
  - `=IMDIV("1", "2+i")` returns approximately `0.4 - 0.2i`.
  - `=IMDIV("0+2i", "3+4i")` returns approximately `0.32 + 0.24i`, dividing purely imaginary numbers.
  - `=IMDIV("4", "0+i")` returns `0 - 4i`, dividing a real number by an imaginary number.
  - `=IMDIV("2+i", "0")` returns an error, as division by zero is undefined.

### [IMEXP](./engineering-functions/im_exp.md)
Calculates the exponential of a complex number.

- **Purpose:** This function is used to compute the exponential of a complex number, which is often required in
  engineering, physics, and mathematics for dealing with growth processes or oscillatory phenomena.

- **Formula:** `IMEXP(inumber)`
  - `inumber` is the complex number for which you want to calculate the exponential. It can be in the form `x+yi` or
    `x+yj`.
  - The formula for the exponential of a complex number is:
    ```
    e^(a + bi) = e^a * [cos(b) + i*sin(b)]
    ```

- **Example Usage:**
  - `=IMEXP("0")` returns `1`, as `e^0 = 1`.
  - `=IMEXP("1")` returns approximately `2.7183`, as `e^1 = 2.7183`.
  - `=IMEXP("i")` returns approximately `0.5403 + 0.8415i`, as `e^(i) = cos(1) + i*sin(1)`.
  - `=IMEXP("1+i")` returns approximately `1.4687 + 2.2874i`, using the formula to calculate both real and imaginary components.
  - `=IMEXP("-1-2i")` returns approximately `-0.0677 - 0.2441i`, using the same formula for exponential.

### [IMLN](./engineering-functions/im_ln.md)
Calculates the natural logarithm of a complex number.

- **Purpose:** This function is used to compute the natural logarithm of a complex number, commonly used in engineering,
  physics, and mathematical applications.

- **Formula:** `IMLN(inumber)`
  - `inumber` is the complex number for which you want to calculate the natural logarithm. It can be in the form `x+yi`
    or `x+yj`.
  - The formula to calculate the natural logarithm of a complex number is:
    ```
    ln(a + bi) = ln|a + bi| + i*arg(a + bi)
    ```
    Where:
    - `ln|a + bi|` is the natural logarithm of the magnitude: `ln(sqrt(a² + b²))`
    - `arg(a + bi)` is the argument (angle) of the complex number: `atan2(b, a)`

- **Example Usage:**
  - `=IMLN("1")` returns `0`, as `ln(1) = 0`.
  - `=IMLN("i")` returns approximately `0 + 1.5708i`, as the magnitude is 1 and the angle is π/2 radians.
  - `=IMLN("1+i")` returns approximately `0.3466 + 0.7854i`, calculated using the formula.
  - `=IMLN("-1-2i")` returns approximately `0.8047 - 2.0344i`, using the natural logarithm formula.

### [IMLOG10](./engineering-functions/im_log10.md)
Calculates the base-10 logarithm of a complex number.

- **Purpose:** This function is used to compute the logarithm with base 10 of a complex number, which is useful in
  engineering, physics, and mathematical applications where log scales are required.

- **Formula:** `IMLOG10(inumber)`
  - `inumber` is the complex number for which you want to calculate the base-10 logarithm. It can be in the form `x+yi`
    or `x+yj`.
  - The formula for the base-10 logarithm of a complex number is:
    ```
    log10(a + bi) = ln(a + bi) / ln(10)
    ```
    Where `ln(10)` is the natural logarithm of 10 (approximately 2.3026).

- **Example Usage:**
  - `=IMLOG10("1")` returns `0`, as `log10(1) = 0`.
  - `=IMLOG10("10")` returns `1`, as `log10(10) = 1`.
  - `=IMLOG10("i")` returns approximately `0 + 0.6822i`, calculated using the formula.
  - `=IMLOG10("1+i")` returns approximately `0.1505 + 0.3411i`, using the base-10 logarithm formula.
  - `=IMLOG10("-1-2i")` returns approximately `0.3490 - 0.8826i`, using the same formula.

### [IMLOG2](./engineering-functions/im_log2.md)
Calculates the base-2 logarithm of a complex number.

- **Purpose:** This function is used to compute the logarithm with base 2 of a complex number, which is useful in
  engineering, physics, and mathematical applications involving binary logarithmic scales.

- **Formula:** `IMLOG2(inumber)`
  - `inumber` is the complex number for which you want to calculate the base-2 logarithm. It can be in the form `x+yi`
    or `x+yj`.
  - The formula for the base-2 logarithm of a complex number is:
    ```
    log2(a + bi) = ln(a + bi) / ln(2)
    ```
    Where `ln(2)` is the natural logarithm of 2 (approximately 0.6931).

- **Example Usage:**
  - `=IMLOG2("1")` returns `0`, as `log2(1) = 0`.
  - `=IMLOG2("2")` returns `1`, as `log2(2) = 1`.
  - `=IMLOG2("i")` returns approximately `0 + 2.2662i`, calculated using the formula.
  - `=IMLOG2("1+i")` returns approximately `0.5000 + 1.1331i`, using the base-2 logarithm formula.
  - `=IMLOG2("-1-2i")` returns approximately `1.1590 - 2.9374i`, using the same formula.

### [IMPOWER](./engineering-functions/im_power.md)
Raises a complex number to a given power.

- **Purpose:** This function is used to calculate the result of raising a complex number to a given power, which is
  common in engineering, physics, and mathematical applications.

- **Formula:** `IMPOWER(inumber, power)`
  - `inumber` is the complex number that you want to raise to a power. It can be in the form `x+yi` or `x+yj`.
  - `power` is the power to which the complex number is raised. It can be any real number.
  - The formula for raising a complex number to a power is:
    ```
    (a + bi)^n = r^n * [cos(n*θ) + i*sin(n*θ)]
    ```
    Where:
    - `r = sqrt(a² + b²)` is the magnitude of the complex number.
    - `θ = atan2(b, a)` is the argument (angle) of the complex number.

- **Example Usage:**
  - `=IMPOWER("1+i", 2)` returns `0 + 2i`, as `(1 + i)^2 = 2i`.
  - `=IMPOWER("2", 3)` returns `8`, as `2^3 = 8`.
  - `=IMPOWER("0+i", 4)` returns `0`, as raising pure imaginary `i` to the fourth power returns 0 due to cyclic
    properties of imaginary numbers.
  - `=IMPOWER("-1-2i", 3)` returns approximately `-11 + 2i`, calculated using the power formula.

### [IMPRODUCT](./engineering-functions/im_product.md)
Calculates the product of two or more complex numbers.

- **Purpose:** This function is used to compute the product of multiple complex numbers, which is widely used in
  engineering, physics, and mathematical calculations involving complex arithmetic.

- **Formula:** `IMPRODUCT(inumber1, [inumber2, ...])`
  - `inumber1, inumber2, ...` are the complex numbers you want to multiply. Each number can be in the form `x+yi` or
    `x+yj`. At least one number must be provided as input.
  - The general process for multiplying complex numbers `(a+bi)` and `(c+di)` is:
    ```
    (a + bi) * (c + di) = (ac - bd) + (ad + bc)i
    ```
    When multiplying more than two complex numbers, the multiplication is associative, so it proceeds pairwise.

- **Example Usage:**
  - `=IMPRODUCT("1+i", "2+i")` returns `1 + 3i`, as `(1+i) * (2+i) = 1 + 3i`.
  - `=IMPRODUCT("2", "3")` returns `6`, as `2 * 3 = 6`.
  - `=IMPRODUCT("1+i", "0")` returns `0`, since any number multiplied by `0` is `0`.
  - `=IMPRODUCT("i", "i")` returns `-1`, as `i * i = -1`.
  - `=IMPRODUCT("-1-2i", "3+4i")` returns `5 - 10i`, calculated using the formula for complex multiplication.

### [IMREAL](./engineering-functions/im_real.md)
Returns the real part of a complex number.

- **Purpose:** This function is used to extract the real part of a given complex number, which is useful in many
  engineering and mathematical calculations.

- **Formula:** `IMREAL(inumber)`
  - `inumber` is the complex number from which you want to extract the real part. It can be in the form `x+yi` or
    `x+yj`.
  - The real part of a complex number `a + bi` is simply `a`.

- **Example Usage:**
  - `=IMREAL("3+4i")` returns `3`, as the real part is 3.
  - `=IMREAL("-2")` returns `-2`, as the real part is -2 (no imaginary part present).
  - `=IMREAL("0+i")` returns `0`, as the real part is 0.
  - `=IMREAL("-1-2i")` returns `-1`, as the real part is -1.
  - `=IMREAL("5")` returns `5`, as the real part is 5 (no imaginary part present).

### [IMSEC](./engineering-functions/im_sec.md)
Calculates the secant of a complex number.

- **Purpose:** This function computes the secant (1/cosine) of a given complex number, which is useful in engineering,
  physics, and mathematical applications involving trigonometric functions for complex values.

- **Formula:** `IMSEC(inumber)`
  - `inumber` is the complex number for which you want to calculate the secant. It can be in the form `x+yi` or `x+yj`.
  - The formula for the secant of a complex number is:
    ```
    sec(a + bi) = 1 / cos(a + bi)
    ```
    Where:
    - `cos(a + bi) = cos(a)cosh(b) - i*sin(a)sinh(b)`
    - `cosh(b)` and `sinh(b)` are the hyperbolic cosine and sine of the imaginary part, respectively.

- **Example Usage:**
  - `=IMSEC("0")` returns `1`, as `sec(0) = 1`.
  - `=IMSEC("i")` returns approximately `0.6481 - 0.0000i`, calculated using the formula.
  - `=IMSEC("1+i")` returns approximately `0.4983 - 0.5911i`, using the secant formula.
  - `=IMSEC("-1-2i")` returns approximately `-0.0417 - 0.0903i`, calculated using the same formula.

### [IMSECH](./engineering-functions/im_sech.md)
Calculates the hyperbolic secant of a complex number.

- **Purpose:** This function computes the hyperbolic secant (1/cosh) of a given complex number, which is useful in
  engineering,
  physics, and mathematical applications involving hyperbolic trigonometric functions for complex values.

- **Formula:** `IMSECH(inumber)`
  - `inumber` is the complex number for which you want to calculate the hyperbolic secant. It can be in the form `x+yi`
    or `x+yj`.
  - The formula for the hyperbolic secant of a complex number is:
    ```
    sech(a + bi) = 1 / cosh(a + bi)
    ```
    Where:
    - `cosh(a + bi) = cosh(a)cos(b) + i*sinh(a)sin(b)`
    - `cosh(a)` and `sinh(a)` are the hyperbolic cosine and sine of the real part, respectively.

- **Example Usage:**
  - `=IMSECH("0")` returns `1`, as `sech(0) = 1`.
  - `=IMSECH("i")` returns approximately `0.6481 + 0.0000i`, calculated using the formula.
  - `=IMSECH("1+i")` returns approximately `0.4983 - 0.5911i`, using the hyperbolic secant formula.
  - `=IMSECH("-1-2i")` returns approximately `-0.0416 + 0.0903i`, calculated using the same formula.

### [IMSIN](./engineering-functions/im_sin.md)
Calculates the sine of a complex number.

- **Purpose:** This function computes the sine of a given complex number, which is useful in engineering, physics, and
  mathematical applications involving trigonometric functions for complex values.

- **Formula:** `IMSIN(inumber)`
  - `inumber` is the complex number for which you want to calculate the sine. It can be in the form `x+yi` or `x+yj`.
  - The formula for the sine of a complex number is:
    ```
    sin(a + bi) = sin(a)cosh(b) + i*cos(a)sinh(b)
    ```
    Where:
    - `cosh(b)` and `sinh(b)` are the hyperbolic cosine and sine of the imaginary part, respectively.

- **Example Usage:**
  - `=IMSIN("0")` returns `0`, as `sin(0) = 0`.
  - `=IMSIN("i")` returns approximately `0.0000 + 1.1752i`, calculated using the formula.
  - `=IMSIN("1+i")` returns approximately `1.2985 + 0.6349i`, using the sine formula.
  - `=IMSIN("-1-2i")` returns approximately `-3.1658 - 1.9596i`, calculated using the same formula.

### [IMSINH](./engineering-functions/im_sinh.md)
Calculates the hyperbolic sine of a complex number.

- **Purpose:** This function computes the hyperbolic sine of a given complex number, which is useful in engineering,
  physics, and mathematical applications involving hyperbolic trigonometric functions for complex values.

- **Formula:** `IMSINH(inumber)`
  - `inumber` is the complex number for which you want to calculate the hyperbolic sine. It can be in the form `x+yi` or
    `x+yj`.
  - The formula for the hyperbolic sine of a complex number is:
    ```
    sinh(a + bi) = sinh(a)cos(b) + i*cosh(a)sin(b)
    ```
    Where:
    - `sinh(a)` and `cosh(a)` are the hyperbolic sine and cosine of the real part, respectively.
    - `cos(b)` and `sin(b)` are the cosine and sine of the imaginary part, respectively.

- **Example Usage:**
  - `=IMSINH("0")` returns `0`, as `sinh(0) = 0`.
  - `=IMSINH("i")` returns approximately `0.0000 + 0.8415i`, calculated using the formula.
  - `=IMSINH("1+i")` returns approximately `0.6349 + 1.2985i`, using the hyperbolic sine formula.
  - `=IMSINH("-1-2i")` returns approximately `-1.9596 - 3.1658i`, calculated using the same formula.

### [IMSQRT](./engineering-functions/im_sqrt.md)
Calculates the square root of a complex number.

- **Purpose:** This function computes the square root of a given complex number, which is useful in engineering,
  physics, and mathematical calculations involving complex numbers.

- **Formula:** `IMSQRT(inumber)`
  - `inumber` is the complex number for which you want to calculate the square root. It can be in the form `x+yi` or
    `x+yj`.
  - The formula for the square root of a complex number `a + bi` is:
    ```
    sqrt(a + bi) = ±(sqrt((|a + bi| + a) / 2) + i * sign(b) * sqrt((|a + bi| - a) / 2))
    ```
    Where:
    - `|a + bi|` is the modulus of the complex number, calculated as `sqrt(a^2 + b^2)`.
    - `sign(b)` is `1` if `b >= 0`, otherwise `-1`.

- **Example Usage:**
  - `=IMSQRT("4")` returns `2`, as `sqrt(4) = 2`.
  - `=IMSQRT("-4")` returns `0 + 2i`, as the square root of `-4` is `2i`.
  - `=IMSQRT("3+4i")` returns approximately `2 + 1i`, calculated using the square root formula.
  - `=IMSQRT("0-1i")` returns approximately `0.7071 - 0.7071i`, using the same formula.
  - `=IMSQRT("1+i")` returns approximately `1.0987 + 0.4551i`.

### [IMSUB](./engineering-functions/im_sub.md)
Subtracts one complex number from another.

- **Purpose:** This function computes the difference between two complex numbers, which is useful in engineering,
  physics, and mathematical calculations involving complex numbers.

- **Formula:** `IMSUB(inumber1, inumber2)`
  - `inumber1` is the complex number from which you want to subtract another complex number.
  - `inumber2` is the complex number to subtract from `inumber1`.
  - The formula for subtracting `inumber2` from `inumber1` is:
    ```
    (a + bi) - (c + di) = (a - c) + (b - d)i
    ```
    Where:
    - `a` and `b` are the real and imaginary parts of `inumber1`, respectively.
    - `c` and `d` are the real and imaginary parts of `inumber2`, respectively.

- **Example Usage:**
  - `=IMSUB("3+4i", "1+2i")` returns `2 + 2i`, as `(3 + 4i) - (1 + 2i) = 2 + 2i`.
  - `=IMSUB("3+4i", "3+4i")` returns `0`, as the complex numbers cancel each other out.
  - `=IMSUB("-1+2i", "1-2i")` returns `-2 + 4i`.
  - `=IMSUB("0", "1+i")` returns `-1 - i`, as the subtraction is done directly.

### [IMSUM](./engineering-functions/im_sum.md)
Adds two or more complex numbers.

- **Purpose:** This function computes the sum of two or more complex numbers, which is useful in engineering,
  physics, and mathematical calculations involving complex numbers.

- **Formula:** `IMSUM(inumber1, inumber2, [...])`
  - `inumber1, inumber2, [...]` are the complex numbers you want to add together. Each number can be in the form `x+yi`
    or `x+yj`.
  - The formula for adding complex numbers is:
    ```
    (a + bi) + (c + di) + ... + (x + yi) = (a + c + ... + x) + (b + d + ... + y)i
    ```
    Where:
    - `a`, `b` are the real and imaginary parts of the first complex number, respectively.
    - `c`, `d` are the real and imaginary parts of the second complex number, respectively.
    - `x`, `y` are the real and imaginary parts of subsequent complex numbers, respectively.

- **Example Usage:**
  - `=IMSUM("1+2i", "3+4i")` returns `4 + 6i`, as `(1 + 2i) + (3 + 4i) = 4 + 6i`.
  - `=IMSUM("0", "1", "1+i")` returns `2 + i`, as `0 + 1 + (1 + i) = 2 + i`.
  - `=IMSUM("-1+2i", "1-2i", "3+4i")` returns `3 + 4i`, as `(-1 + 2i) + (1 - 2i) + (3 + 4i) = 3 + 4i`.
  - `=IMSUM("0")` returns `0`, as it sums to itself when there's only one number.

### [IMTAN](./engineering-functions/im_tan.md)  
Calculates the tangent of a complex number.

- **Purpose:** This function computes the tangent of a given complex number, combining real and imaginary parts.
  It can be applied in various engineering, physics, and mathematical calculations involving complex trigonometric
  functions.

- **Formula:** `IMTAN(inumber)`
  - `inumber` is the complex number for which you want to calculate the tangent. It can be in the form `x+yi` or
    `x+yj`.
  - The formula for the tangent of a complex number is:
    ```
    tan(a + bi) = sin(a + bi) / cos(a + bi)
                = (sin(a)cosh(b) + i*cos(a)sinh(b)) / (cos(a)cosh(b) - i*sin(a)sinh(b))
    ```
    Where:
    - `cosh(b)` and `sinh(b)` are the hyperbolic cosine and sine of the imaginary part, respectively.
    - `cos(a)` and `sin(a)` are the cosine and sine of the real part, respectively.

- **Example Usage:**
  - `=IMTAN("0")` returns `0`, as `tan(0) = 0`.
  - `=IMTAN("i")` returns approximately `0.0000 + 1.5574i`, calculated using the formula.
  - `=IMTAN("1+i")` returns approximately `1.0839 + 0.2718i`, using the tangent formula.
  - `=IMTAN("-1-2i")` returns approximately `0.0338 - 1.0148i`, calculated using the same formula.

## O

### [OCT2BIN](./engineering-functions/oct_2_bin.md)
Converts an octal number to its binary equivalent.

- **Purpose:** This function converts an octal (base-8) number to a binary (base-2) number. This is useful in
  programming,
  electronics, and computer science.

- **Formula:** `OCT2BIN(octal_number, [places])`
  - `octal_number` is the octal number you want to convert to binary. It can be a string or a numeric value.
  - `places` (optional) is the number of characters in the result. If the binary result is shorter, leading zeros are
    added. If omitted, the result uses the minimum number of characters.

- **Example Usage:**
  - `=OCT2BIN("7")` returns `111`, as `7` in octal is `111` in binary.
  - `=OCT2BIN("10")` returns `1000`, as `10` (octal) is `1000` in binary.
  - `=OCT2BIN("10", 6)` returns `001000`, padding with leading zeros to make the result 6 characters long.
  - `=OCT2BIN("377")` returns `11111111`, as `377` (octal) is `11111111` in binary.
  - `=OCT2BIN("1")` returns `1`, as `1` in octal is `1` in binary.

### [OCT2DEC](./engineering-functions/oct_2_dec.md)
Converts an octal number to its decimal equivalent.

- **Purpose:** This function converts an octal (base-8) number to a decimal (base-10) number, which is commonly used in
  various fields like programming, electronics, and computer science.

- **Formula:** `OCT2DEC(octal_number)`
  - `octal_number` is the octal number you want to convert to decimal. It can be a string or a numeric value.
  - The conversion is calculated as the sum of digits in the octal number multiplied by 8 raised to their positional
    powers.

- **Example Usage:**
  - `=OCT2DEC("7")` returns `7`, as `7` in octal is already `7` in decimal.
  - `=OCT2DEC("10")` returns `8`, as `10` (octal) is `8` in decimal.
  - `=OCT2DEC("377")` returns `255`, as `377` (octal) is `255` in decimal.
  - `=OCT2DEC("0")` returns `0`, as `0` in octal is `0` in decimal.

### [OCT2HEX](./engineering-functions/oct_2_hex.md)
Converts an octal number to its hexadecimal equivalent.

- **Purpose:** This function converts an octal (base-8) number to a hexadecimal (base-16) number. It is commonly used in
  programming, electronics, and computer science.

- **Formula:** `OCT2HEX(octal_number, [places])`
  - `octal_number` is the octal number you want to convert to hexadecimal. It can be a string or a numeric value.
  - `places` (optional) is the number of characters in the result. If the hexadecimal result is shorter, leading zeros
    are added. If omitted, the result uses the minimum number of characters.
  - The conversion is done by first converting the octal number to decimal, and then converting the decimal number to
    hexadecimal.

- **Example Usage:**
  - `=OCT2HEX("7")` returns `7`, as `7` in octal is `7` in hexadecimal.
  - `=OCT2HEX("10")` returns `8`, as `10` (octal) is `8` in hexadecimal.
  - `=OCT2HEX("377")` returns `FF`, as `377` (octal) is `255` in decimal, and `FF` in hexadecimal.
  - `=OCT2HEX("10", 4)` returns `0008`, padding with leading zeros to make the result 4 characters long.
  - `=OCT2HEX("1")` returns `1`, as `1` in octal is `1` in hexadecimal.