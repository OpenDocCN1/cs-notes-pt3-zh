# Conjecture and Proof

Example 6

+   - We know that some numbers of the form 2^p−1 are prime when p is prime.
+     - These are called the Mersenne primes.
+   - Can we prove the inverse, that a^n−1 is composite whenever either a>2, or (a=2 but n is composite)?
+     - All we need is to find a factor greater than 1.
+   - Note a^n−1 factors into (a−1)(a^{n−1}+...+a+1).
+     - When a>2, (a−1)>1, and so we have a factor.
+     - When n is composite, ∃r,s>1: n=rs. Thus, given a=2, a^n = 2^n = 2^{rs} = (2^r)^s, and since r>1, 2^r > 2 so 2^n − 1 = b^s−1 with b = 2^r > 2, which now fits the first case.