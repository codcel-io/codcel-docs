<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## Type Conversions

## Excel Formulas

Excel's formula language does not enforce data types for cell values, which means it's not strongly typed. Types are
inferred based on context.

For instance, the formula below doesn't require cell types to be declared:

    =A1 + A2

Excel attempts to interpret `A1` and `A2` as numbers automatically.

Excel formulas are "loosely typed", with the application interpreting cell data types on-the-fly.

In Excel it is possible to write:

    ="10" + 20

and it will give you the answer 30.

In most programming languages this would not be possible.

It can be inferred that Excel is not "strongly typed" and can be referred to as "loosely typed".

## Codcel Generated Calculations

Codcel generated calculations are "strongly typed" which goes against the paradigm of Excel's "loosely typed" system.

However, to overcome the differences, Codcel will try to find the correct type for the Excel type at code generation
time. If this is not possible, Codcel will perform a conversion on-the-fly at runtime. This may have an impact on
performance, so
it is important to know how Codcel performs the conversions compared to Excel and by doing so you may be able to improve
your Excel formulas to avoid these situations.

The way Codcel performs these type conversions may lead to different results for a calculation. To avoid differences it
is important to understand this part of the documentation.

Before, we go into the ways Codcel performs type conversions it is important for you to understand why Codcel produces
code that is "strongly typed".

### The advantages of "Strongly Typed" code

- **Early Error Detection:**
  Compile-time error checking prevents type mismatches, such as using an integer where a string is required, unless
  explicitly converted.

    ```
    // Strongly typed languages would prevent this error at compile time
    int number = "string"; // Error: Type mismatch
  ```

- **Self-documenting Code:**
  Declared types within the code clarify the intended use of data, enhancing readability and maintenance.

  ```
  // In TypeScript
  let userID: number; // Clearly an integer
  let userName: string; // Clearly a string
  ```

- **Consistency:**
  Types are enforced consistently, leading to more predictable and stable code behavior.

  ```
  // In Swift
  var userScore: Int = 100 // userScore will always be an integer
  ```

- **Reliability:**
  Early detection of type issues leads to fewer runtime bugs and more robust programs.

  ```
  // In Java
  String count = "25";
  // In a strongly typed language, this would not compile
  int total = count + 5; // Error: Cannot add `int` to `String`
  ```

- **Optimization:**
  Compilers can perform more effective optimizations knowing the specific types being used.

  ```
  // In Rust
  // Rust uses strong typing to perform various compile-time optimizations
  let is_active: bool = true;
  ```

- **Tooling Support:**
  Strong types improve tool capabilities like autocompletion, refactoring, and error detection.

  ```
  // In C#
  // Tools can provide relevant autocompletions and checks based on the type
  DateTime startDate;
  ```

- **Interoperability:**
  Clear data type contracts aid in the reliable exchange of data with external systems.

  ```
  // In Go
  // A strongly typed function signature
  func AddNumbers(a int, b int) int {
      return a + b
   }
   ```

- **Safety:**
  Strong typing can prevent bugs, especially in system-level programming, and support security measures.

  ```
  -- In Haskell
  -- Uses strong type systems to ensure safety
  safeDivide :: Int -> Int -> Maybe Int
  safeDivide _ 0 = Nothing
  safeDivide x y = Just (x `div` y)
  ```

## Codcel Supported Data Types

Codcel can work with several data types:

- **Integer**: This is a 32-bit whole number. For instance, `1`.
- **Float**: A 64-bit floating-point number with double precision, like `3.14`.
- **String**: A UTF-8 encoded sequence of characters. Example: `"Hello World!"`.
- **Boolean**: Represents a true or false value. For example: `true`.

## Codcel Type Conversions

Codcel automatically determines the correct data type during the compile time. If it's not possible, it attempts to do so at runtime.

**Note**: If the correct type is not identified at runtime, this might cause an error in your calculations.

### Best Practices for Type Conversions

To minimize errors, it's best to reduce the number of type conversions in your Excel formulas. For example, use `=2 + 2` instead of `=2 + "2"`, as the latter forces a conversion from a String to a number.

