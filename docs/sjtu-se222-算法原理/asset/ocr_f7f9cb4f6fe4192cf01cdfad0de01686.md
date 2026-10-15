# Quiz

Algorithm 1.7 Count1

Input: $n = 2^k$, for some positive integer $k$.

Output: $count$ = number of times Step 4 is executed.

+   1. $count \leftarrow 0$;
+   2. **while** $n \ge 1$
+   3. **for** $j \leftarrow 1$ **to** $n$
+   4. $count \leftarrow count + 1$
+   5. **end for**
+   6. $n \leftarrow n/2$
+   7. **end while**
+   8. **return** $count$

```
$n + \frac{n}{2} + \frac{n}{2^2} + \cdots + \frac{n}{2^j} + \cdots + \frac{n}{2^{\log n}} = 2n - 1 = \theta(n)$
```