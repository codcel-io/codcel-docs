<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## RIGHTB Function

The `RIGHTB` function in Excel is a text function that allows users to extract a specified number of bytes from the
end (right side) of a text string. It is the byte-based counterpart of the `RIGHT` function. In single-byte character
set (SBCS) languages like English, `RIGHTB` behaves identically to `RIGHT`. In double-byte character set (DBCS)
languages such as Japanese, Chinese, and Korean, each double-byte character is counted as 2 bytes, making the
distinction important.

### Syntax:

    RIGHTB(text, [num_bytes])

- **text**: The text string from which you want to extract characters. This can be a direct string, a cell reference, or
  the result of another function.
- **num_bytes** (optional): The number of bytes to extract starting from the right side of the string. If omitted,
  it defaults to 1, meaning only the last byte will be extracted.

### Key Details:

- If `num_bytes` is greater than the byte length of the text string, the `RIGHTB` function will return the entire string
  without any error.
- If `num_bytes` is set to 0, the result will be an empty string (`""`).
- If `num_bytes` is negative or not an integer, Excel will return a `#VALUE!` error.
- In SBCS languages (e.g., English), `RIGHTB` returns the same results as `RIGHT` because each character equals one
  byte. The difference only becomes apparent in DBCS languages where characters may occupy two bytes.

### Examples:

1. **Extracting the Last Three Bytes**:
    ```excel
    =RIGHTB("Excel", 3)
    ```
   This formula will return `"cel"`, which are the last three bytes of the text "Excel" (in an SBCS environment, this
   is equivalent to the last 3 characters).

2. **Default Behavior (Extracting the Last Byte)**:
    ```excel
    =RIGHTB("Excel")
    ```
   Since `num_bytes` is omitted, the formula will return `"l"`, the last byte of the text string "Excel".

3. **Using a Cell Reference**:
   If cell A1 contains the text "Product123", the formula:
    ```excel
    =RIGHTB(A1, 3)
    ```
   will return `"123"`, extracting the last 3 bytes from the value in cell A1.

4. **Combining with Other Functions**:
   You can use `RIGHTB` in combination with other functions. For example:
    ```excel
    =RIGHTB(A1, LENB(A1) - FINDB("-", A1))
    ```
   This formula extracts all bytes after a hyphen ("-") in a string. It calculates the number of bytes to
   extract based on the byte position of the hyphen.

5. **Handling Too Many Bytes**:
   If you try to extract more bytes than are available in the string, the `RIGHTB` function will still return the
   full string. For example:
    ```excel
    =RIGHTB("Excel", 10)
    ```
   will return `"Excel"` even though the text string contains fewer than 10 bytes.

### Notes:

- The `RIGHTB` function is case-sensitive and returns the characters exactly as they appear in the text string.
- It is commonly used in data parsing tasks involving DBCS text, such as extracting suffixes or parts of product codes
  where byte positions matter.
- The `num_bytes` argument counts bytes, not characters. When working with DBCS text, be mindful that a double-byte
  character occupies positions for two bytes.
- For character-based extraction from the right (rather than byte-based), use the `RIGHT` function.
- The `RIGHTB` function is equivalent to `RIGHT` in Excel when the default language setting is a single-byte character
  set language. In DBCS language environments, `RIGHTB` counts each double-byte character as 2 bytes.

By combining `RIGHTB` with other byte-based functions like `LENB` and `FINDB`, you can perform advanced text string
manipulations with ease in DBCS language environments.