Ensure there are no cells in your Excel formula showing the "#VALUE!" error. These errors need correction before using Codcel code generation.

### Rules for Type Conversions

#### To Float

- String to Float
  - `"2.2"` converts to `2.2`
  - `"2"` converts to `2.0`
  - `"2,2"` converts to `2.2` (if `,` is set as the decimal separator)
- Integer to Float
  - `2` converts to `2.0`
- Boolean to Float
  - `FALSE` converts to `0.0`
  - `TRUE` converts to `1.0`

#### To String

- Float to String
  - `2.2` converts to `"2.2"`
  - `2.2` converts to `"2,2"` (if `,` is the decimal separator)
- Integer to String
  - `2` converts to `"2"`
- Boolean to String
  - `TRUE` converts to `"TRUE"`
  - `FALSE` converts to `"FALSE"`

#### To Integer

- Float to Integer
  - `2.7` converts to `2` (truncated towards zero)
- String to Integer
  - `"2"` converts to `2`
- Boolean to Integer
  - `TRUE` converts to `1`
  - `FALSE` converts to `0`

#### To Boolean

- Float to Boolean
  - `0.0` converts to `FALSE`
  - Any non-zero value converts to `TRUE`
- String to Boolean
  - `"TRUE"` converts to `TRUE`
  - `"FALSE"` converts to `FALSE`
- Integer to Boolean
  - `0` converts to `FALSE`
  - Any non-zero value converts to `TRUE`

## Differences Between Codcel and Excel in Type Conversions

Understanding how Codcel differs from Excel in handling type conversions requires exploring how Excel operates. Let's look at some examples:


Example 1:

A simple plus example:

|     | A        | B   | C   |
|-----|----------|-----|-----|
| 1   |          |     |     |
| 2   | =2 + "2" |     |     |
| 3   |          |     |     |

The calculation at A2, will give the answer 4 in Excel and Codcel.

Example 2:

In the next simple plus example:

|     | A       | B   | C   |
|-----|---------|-----|-----|
| 1   |         |     |     |
| 2   | =2 + B1 | "2" |     |
| 3   |         |     |     |

In Excel the formula at A2 will give a #VALUE! error.

**Note:** However, Codcel will always try to convert to the correct type. In this example, Codcel will give the result 4.

Example 3:

In this simple plus example:

|     | A            | B   | C   |
|-----|--------------|-----|-----|
| 1   |              |     |     |
| 2   | =2 + "Hello" |     |     |
| 3   |              |     |     |

As expected in Excel the formula at A2 will give the error: #VALUE!.

In Codcel this will be caught at compile time, and an error will be given.

However, if the formula contains a user input or external call then at runtime an error message will be shown and the
calculation will not be performed:

    Cannot convert "Hello" to a number

Example 3 makes sense, but Excel works differently if it is expecting a range of cells.

## Cell ranges

In Excel if a range of cells is used in a calculation, then invalid values may be ignored.
An example of such a formula is "SUM":

SUM(number1, [number2], ...)

Example 4:

|     | A                | B   | C   |
|-----|------------------|-----|-----|
| 1   |                  |     |     |
| 2   | =SUM(2; "Hello") |     |     |
| 3   |                  |     |     |

In example 4 at cell A2, Excel will raise an error: #VALUE!. However, in Example 5 it will not
raise an error:

Example 5:

|     | A              | B       | C   |
|-----|----------------|---------|-----|
| 1   |                | "Hello" |     |
| 2   | =SUM(2; B1; 2) |         |     |
| 3   |                |         |     |

Here, the result of A2 will be 4. Here the value "Hello" at cell B1 is simply ignored, and the SUM is calculated by 2
and 2.

Example 6:

|     | A                     | B   | C   |
|-----|-----------------------|-----|-----|
| 1   |                       |     |     |
| 2   | =SUM(2; TRUE; "6"; 1) |     |     |
| 3   |                       |     |     |

Interestingly in Example 6, the result is 10.  It is 2 + (TRUE is 1) + 6 + 1 = 10.

