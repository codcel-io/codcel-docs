<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Logical Functions

This contains the list of logical functions that are currently supported by Codcel.

## A

### [AND](./logical-functions/and.md)
Returns TRUE if all the arguments evaluate to TRUE; otherwise, returns FALSE.

- **Purpose:** Evaluates multiple conditions and returns TRUE only if all arguments are TRUE.

- **Formula:** AND(logical1, [logical2], ...)
  - **logical1, logical2, ...** are the conditions or expressions to evaluate. Each must return either TRUE or FALSE.

- **Example Usage:**
  - =AND(TRUE, TRUE, TRUE) returns TRUE (all arguments are TRUE).
  - =AND(TRUE, FALSE) returns FALSE (one argument is FALSE).
  - =AND(A1 > 0, B1 < 10) returns TRUE if A1 is greater than 0 and B1 is less than 10.

## B

### [BYCOL](./logical-functions/bycol.md)
Applies a LAMBDA function to each column in an array, returning a single-row array of results.

- **Purpose:** Processes every column of an array by applying a custom LAMBDA function and returning one result per column.

- **Formula:** BYCOL(array, lambda)
  - **array** is the array or range to process column by column.
  - **lambda** is a LAMBDA function with one parameter that receives each column as an array and returns a single value.

- **Example Usage:**
  - =BYCOL(A1:C5, LAMBDA(col, SUM(col))) sums each column in the range.
  - =BYCOL(A1:D10, LAMBDA(col, MAX(col))) finds the maximum value in each column.
  - =BYCOL(A1:C10, LAMBDA(col, AVERAGE(col))) calculates the average of each column.

### [BYROW](./logical-functions/byrow.md)
Applies a LAMBDA function to each row in an array, returning a single-column array of results.

- **Purpose:** Processes every row of an array by applying a custom LAMBDA function and returning one result per row.

- **Formula:** BYROW(array, lambda)
  - **array** is the array or range to process row by row.
  - **lambda** is a LAMBDA function with one parameter that receives each row as an array and returns a single value.

- **Example Usage:**
  - =BYROW(A1:C5, LAMBDA(row, SUM(row))) sums each row in the range.
  - =BYROW(A1:D10, LAMBDA(row, MAX(row))) finds the maximum value in each row.
  - =BYROW(A1:C10, LAMBDA(row, AVERAGE(row))) calculates the average of each row.

## I

### [IFNA](./logical-functions/ifna.md)
Returns a specified value if a formula evaluates to #N/A; otherwise returns the formula result.

- **Purpose:** Catches only `#N/A` errors and returns an alternative value, while allowing other error types to surface.

- **Formula:** IFNA(value, value_if_na)
  - **value** is the formula or expression to evaluate (typically a lookup function).
  - **value_if_na** is the value to return if the result is `#N/A`.

- **Example Usage:**
  - =IFNA(VLOOKUP("Widget", A1:B10, 2, FALSE), "Not Found") returns "Not Found" if the lookup fails with #N/A.
  - =IFNA(MATCH("Blue", C1:C20, 0), 0) returns 0 if "Blue" is not found in the range.
  - =IFNA(INDEX(B1:B50, MATCH("Jane", A1:A50, 0)), "Unknown") returns "Unknown" if the match fails.

## L

### [LAMBDA](./logical-functions/lambda.md)
Creates custom reusable functions with user-defined parameters and calculations.

- **Purpose:** Defines a custom function that can accept parameters and returns a calculated result.

- **Formula:** LAMBDA([parameter1, parameter2, ...], calculation)
  - **parameter1, parameter2, ...** are optional named parameters.
  - **calculation** is the formula to execute using those parameters.

- **Example Usage:**
  - =LAMBDA(x, x*2)(5) returns 10 (doubles the input).
  - =LAMBDA(length, width, length*width)(4, 6) returns 24 (calculates area).

- **Note:** Codcel supports inline LAMBDA only; named LAMBDAs are not currently supported.

### [LET](./logical-functions/let.md)
Assigns names to calculation results within a formula, reducing repetition and improving readability.

- **Purpose:** Defines named variables within a formula to store intermediate results.

- **Formula:** LET(name1, value1, [name2, value2, ...], calculation)
  - **name1, name2, ...** are the variable names to define.
  - **value1, value2, ...** are the values or expressions assigned to each name.
  - **calculation** is the final formula using the defined names.

- **Example Usage:**
  - =LET(x, 10, x * 2) returns 20 (assigns 10 to x, then calculates x * 2).
  - =LET(a, 5, b, 3, a + b) returns 8 (assigns two variables and adds them).
  - =LET(total, SUM(A1:A10), IF(total > 100, "High", "Low")) uses total twice without recalculating.

## M

### [MAKEARRAY](./logical-functions/makearray.md)
Creates an array of a specified size by applying a LAMBDA function to generate each element based on its row and column position.

- **Purpose:** Dynamically constructs arrays where each cell's value is determined by a LAMBDA that receives the row and column index.

- **Formula:** MAKEARRAY(rows, cols, lambda)
  - **rows** is the number of rows in the resulting array.
  - **cols** is the number of columns in the resulting array.
  - **lambda** is a LAMBDA with two parameters (row index and column index) that returns the value for each position.

- **Example Usage:**
  - =MAKEARRAY(5, 5, LAMBDA(r, c, r * c)) creates a 5x5 multiplication table.
  - =MAKEARRAY(4, 4, LAMBDA(r, c, IF(r = c, 1, 0))) creates a 4x4 identity matrix.
  - =MAKEARRAY(3, 3, LAMBDA(r, c, r + c)) creates a 3x3 grid of row-plus-column sums.

