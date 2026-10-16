# 4.2  The iteration method

+   - **Substitution:** It is difficult to come up with a good guess
+   - **The iteration method**
+     - doesn't require us to guess the answer
+     - may require more **algebra**（迭代法对代数能力的要求较高）
+     - to **expand (iterate)** the recurrence and express it as a **summation of terms**, and the initial conditions
+     - to **evaluate summations.**（不断迭代展开为级数，并求和）

**For example,**  \(T(n)=3T(\lfloor n/4\rfloor)+n\)

```
\[
\begin{aligned}
T(n) &= n + 3T(\lfloor n/4\rfloor) \\
     &= n + 3\left(\lfloor n/4\rfloor + 3T(\lfloor n/16\rfloor)\right) \\
     &= n + 3\left(\lfloor n/4\rfloor + 3\left\lfloor n/16\right\rfloor + 3T(\lfloor n/64\rfloor)\right) \\
     &= n + 3\lfloor n/4\rfloor + 9\lfloor n/16\rfloor + 27T(\lfloor n/64\rfloor)
\end{aligned}
\]
```