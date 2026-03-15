<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SORTBY Function

The `SORTBY` function in Excel allows you to sort the contents of a range or array based on the values in one or more
other ranges or arrays. This function is particularly useful when you need to sort one dataset according to the values
of another dataset.

### Syntax

```excel
SORTBY(array, by_array1, [sort_order1], [...], [by_array_n, [sort_order_n]])
```

- **array**: The array or range to be sorted.
- **by_array1**: The first array or range to sort by.
- **sort_order1**: (Optional) The order to sort by. Use `1` for ascending (default) and `-1` for descending.
- **by_array_n**: (Optional) Additional arrays or ranges to sort by.
- **sort_order_n**: (Optional) The order to sort the additional arrays or ranges.

### Examples

1. **Sort a range by a single criterion**

   To sort the range `A2:B5` by the values in column `B` in ascending order:

   ```excel
   =SORTBY(A2:B5, B2:B5, 1)
   ```

2. **Sort a range by multiple criteria**

   To sort the range `A2:C5` by the values in column `B` in ascending order and then by values in column `C` in
   descending order:

   ```excel
   =SORTBY(A2:C5, B2:B5, 1, C2:C5, -1)
   ```

### Notes

- If the `array` size does not match any `by_array` size, Excel will return a `#VALUE!` error.
- The `SORTBY` function helps in arranging data dynamically and is particularly useful when combined with other
  functions like `FILTER`.

### Usage Tips

- Combine `SORTBY` with `UNIQUE` to get a sorted list of unique values.
- Use in conjunction with `FILTER` for more complex data manipulation and analysis tasks.

By understanding and utilizing the `SORTBY` function, you can efficiently manage and analyze your data, making it a
powerful tool in your Excel toolkit.