# Quiz

# Algorithm 1.8 Count2

Input: A positive integer n.

Output: count = number of times Step 5 is executed.

+   1. count ← 0;
+   2. for i ← 1 to n
+   3. m ← ⌊n/i⌋
+   4. for j ← 1 to m
+   5. count ← count + 1
+   6. end for
+   7. end for
+   8. return count

A. Θ(n²)    B. Θ(n).

![](bbox=[0.48, 0.68, 0.92, 0.8])