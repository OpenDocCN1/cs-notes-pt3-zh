# § 5 Checking Your Analysis

Method 1

+   - When T(N) = O(N), check if T(2N)/T(N) ≈ 2
+   - When T(N) = O(N²), check if T(2N)/T(N) ≈ 4
+   - When T(N) = O(N³), check if T(2N)/T(N) ≈ 8
+   - … …

Method 2

When T(N) = O(f(N)), check if
lim_{N→∞} T(N)/f(N) ≈ Constant

Read the example given on p.28 (Figures 2.12 & 2.13).