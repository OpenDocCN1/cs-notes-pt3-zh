At point C, the second assignment statement s ← 0 is executed, the follow assertion is true:

k=0 and s=0  (6)

Now the loop is entered. Before the loop execute, assertion(6) holds k=0 and s=0. By assertion(1), n≥1. so it follows that k≤n is required. Because k=0, it follows k-1=-1, so the sum in (4) is empty s=0. there for loop invariant (4) is true just before the first loop is entered.

Now, assume that, at some stage during the execution of the code fragment, the loop invariant holds. That is k to some value k₀, 0≤k₀≤n,

D : k₀≤n and s=y[0]+y[1]+...+y[k₀-1]  (7)

We should to prove execute the code fragment, the loop invariant is still true or get the output specification.