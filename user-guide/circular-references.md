<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Circular References

A circular reference occurs when a formula refers back to its own cell, either directly or through a chain of references. Codcel can detect and resolve circular references using iterative calculation.

---

## Detection

Codcel analyses the dependency graph of all formulas in your workbook using Tarjan's Strongly Connected Components algorithm. This identifies:

- **Direct self-references:** A cell whose formula references itself (e.g., `A1 = A1 + 1`)
- **Indirect cycles:** A chain of cells that eventually reference back to the starting cell (e.g., `A1 → B1 → C1 → A1`)

Cells involved in circular references are grouped together. Each group is resolved independently.

---

## Enabling Iterative Calculation

By default, circular references produce an error. To enable iterative resolution:

1. Open **Settings** in the desktop app
2. Enable **Iterative Calculation**
3. Configure the iteration parameters:

| Setting | Default | Description |
|---------|---------|-------------|
| Maximum Iterations | 100 | The most iterations Codcel will perform per circular group |
| Maximum Change (Convergence Threshold) | 0.001 | Iteration stops when all values change by less than this amount |

Or in `codcel.toml`:

```toml
[formatting]
allow_circular_references = true
circular_max_iterations = 100
circular_convergence_threshold = 0.001
```

Or via the CLI:

```bash
codcel ... --enable-iterative-calculation --maximum-iterations 100 --maximum-change 0.001
```

---

## How It Works

When iterative calculation is enabled, the generated code resolves each circular group as follows:

1. **Initialise** all cells in the group to zero (or their default values)
2. **Evaluate** all formulas in the group
3. **Check convergence:** If the maximum change across all cells is less than the threshold, stop
4. **Repeat** from step 2, up to the maximum number of iterations
5. **Return** the last computed values

If convergence is not reached within the maximum iterations, Codcel uses the last computed values. The calculation does not fail -- it simply stops iterating.

---

## Common Use Cases

Circular references are frequently used in:

- **Financial models:** Goal-seeking calculations where a result feeds back into the inputs
- **Iterative simulations:** Monte Carlo or convergence-based calculations
- **Balancing equations:** Calculations that must satisfy constraints through iteration

---

## Tips

- **Set appropriate iteration limits:** For simple circular references, 100 iterations is usually sufficient. For complex financial models, you may need 200-500.
- **Choose a reasonable threshold:** The default 0.001 works well for most cases. For currency calculations, you may want 0.01. For scientific calculations, you may need 0.00001.
- **Keep circular groups small:** The fewer cells involved in a cycle, the faster convergence.
- **Test with different inputs:** Convergence behaviour can vary depending on input values. Test with a range of inputs to ensure stability.

---

## Troubleshooting

### Convergence Not Reached

If your calculation does not converge:

1. **Increase maximum iterations** -- some models need more iterations
2. **Relax the threshold** -- a larger threshold converges sooner
3. **Check for oscillation** -- if values alternate between two states, the formula may not be suitable for iterative resolution
4. **Simplify the cycle** -- try breaking complex circular references into smaller, independent groups

### Unexpected Results

If the converged values differ from Excel:

1. Ensure Excel has the same iteration settings (File > Options > Formulas > Enable iterative calculation)
2. Match the maximum iterations and convergence threshold between Excel and Codcel
3. Check that all cells in the circular group are included in the transpilation (annotated correctly)

---

## See Also

- [Settings Reference](./settings.md#enable-iterative-calculation) -- iteration settings
- [Differences from Excel](./differences.md) -- other behavioural differences