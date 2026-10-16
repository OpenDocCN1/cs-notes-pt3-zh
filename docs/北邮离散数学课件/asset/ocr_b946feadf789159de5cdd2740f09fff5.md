Although the construction in Theorem 2 provides a general method for solving systems of linear congruences with pairwise relatively prime moduli, it can be easier to solve a system using a different method. Example 6 illustrates the use of a method known as back substitution.

# EXAMPLE 6

Use the method of back substitution to find all integers x such that x ≡ 1 (mod 5), x ≡ 2 (mod 6), and x ≡ 3 (mod 7).

Solution: By Theorem 4 in Section 4.1, the first congruence can be rewritten as an equality, x = 5t + 1 where t is an integer. Substituting this expression for x into the second congruence tells us that

5t + 1 ≡ 2 (mod 6)

which can be easily solved to show that t ≡ 5 (mod 6) (as the reader should verify). Using Theorem 4 in Section 4.1 again, we see that t = 6u + 5 where u is an integer. Substituting this expression for t back into the equation x = 5t + 1 tells us that x = 5(6u + 5) + 1 = 30u + 26. We insert this into the third equation to obtain

30u + 26 ≡ 3 (mod 7)

Solving this congruence tells us that u ≡ 6 (mod 7) (as the reader should verify). Hence, Theorem 4 in Section 4.1 tells us that u = 7v + 6 where v is an integer. Substituting this expression for u into the equation x = 30u + 26 tells us that x = 30(7v + 6) + 26 = 210u + 206. Translating this back into a congruence, we find the solution to the simultaneous congruences,

x ≡ 206 (mod 210)