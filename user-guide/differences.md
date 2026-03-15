<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Differences

The generated calculations by Codcel may not produce exactly the same results as in Excel.

We try our best so that the generated calculations match as closely as possible to Excel. However, there are some reasons why this is not always possible.

We do not have access to the source code of Excel, so we do not know exactly how Microsoft performs their calculations. We can only go by the documentation and our own testing.

On every release we run an extensive range of tests to ensure the results are as close as possible. If there are significant changes between each release, these will be documented and the version number will be incremented accordingly.

In the majority of cases the results produced by Excel will be the same as the results produced by Codcel.

Codcel produces test documentation that shows whether the calculations match your Excel calculation. This is the first line of defence and should highlight any initial issues. This is an important feature, but it only works with one test.

We do not guarantee that the calculations are exactly the same as in Excel, and before you deploy a Codcel calculation to production you should perform your own testing.
When you are happy with the tests, it is your responsibility to move the calculation into a production environment.

In this document we will explain where there are potential differences and how to avoid them. We consider Excel to be a "Low Code Programming Language", and as in all programming languages there are best practices that can be followed to avoid pitfalls.

What do I need to know:

- [Type Conversions](./differences/type-conversions.md)
- [Rounding](./differences/rounding.md)
- [Date Handling](./differences/date-handling.md)
- [FORECAST.ETS Precision](./differences/forecast-ets.md)
- [LAMBDA Support](./differences/lambda-support.md)
- [Known Function Differences](./differences/known-function-differences.md)