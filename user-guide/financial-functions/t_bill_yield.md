<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TBILLYIELD Function

The `TBILLYIELD` function in Excel calculates the **yield for a Treasury bill (T-bill)** based on its price. This is
useful for investors to evaluate the annualized return on T-bills in financial markets.

### Key Features of TBILLYIELD:

- Computes the annual yield for a Treasury bill as a percentage.
- Assumes a 360-day year for calculation purposes.
- Ideal for determining the return on investment when purchasing T-bills.

### Syntax:

```plaintext
TBILLYIELD(settlement, maturity, price)
```

- **settlement**: The settlement date of the T-bill (the date the investor buys the bill).  
  This must be a valid Excel date.
- **maturity**: The maturity date of the T-bill (the date the bill is redeemed).  
  This must also be a valid Excel date later than the settlement date.
- **price**: The price per $100 face value of the T-bill, entered as a number (e.g., `97.50`).

### Examples:

1. **Basic T-Bill Yield**:
   `=TBILLYIELD(DATE(2023, 1, 1), DATE(2023, 7, 1), 97.50)`  
   Calculates the annualized yield for a T-bill purchased on January 1, 2023, with a price of $97.50, and maturing on
   July 1, 2023.  
   **Result**: `5.02%`.

2. **T-Bill with Lower Price**:
   `=TBILLYIELD(DATE(2023, 5, 1), DATE(2023, 11, 1), 96.50)`  
   Determines the yield for a T-bill bought at $96.50, purchased on May 1, 2023, and maturing on November 1, 2023.  
   **Result**: `7.23%`.

3. **Shorter Term T-Bill**:
   `=TBILLYIELD(DATE(2023, 8, 1), DATE(2023, 9, 1), 99.75)`  
   Calculates the yield for a 1-month T-bill purchased at $99.75, with a maturity of September 1, 2023.  
   **Result**: `3.00%`.

### Notes:

- The formula for the T-bill yield is based on the price and remaining term of the T-bill:
  ```plaintext
  TBILLYIELD = ((100 − Price) / Price) × (360 / Days to Maturity)
  ```
  Where **Days to Maturity** is the difference in days between **maturity** and **settlement**.
- Both **settlement** and **maturity** dates must be valid Excel dates.
- The **maturity date** must always be later than the **settlement date**.

> **Tips**:
> - Use `TBILLYIELD` to calculate the return on investment for Treasury bills.
> - Ensure input dates and prices are correct to avoid errors in Excel.
> - T-bills are a government-backed, low-risk investment, making them ideal for short-term saving goals.