However, in Example 7, if you move TRUE and "6" into separate cells they are ignored.

Example 7:

|     | A                  | B   | C    |
|-----|--------------------|-----|------|
| 1   |                    |     | "6"  |
| 2   | =SUM(2; C2; C1; 1) |     | TRUE |
| 3   |                    |     |      |

In Example 7, SUM will give the answer 3, because "6" and TRUE are ignored.

In Codcel Example 7 and Example 6 the value will be 10.  Codcel will always do type conversion where possible.

How does Codcel handle Example 4 and Example 5.  To recap, Example 4 raised an error and Example 5 did not:

Example 4:

|     | A                | B   | C   |
|-----|------------------|-----|-----|
| 1   |                  |     |     |
| 2   | =SUM(2; "Hello") |     |     |
| 3   |                  |     |     |

Example 5:

|     | A              | B       | C   |
|-----|----------------|---------|-----|
| 1   |                | "Hello" |     |
| 2   | =SUM(2; B1; 2) |         |     |
| 3   |                |         |     |

As stated Codcel will always try to convert a type, however "Hello" cannot be converted to a number.

Should Codcel just ignore "Hello" as in Example 5 or should it raise an error as in example 4?

To solve this problem, Codcel has an option called strict-type-conversion.  If it is set to true, then "Hello" will not be ignored an error will be raised.  

However, if strict-type-conversion is set to false then "Hello" will be ignored and the calculation will be performed.

**Note:** The default setting for strict-type-conversion is false.

## strict-type-conversion set to true

Example 4:

|     | A                | B   | C   |
|-----|------------------|-----|-----|
| 1   |                  |     |     |
| 2   | =SUM(2; "Hello") |     |     |
| 3   |                  |     |     |

In this Example 4 an error will be raised. 

Example 5:

|     | A              | B       | C   |
|-----|----------------|---------|-----|
| 1   |                | "Hello" |     |
| 2   | =SUM(2; B1; 2) |         |     |
| 3   |                |         |     |

In this Example 5 an error will be raised.

Example 6:

|     | A                     | B   | C   |
|-----|-----------------------|-----|-----|
| 1   |                       |     |     |
| 2   | =SUM(2; TRUE; "6"; 1) |     |     |
| 3   |                       |     |     |

Example 7:

|     | A                  | B   | C    |
|-----|--------------------|-----|------|
| 1   |                    |     | "6"  |
| 2   | =SUM(2; C2; C1; 1) |     | TRUE |
| 3   |                    |     |      |

Just to clarify in Example 6 and Example 7, the result will be 10.  Codcel will always perform type conversions where it is possible.

## strict-type-conversion set to false

Example 4:

|     | A                | B   | C   |
|-----|------------------|-----|-----|
| 1   |                  |     |     |
| 2   | =SUM(2; "Hello") |     |     |
| 3   |                  |     |     |

In this Example 4 the result will be 2.  Codcel will ignore "Hello".

Example 5:

|     | A              | B       | C   |
|-----|----------------|---------|-----|
| 1   |                | "Hello" |     |
| 2   | =SUM(2; B1; 2) |         |     |
| 3   |                |         |     |

In this Example 5 the result will be 4.  Codcel will ignore "Hello".

Example 6:

|     | A                     | B   | C   |
|-----|-----------------------|-----|-----|
| 1   |                       |     |     |
| 2   | =SUM(2; TRUE; "6"; 1) |     |     |
| 3   |                       |     |     |

Example 7:

|     | A                  | B   | C    |
|-----|--------------------|-----|------|
| 1   |                    |     | "6"  |
| 2   | =SUM(2; C2; C1; 1) |     | TRUE |
| 3   |                    |     |      |

Just to clarify in Example 6 and Example 7, the result will be 10.  Codcel will always perform type conversions where it is possible.

**Note:**: Due to the differences between the way Excel and Codcel handle types, there may be test results that do not match the test results in Excel.  However, by correctly using the correct types in Excel to start with, these should be generally avoided.