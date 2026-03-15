<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# CRUD Tables

Codcel tables are **read-only by default** to protect data integrity and prevent accidental changes.  
However, you can explicitly mark any table as a **CRUD table** to enable full database operations.

CRUD stands for the four fundamental operations:

- **Create** — insert new rows  
- **Read** — query and list rows  
- **Update** — modify existing rows  
- **Delete** — remove rows  

When a table is designated as a CRUD table, Codcel automatically generates a set of ready-to-use functions for managing data.

---

## Generated Functions

Codcel creates these functions for each CRUD table:

| Operation | Description |
|------------|-------------|
| **Add Row** | Inserts a new record into the table |
| **Read Row** | Returns a row as a list (vector) |
| **Get Row** | Returns a row as an object (key/value) |
| **Update Row** | Updates an existing record |
| **Delete Row** | Removes a record from the table |

---

## Setting Up a CRUD Table

Here’s an example of a `Persons` table in Excel:

|   | A        | B           | C                   | D                 | E         |
|---|----------|-------------|---------------------|-------------------|-----------|
| 1 | **Name** | **Surname** | **Email**           | **Date of Birth** | **Phone** |
| 2 | John     | Smith       | john.s@example.com  | 1985-03-15        | 555-0123  |
| 3 | Sarah    | Johnson     | sarah.j@example.com | 1990-07-22        | 555-0456  |
| 4 | Michael  | Brown       | mike.b@example.com  | 1978-11-30        | 555-0789  |

```
---- SHEET: Persons ----
```

To mark it as a CRUD table in Codcel, use this syntax:

```
*T*Persons!A1:Persons!E4*CRUD*I*Persons
```

### Syntax Breakdown

| Symbol | Meaning |
|--------|----------|
| `*T*` | Declares this as a CRUD table statement |
| `Persons!A1:Persons!E4` | Range of the table (top row = headers, must be unique across Excel) |
| `*CRUD*` | Specifies which CRUD operations are enabled (`*CRU*` = no delete, `*CU*` = create & update only) |
| `*I*` | *(Optional)* If included, rows (2–4 in this example) are **inserted into the database** during creation |
| `Persons` | The name of the database table |

---

## Example REST API Endpoints

When Codcel generates the Excel into code, Codcel can generate these
as functions in different languages such as Rust, Java, C# and more.

However for this example we will use the RESTful service endpoints that Codcel generates:

### Add Persons Row

**URL:**  
`POST http://localhost:3030/add_persons_row`

**Request:**
```json
{
  "date_of_birth": "1985-03-15T00:00:00Z",
  "email": "john.s@example.com",
  "name": "John",
  "phone": "555-0123",
  "surname": "Smith"
}
```

**Response:**
```json
{
  "add_persons_row": "8f05df76-d09e-45a0-9fd2-a5ef7d982df6"
}
```
Returns the **Codcel ID** of the newly created record.

---

### Read Persons Row

**URL:**  
`POST http://localhost:3030/read_persons_row`

**Request:**
```json
{
  "codcel_id": "8f05df76-d09e-45a0-9fd2-a5ef7d982df6"
}
```

**Response:**
```json
{
  "read_persons_row": [
    "8f05df76-d09e-45a0-9fd2-a5ef7d982df6",
    "John",
    "Smith",
    "john.s@example.com",
    "31121",
    "555-0123"
  ]
}
```

> The first item is the Codcel ID; the rest follow the header order.

---

### Get Persons Row

**URL:**  
`POST http://localhost:3030/get_persons_row`

**Response:**
```json
{
  "name": "John",
  "surname": "Smith",
  "email": "john.s@example.com",
  "date_of_birth": "1985-03-15T00:00:00Z",
  "phone": "555-0123"
}
```

---

### Update Persons Row

**URL:**  
`POST http://localhost:3030/update_persons_row`

**Request:**
```json
{
  "codcel_id": "8f05df76-d09e-45a0-9fd2-a5ef7d982df6",
  "date_of_birth": "1985-03-15T00:00:00Z",
  "email": "john.s@example.com",
  "name": "John",
  "phone": "555-0123",
  "surname": "Smith"
}
```

