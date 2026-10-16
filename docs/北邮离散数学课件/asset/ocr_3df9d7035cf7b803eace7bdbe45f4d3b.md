# A More Verbose Version

Uses some number theory we haven’t defined yet.

Suppose n² is even ∴ 2|n² ∴ n² mod 2 = 0. Of course n mod 2 is either 0 or 1. If it’s 1, then n≡1 (mod 2), so n²≡1 (mod 2), using the theorem that if a≡b (mod m) and c≡d (mod m) then ac≡bd (mod m), with a=c=n and b=d=1. Now n²≡1 (mod 2) implies that n² mod 2 = 1. So by the hypothetical syllogism rule, (n mod 2 = 1) implies (n² mod 2 = 1). Since we know n² mod 2 = 0 ≠ 1, by modus tollens we know that n mod 2 ≠ 1. So by disjunctive syllogism we have that n mod 2 = 0 ∴ 2|n ∴ n is even.