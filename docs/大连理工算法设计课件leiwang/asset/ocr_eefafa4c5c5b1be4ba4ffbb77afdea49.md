# # Minor simplification

+   - For \( n \ge 50 \), we have \( 3\lfloor n/10 \rfloor \ge n/4 \).

+   - Therefore, for \( n \ge 50 \) the recursive call to SELECT in Step 4 is executed recursively on \( \le 3n/4 \) elements.

+   - Thus, the recurrence for running time can assume that Step 4 takes time \( T(3n/4) \) in the worst case.

+   - For \( n < 50 \), we know that the worst-case time is \( T(n) = \Theta(1) \).