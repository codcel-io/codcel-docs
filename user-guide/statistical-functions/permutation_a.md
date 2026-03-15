<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PERMUTATIONA Function

The `PERMUTATIONA` function in Excel is used to **return the number of permutations for a given number of objects (with
repetition allowed)** from a total number of objects. This function is typically used in combinatorics to calculate the
number of arrangements when repetition of objects is allowed.

### Key Features of PERMUTATIONA:

- **Permutations with Repetition**: Calculates permutations where repetition of objects is allowed.
- **Useful in Combinatorial Problems**: Helps solve problems in probability, decision-making, and counting outcomes.
- **Order Matters**: Since it calculates permutations, the order of the objects is important.

### Syntax:

```plaintext
PERMUTATIONA(number, number_chosen)
```

- **number**: Required. The total number of objects.
- **number_chosen**: Required. The number of objects to arrange or choose.

### How It Works:

The `PERMUTATIONA` function calculates the result using this formula:

```plaintext
number^number_chosen
```

This represents the total number of ways to arrange `number_chosen` items from a total of `number` objects, with
repetition allowed.

### Examples:

1. **Basic Example**:
   If you have a total of 3 objects and want to arrange them in groups of 2:
   ```excel
   =PERMUTATIONA(3, 2)
   ```
   Result: `9` (since \( 3^2 = 9 \)).

2. **Larger Sets**:
   To calculate the number of ways to arrange 4 objects into groups of 3:
   ```excel
   =PERMUTATIONA(4, 3)
   ```
   Result: `64` (since \( 4^3 = 64 \)).

3. **Single Object**:
   To calculate the permutations of 1 object chosen in groups of 4:
   ```excel
   =PERMUTATIONA(1, 4)
   ```
   Result: `1` (since \( 1^4 = 1 \)).

4. **Full Set Permutations**:
   To calculate all permutations of 5 objects choosing all 5:
   ```excel
   =PERMUTATIONA(5, 5)
   ```
   Result: `3125` (since \( 5^5 = 3125 \)).

### Notes:

- **Input Restrictions**:
    - Both `number` and `number_chosen` must be positive integers.
    - If either argument is non-numeric, Excel will return a `#VALUE!` error.
    - If either argument is negative, Excel will return a `#NUM!` error.

- **Use Case**:
    - Use this when considering permutations **with repetition allowed**. For permutations without repetition, use the
      `PERMUT` function instead.

- **Order Sensitivity**:
    - Permutations differ from combinations in that the order of items matters.

### Applications:

- **Business**: Calculate the number of possible product codes or SKU arrangements when repetition is allowed.
- **Education**: Explore problems in combinatorics, such as permutations in arrangements with repetition.
- **Password Generation**: Determine the number of possible combinations for passwords of a certain length.

> **Tip**: For permutations without repetition, refer to the `PERMUT` function. For combinations (where order does not
> matter), use the `COMBIN` or `COMBINA` functions.