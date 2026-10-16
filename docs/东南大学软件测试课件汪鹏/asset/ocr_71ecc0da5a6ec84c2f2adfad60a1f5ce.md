# # 挑战：测试用例规划

```
class Roots {
    // Solve ax² + bx + c = 0
    public roots(double a, double b, double c)
    { ... }

    // Result: values for x
    double root_one, root_two;
}
```

+   - **Which values for _a_, _b_, _c_ should we test?**
+     - assuming a, b, c were 32-bit integers, we’d have (2³²)³ ≈ 10²⁸ legal inputs
+     - with 1.000.000.000.000 tests/s, we would still require 2.5 billion years