### [MAP](./logical-functions/map.md)
Applies a LAMBDA function to each element in one or more arrays, returning a new array of results.

- **Purpose:** Transforms every element in an array by applying a custom LAMBDA function.

- **Formula:** MAP(array1, [array2, ...], lambda)
  - **array1, array2, ...** are the arrays or ranges to map over. All arrays must have the same dimensions.
  - **lambda** is the LAMBDA function applied to each element (or set of corresponding elements).

- **Example Usage:**
  - =MAP(A1:A5, LAMBDA(x, x * 2)) doubles each value in the range.
  - =MAP(A1:A5, B1:B5, LAMBDA(price, qty, price * qty)) multiplies corresponding prices and quantities.
  - =MAP(A1:A5, LAMBDA(x, IF(x >= 50, "Pass", "Fail"))) classifies each value.

## R

### [REDUCE](./logical-functions/reduce.md)
Reduces an array to a single accumulated value by applying a LAMBDA function cumulatively to each element.

- **Purpose:** Accumulates array elements into a single result using a custom LAMBDA function with an accumulator.

- **Formula:** REDUCE(initial_value, array, lambda)
  - **initial_value** is the starting value for the accumulator.
  - **array** is the array or range to reduce.
  - **lambda** is a LAMBDA with two parameters (accumulator and current element) that returns the updated accumulator.

- **Example Usage:**
  - =REDUCE(0, A1:A5, LAMBDA(acc, x, acc + x)) sums all values in the range.
  - =REDUCE(1, A1:A5, LAMBDA(acc, x, acc * x)) calculates the product of all values.
  - =REDUCE(0, A1:A10, LAMBDA(acc, x, IF(x > 50, acc + 1, acc))) counts values greater than 50.

## O

### [OR](./logical-functions/or.md)
Returns TRUE if any of the arguments evaluate to TRUE; otherwise, returns FALSE.

- **Purpose:** Evaluates multiple conditions and returns TRUE if at least one argument is TRUE.

- **Formula:** OR(logical1, [logical2], ...)
  - **logical1, logical2, ...** are the conditions or expressions to evaluate. Each must return either TRUE or FALSE.

- **Example Usage:**
  - =OR(TRUE, FALSE, FALSE) returns TRUE (at least one argument is TRUE).
  - =OR(FALSE, FALSE, FALSE) returns FALSE (none of the arguments are TRUE).
  - =OR(A1 > 5, B1 = 10) returns TRUE if A1 is greater than 5 or B1 equals 10.

## S

### [SCAN](./logical-functions/scan.md)
Applies a LAMBDA function cumulatively to each element of an array, returning an array of all intermediate accumulated values.

- **Purpose:** Builds cumulative results by processing each element with an accumulator and a custom LAMBDA function, returning every intermediate state.

- **Formula:** SCAN(initial_value, array, lambda)
  - **initial_value** is the starting value for the accumulator.
  - **array** is the array or range to scan over.
  - **lambda** is a LAMBDA with two parameters (accumulator and current element) that returns the updated accumulator.

- **Example Usage:**
  - =SCAN(0, A1:A5, LAMBDA(acc, x, acc + x)) returns a running total of the values.
  - =SCAN(1, A1:A5, LAMBDA(acc, x, acc * x)) returns cumulative products.
  - =SCAN(0, A1:A10, LAMBDA(acc, x, IF(x > 50, acc + 1, acc))) returns a running count of values greater than 50.

### [SWITCH](./logical-functions/switch.md)
Evaluates an expression and matches it to a list of values, returning the result corresponding to the first match. If
there’s no match, returns an optional default value.

- **Purpose:** Evaluates an expression against a list of values and returns the corresponding result, or a default value
  if no match is found.

- **Formula:** SWITCH(expression, value1, result1, [value2, result2], ..., [default])
  - **expression** is the input value to evaluate.
  - **value1, value2, ...** are possible values to match against the expression.
  - **result1, result2, ...** are the values to return for the matching value.
  - **default** is an optional value returned if no match is found.

- **Example Usage:**
  - =SWITCH(2, 1, "One", 2, "Two", 3, "Three", "None") returns "Two" (expression matches 2).
  - =SWITCH("B", "A", "Apple", "B", "Banana", "C", "Cherry", "Unknown") returns "Banana" (expression matches "B").
  - =SWITCH(5, 1, "Low", 10, "High", "Out of Range") returns "Out of Range" (no match, returns default).


## X

### [XOR](./logical-functions/xor.md)
Returns TRUE if an odd number of the arguments evaluate to TRUE; otherwise, returns FALSE.

- **Purpose:** Evaluates multiple conditions and returns TRUE only if an odd number of arguments are TRUE.

- **Formula:** XOR(logical1, [logical2], ...)
  - **logical1, logical2, ...** are the conditions or expressions to evaluate. Each must return either TRUE or FALSE.

- **Example Usage:**
  - =XOR(TRUE, FALSE, TRUE) returns TRUE (an odd number of arguments are TRUE).
  - =XOR(FALSE, FALSE, TRUE) returns TRUE (one argument is TRUE).
  - =XOR(FALSE, FALSE) returns FALSE (no arguments are TRUE).
  - =XOR(TRUE, TRUE) returns FALSE (an even number of arguments are TRUE).