# Supplement: Algorithm 2

+   - Mutual exclusion? √
+   - Progress? X
+   - Bounded-waiting? X

# Shared variables

+   - boolean flag[2];
+     initially flag [0] = flag [1] = false.
+   - flag [i] = true ⇒ P_i ready to enter its critical section

# Process P₀

```
do {
  while (flag[1]);
  flag[0] := true;
  critical section
  flag [0] = false;
  remainder section
} while (1);
```

# Process P₁

```
do {
  while (flag[0]);
  flag[1] := true;
  critical section
  flag [1] = false;
  remainder section
} while (1);
```