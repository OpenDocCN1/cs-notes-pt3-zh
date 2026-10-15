Pass to the test box. If k₀≥n, then because k₀≤n by hypothesis, it follows that k₀=n, this implies that

H: K₀=n and s=y[0]+y[1]+...+y[n-1] (8)

Just the output specification(3).

On the other hand, k₀<n, and (7), becomes

E: k₀<n and s=y[0]+y[1]+...+y[k₀-1] (9)

Just the assertion of E, then the statement s ← s+y[k₀] is executed, the point F is

F: k₀<n and s= y[0]+y[1]+...+y[k₀-1]+y[k₀] = y[0]+y[1]+...+y[k₀] (10)

The next statement to be executed is k₀ ← k₀+1. then because before increasing k₀<n, now k₀ ≤n. and (10) becomes

G: k₀ ≤ n and s= y[0]+y[1]+...+y[k₀-1] (11)