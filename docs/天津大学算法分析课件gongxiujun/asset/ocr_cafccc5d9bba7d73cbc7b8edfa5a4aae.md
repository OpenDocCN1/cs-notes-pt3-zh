# Step 3. Defining an optimal value function

![](bbox=[0.265, 0.138, 0.741, 0.285])

We have known that a subproblem is constrained by two parameters: number of items and capacities.

+   - For a given subproblem with items \(i, i+1, \cdots, n\) and capacities \(y\), we define its optimal value by \(f(i,y)\).
+   - \(f(n,0)=0\), and \(f(n,w_n)=p_n\) if \(w_n<c\) else 0
+   - \(f(1,c)\) is our goal, why?