**Response:**
```json
{
  "update_persons_row": "8f05df76-d09e-45a0-9fd2-a5ef7d982df6"
}
```

---

### Delete Persons Row

**URL:**  
`POST http://localhost:3030/delete_persons_row`

**Request:**
```json
{
  "codcel_id": "8f05df76-d09e-45a0-9fd2-a5ef7d982df6"
}
```

**Response:**
```json
{
  "delete_persons_row": "8f05df76-d09e-45a0-9fd2-a5ef7d982df6"
}
```

---

## Individual Column Access

Codcel automatically creates endpoint functions for each column:

| Column | Example Endpoint | Returns |
|---------|------------------|----------|
| `name` | `POST /name` | `{"name": "John"}` |
| `surname` | `POST /surname` | `{"surname": "Smith"}` |
| `email` | `POST /email` | `{"email": "john.s@example.com"}` |
| `date_of_birth` | `POST /date_of_birth` | `{"date_of_birth": "1985-03-15T00:00:00Z"}` |
| `phone` | `POST /phone` | `{"phone": "555-0123"}` |

---

## Column Modifiers

Each header can specify **uniqueness** or **optionality**.

| Symbol | Meaning |
|---------|----------|
| `*U*` | Marks the column as **unique** |
| `*X*` | Marks the column as **optional** |

Example:

|   | A        | B           | C              | D                  | E         |
|---|----------|-------------|----------------|--------------------|-----------|
| 1 | **Name** | **Surname** | **\*U\*Email** | **\*X\*Date of Birth** | **Phone** |
| 2 | John     | Smith       | john.s@example.com | 1985-03-15 | 555-0123  |

> Note: If a column is optional, the first row must contain a value so Codcel can infer the data type.

---

## Searching Data

Each row in a CRUD table automatically receives a **Codcel ID**, a unique UUID that identifies that record inside the database.

However, since the Codcel ID does **not exist in the Excel sheet by default**, functions like `FILTER` or `VLOOKUP` cannot use it directly.  
To perform lookups (for example, find a person by email), you must first **add a Codcel ID column** to your table.

To search by another field (e.g., email), use Excel’s built-in functions to retrieve the Codcel ID first, then query the row.

---

### Why Add the Codcel ID Column?

Adding a Codcel ID column allows you to:
- Search for and reference specific rows directly within Excel.
- Use functions like `FILTER`, `MATCH`, or `INDEX` to locate a record.
- Update or delete the correct record via its Codcel ID through the API.

Without the Codcel ID column, Codcel cannot match Excel rows to the corresponding database entries when performing CRUD operations.

---

### Codcel ID Column Rules

When you add a Codcel ID column:

1. The header **must be exactly named** `Codcel Id`.
2. It **must be the first column** in the table.
3. The values must be **text**, not numbers (e.g., `"A"`, `"B"`, `"C"` — not `1`, `2`, `3`).
4. The Codcel IDs you enter are **temporary placeholders**; Codcel automatically replaces them with real UUIDs when inserting into the database.

---

### Example: Persons Table with Codcel ID

|   | A         | B        | C         | D              | E                  | F         |
|---|-----------|----------|-----------|----------------|--------------------|-----------|
| 1 | Codcel Id | **Name** | **Surname** | **\*U\*Email** | **\*X\*Date of Birth** | **Phone** |
| 2 | A         | John     | Smith     | john.s@example.com | 1985-03-15 | 555-0123  |
| 3 | B         | Sarah    | Johnson   | sarah.j@example.com | 1990-07-22 | 555-0456  |
| 4 | C         | Michael  | Brown     | mike.b@example.com | 1978-11-30 | 555-0789  |
```
---- SHEET: Persons ----
```

Codcel will replace `A`, `B`, `C` with UUIDs like `12e849f0-9bf2-4007-8610-c04004c525f5` when inserting into the database.
This ensures every row is securely and uniquely identified — random UUIDs prevent guessing sequential IDs (which could be a security risk).

Example filter formula to find by email:

|   | A | B |
|---|---|---|
| 1 | \*I\*B1\*PersonsEmail | john.s@example.com |
| 3 | \*O\*B3\*FindCodcelIdByPersonsEmail | =FILTER(Persons!A2:A4, Persons!D2:D4=B1) |
```
---- SHEET: Search ----
```

