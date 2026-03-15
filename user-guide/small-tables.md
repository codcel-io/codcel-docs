<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Small Tables

Small tables can contain thousands of rows.

These work just as you would expect a table to work in Excel
and allow for functions inside rows, as shown in cell C3:

|       | A     | B   | C               | D         | E   |
|-------|-------|-----|-----------------|-----------|-----|
| **1** | Name  | Sex | Age             | *I*E1*Age | 20  |
| **2** | Adam  | M   | 22              |           | 10  |
| **3** | Bob   | M   | **=SUM(E1;E2)** |           |     |
| **4** | Kate  | F   | 47              |           |     |
| **5** | Carla | F   | 52              |           |     |

The following [VLOOKUP](./table-functions/vlookup.md):

    =VLOOKUP("Bob"; A2:C5; 3; FALSE)

will find the row **C3** and calculate it. So the result of this lookup will be **30**, which is the sum of 20 and 10.
As shown, a function can even contain input values.

The tables can be placed anywhere, as they are indicated by the range. In this example: **A2:C5**.

> **Note:** If functions and input values are not needed in the small table, and the limitations of the large table are not an issue, it is always better to use a large table, even if the table is small.