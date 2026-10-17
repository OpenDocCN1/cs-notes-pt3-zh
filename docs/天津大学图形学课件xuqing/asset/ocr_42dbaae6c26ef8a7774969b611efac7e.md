# # B-Spline Curves

+   - Continuity: C<sub>2</sub> or higher

+   - including
+     - uniform
+     - Non-uniform
+     - NURBS

```
\(P(u) = \sum_{k=0}^n p_k B_{k,d}(u)\)
\(u_{min} \le u \le u_{max}\)
\(2 \le d \le n + 1\)
```

```
\(B_{k,1}(u) = \begin{cases} 1 & u_k \le u \le u_{k+1} \\ 0 & otherwise \end{cases}\)
```

```
\(B_{k,d}(u) = \frac{u - u_k}{u_{k+d-1} - u_k} B_{k,d-1}(u) + \frac{u_{k+d} - u}{u_{k+d} - u_{k+1}} B_{k+1,d-1}(u)\)
```