This example:
- Takes the email entered in `B1`
- Filters the `Persons` table by that email
- Returns the matching **Codcel ID** (which can then be used with `Get Persons Row` or `Update Persons Row`)

---

## The Database

CRUD tables in Codcel are backed by **PostgreSQL**, a reliable, ACID-compliant relational database.

Codcel uses PostgreSQL for:
- Transactional integrity  
- Data indexing  
- Full SQL support  
- Scalability and security  

📘 **See also:**  
[PostgreSQL Installation Guide](crud-tables/postgresql-installation.md) — how to install PostgreSQL on macOS, Windows, and Linux.

---

## Running the Generated Code

When executing the generated code, Codcel needs to know where your PostgreSQL database is located.  
This is configured using the **`CODCEL_POSTGRESQL_URL`** environment variable.

### Example

```bash
export CODCEL_POSTGRESQL_URL=postgresql://postgres@localhost:5432/postgres
```

Explanation

- postgresql:// — protocol used to connect to PostgreSQL
- postgres — username (the default PostgreSQL user)
- localhost — host where the database is running
- 5432 — default PostgreSQL port 
- postgres — database name

You can customize the connection string as needed, for example, to include a password or connect to a remote database:

    export CODCEL_POSTGRESQL_URL=postgresql://user:password@db.example.com:5432/mydatabase

# Person's Table in PostgreSQL

Codcel automatically creates both the **database** and its corresponding **tables** in PostgreSQL.  
The database name matches the **project name**, and the tables are generated the first time any Person table function is executed.

> The **first call** may take slightly longer because Codcel is initializing the table structure.  
> Subsequent calls will be much faster, as the schema is already set up.

---

## Viewing the Tables in PostgreSQL

If you have the PostgreSQL command-line tool (`psql`) installed, you can easily inspect the tables created by Codcel.

Assuming your project is called `persons`, open a terminal and run:

```bash
psql persons
```

You should see something like:

```
psql (14.19 (Homebrew))
Type "help" for help.

persons=#
```

---

## Listing All Tables

To list all tables in the database, type:

```
persons=# \dt
```

You should see something similar to:

```
           List of relations
 Schema |        Name        | Type  |  Owner   
--------+--------------------+-------+----------
 public | persons_a2_e2_crud | table | codcel
(1 row)
```

This confirms that Codcel successfully created the **CRUD table** for your Excel sheet.

---

## Inspecting the Table Structure

To view the detailed structure of the table, use the `\d` command:

```
persons=# \d persons_a2_e2_crud
```

You’ll get an output like this:

```
        Table "public.persons_a2_e2_crud"
   Column      |       Type       | Collation | Nullable | Default 
---------------+------------------+-----------+----------+---------
 c0            | text             |           | not null | 
 name          | text             |           | not null | 
 surname       | text             |           | not null | 
 email         | text             |           | not null | 
 date_of_birth | double precision |           | not null | 
 phone         | text             |           | not null | 
```

> The **Codcel ID** is stored internally as the column **`c0`**.  
> This field is automatically generated and acts as the **primary unique identifier** for each row.

---

## Viewing the Table Data

You can query the contents of the table using a standard SQL `SELECT` statement:

```sql
SELECT * FROM persons_a2_e2_crud;
```

Example output:

```
                  c0                  | name | surname |       email        | date_of_birth |  phone   
--------------------------------------+-------+---------+--------------------+---------------+----------
 c8d26484-d27f-43df-87d3-ba409cddcb66 | John  | Smith   | john.s@example.com |         31121 | 555-0123
 cbec9c42-753d-4c48-afa6-21ebc03c86b2 | Sarah | Johnson | sarah.j@example.com|         33015 | 555-0456
 12e849f0-9bf2-4007-8610-c04004c525f5 | Mike  | Brown   | mike.b@example.com |         28931 | 555-0789
```

> **Note:** Dates and times are stored internally as **numeric values** (Excel’s date serial format).  
> Codcel automatically converts these into proper date or timestamp types when accessed through the API or application.

---

## Exiting the PostgreSQL Shell

