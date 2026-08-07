<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# Tables

In Codcel, tables are read-only by default. It is possible to specify any table as a
CRUD database table where it is not read-only. CRUD table implementation can be found here:
[CRUD Table Implementation](./crud-tables.md).

In Codcel there are three types of tables:

### [Small Tables](./small-tables.md)
These tables are used when there is a small number of rows, typically in the thousands.

### [Large Tables](./large-tables.md)
Large tables support up to 1,048,576 rows.

### [Massive Tables](./massive-tables.md)
Massive tables are similar to large tables but can support tables with billions of rows.