# # Floating Point in C

# ## C Guarantees Two Levels

+   - **float** single precision
+   - **double** double precision

# ## Conversions/Casting

+   - Casting between `int`, `float`, and `double` changes bit representation
+   - **double/float → int**
+     - Truncates fractional part
+     - Like rounding toward zero
+     - Not defined when out of range or NaN: Generally sets to TMin
+   - **int → double**
+     - Exact conversion, as long as `int` has ≤ 53 bit word size
+   - **int → float**
+     - Will round according to rounding mode