To quit the PostgreSQL command-line interface, type:

```
\q
```

---

# Database Maintenance and Versioning

Codcel does **not** include built-in tools for managing or maintaining your PostgreSQL database.  
This is intentional — the PostgreSQL ecosystem already provides a wide range of professional tools and workflows for database administration.

---

## Database Maintenance

You can manage your Codcel-generated database using **any standard PostgreSQL toolset**, such as:

- **pgAdmin** — graphical PostgreSQL management tool  
- **psql** — the official command-line interface  
- **DBeaver**, **TablePlus**, or **DataGrip** — third-party SQL editors  
- **SQL scripts** or **migration tools** (Flyway, Liquibase, etc.)  

As the database schema created by Codcel follows standard PostgreSQL conventions, it can be maintained, indexed, and optimized by any **experienced DBA** or developer familiar with SQL.

Example tasks you may perform manually include:
- Adding **indexes** to improve query performance  
- Creating **views** for reporting  
- Managing **roles and permissions**  
- Performing **backups and restores**  

---

## Handling Schema Changes

If you make structural changes to your Excel sheet (for example, add or remove columns in the Person’s table), it’s **not recommended** to modify the existing PostgreSQL table directly.

Instead, the safer approach is to:

1. **Generate a new project** with the updated Excel sheet.  
   For example, if your original project was called `persons`, create a new project named **`persons_v2`**.  
2. Codcel will automatically create a **new database and tables** (e.g., `persons_v2_a2_e2_crud`).  
3. **Manually migrate** your data from the previous version (`persons`) to the new version (`persons_v2`) using standard SQL commands or PostgreSQL tools.  

Example migration steps:

```sql
-- Connect to the persons_v2 database
\c persons_v2;

-- Insert data from the old table (assuming compatible structure)
INSERT INTO persons_v2_a2_e2_crud (name, surname, email, date_of_birth, phone)
SELECT name, surname, email, date_of_birth, phone FROM persons_a2_e2_crud;
```

This versioned approach ensures that:
- Your original project remains stable and reproducible.  
- You can test new changes safely in a separate environment.  
- Database migrations remain under your full control.

---

In short, Codcel focuses on **code and schema generation**, not database lifecycle management — giving you full freedom to use the PostgreSQL administration tools and best practices that suit your environment.

---

## PostgreSQL Engine Details

### Connection Management

The generated code uses connection pooling to manage database connections efficiently. Connections are reused across requests, reducing the overhead of establishing new connections for each operation.

The connection URL is configured via the `CODCEL_POSTGRESQL_URL` environment variable:

```bash
export CODCEL_POSTGRESQL_URL=postgresql://user:password@host:port/database
```

### Type Mapping

Codcel maps Excel data types to PostgreSQL column types:

| Excel Data Type | PostgreSQL Type | Notes |
|----------------|-----------------|-------|
| Text | `text` | Default for string values |
| Integer | `integer` | 32-bit integers |
| Large integer | `bigint` | For values exceeding 32-bit range |
| Decimal | `double precision` | 64-bit floating point |
| Boolean | `boolean` | TRUE/FALSE values |
| Date | `double precision` | Stored as Excel serial numbers; converted by the API |
| Timestamp | `double precision` | Stored as Excel serial numbers; converted by the API |

**Note:** Dates and timestamps are stored as Excel serial numbers internally to maintain exact compatibility with the calculation engine. The generated API automatically converts these to standard date formats in JSON responses.

### Row Identification

Every row in a CRUD table receives a **Codcel ID** -- a UUID generated by the database engine. This ID is stored in the `c0` column and serves as the primary key. UUIDs are used instead of sequential integers for security (preventing ID enumeration attacks).

### Column Naming

Internally, table columns are referenced using a positional naming scheme (`c0`, `c1`, `c2`, etc.) in addition to their header names. The `c0` column always contains the Codcel ID.

---

## See Also

- [Tables Overview](./tables.md) -- comparison of all table types
- [Large Tables](./large-tables.md) -- read-only tables within Excel
- [Massive Tables](./massive-tables.md) -- CSV/Parquet-backed tables for billions of rows
- [Table Functions](./table-functions.md) -- lookup and filtering functions