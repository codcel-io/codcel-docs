<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TBILLEQ Function

The `TBILLEQ` function in Excel calculates the **equivalent annual yield** for a Treasury bill (T-bill) based on its
discount rate. This allows the comparison of T-bill yields to other investments with annual yields.

### Key Features of TBILLEQ:

- Computes the equivalent annual yield for short-term securities like T-bills.
- Useful for comparing the yields of T-bills with other investments.
- Assumes a 360-day year for calculation purposes.

### Syntax:

```plaintext
TBILLEQ(settlement, maturity, discount)
```

- **settlement**: The settlement date of the T-bill (the date the investor buys the bill).  
  This must be a valid Excel date.
- **maturity**: The maturity date of the T-bill (the date the bill is redeemed).  
  This must also be a valid Excel date later than the settlement date.
- **discount**: The discount rate of the T-bill (expressed as a decimal or percentage).

### Examples:

1. **Basic T-Bill Equivalent Yield**:
   `=TBILLEQ(DATE(2023, 1, 1), DATE(2023, 7, 1), 0.05)`  
   Calculates the equivalent annual yield for a T-bill with a discount rate of 5% purchased on January 1, 2023, and
   maturing on July 1, 2023.  
   **Result**: `0.0513` (equivalent to 5.13%).

2. **T-Bill with Higher Discount Rate**:
   `=TBILLEQ(DATE(2023, 5, 1), DATE(2023, 11, 1), 0.07)`  
   Determines the equivalent annual yield for a T-bill with a 7% discount rate, a purchase date of May 1, 2023, and a
   maturity date of November 1, 2023.  
   **Result**: `0.0728` (equivalent to 7.28%).

3. **Shorter Term T-Bill**:
   `=TBILLEQ(DATE(2023, 8, 1), DATE(2023, 9, 1), 0.02)`  
   Calculates the equivalent annual yield for a 1-month T-bill with a 2% discount rate, purchased on August 1, 2023.  
   **Result**: `0.0244` (equivalent to 2.44%).

### Notes:

- The formula for equivalent annual yield is based on the actual T-bill terms and uses the following formula:
  ```plaintext
  TBILLEQ = (365 × Discount Rate) / (360 − (Discount Rate × Days to Maturity))
  ```
  Where **Days to Maturity** is the difference in days between **maturity** and **settlement**.
- Both **settlement** and **maturity** dates must be valid and refer to calendar dates.
- The **maturity date** must always occur after the **settlement date**.

> **Tips**:
> - Use `TBILLEQ` to accurately compare short-term T-bill yields with annualized yields from other fixed-income
    investments.
> - Ensure that the inputs are formatted as valid dates and percentages in Excel to avoid errors.
> - Keep in mind that T-bills are considered low-risk, short-term instruments, making them ideal for preserving capital
    in volatile markets.