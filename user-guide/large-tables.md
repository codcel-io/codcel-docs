<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Large Tables

If you need large tables with up to 1,048,576 rows, then Codcel enforces some limitations.

The limitations in Codcel are:

- One whole sheet must represent only one table.
- The sheet name must start with **T_**, and only table sheets should use this prefix. For example, if the table contained a list of addresses, a suitable sheet name would be **T_Addresses**.
- If the sheet contains functions and calculations, these will be ignored. The values as calculated in Excel will be used. For example, **=SUM(10;20)** will be stored internally as 30 and will never be recalculated. A function in a large table cannot contain an input value, as the input value will change on each call, making it impossible to calculate at import time.
- The first row (**row 1**) must contain the headers of the table. The data rows must follow immediately after.
- The table must start at the first column (**column A**).

An example table for addresses would be called **T_Addresses** and structured as follows:

|       | A        | B                   | C            | D        |
|-------|----------|---------------------|--------------|----------|
| **1** | Postcode | Street              | Town         | District |
| **2** | 1000-100 | Rua Cidade de Horta | Lisbon       | Lisbon   |
| **3** | 2000-100 | Rua Mulagre         | Santarem     | Santarem |
| **4** | 2860-102 | Rua Flamingos       | Alhos Vedras | Setubal  |
| ...   | ...      | ...                 | ...          | ...      |

The following [VLOOKUP](./table-functions/vlookup.md):

    =VLOOKUP("1000-100"; A1:D4; 3; FALSE)

will return the value "Lisbon".

> **Note:** In this example the **table array** range in the **VLOOKUP** of **A1:D4** will be ignored. The whole table is always used.