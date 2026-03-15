<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CONVERT Function

The `CONVERT` function in Excel is used to convert a number from one measurement system to another. This function can be especially useful for tasks like converting units of distance, time, weight, temperature, pressure, and more.

### Syntax:

    CONVERT(number, from_unit, to_unit)


- **number**: The numeric value you want to convert.
- **from_unit**: The unit for the number you're converting from.
- **to_unit**: The unit you want to convert to.

### Examples:

1. `=CONVERT(100, "km", "mi")` would convert 100 kilometers to miles.
2. `=CONVERT(32, "C", "F")` would convert 32 degrees Celsius to Fahrenheit.
3. `=CONVERT(1, "gal", "l")` would convert 1 US gallon to liters.

> **Note**: Excel provides a vast array of unit strings for the `from_unit` and `to_unit` arguments, covering categories like distance, temperature, weight, time, and many others. Ensure to use the correct unit strings and to verify that the conversion you're attempting is supported by the `CONVERT` function.