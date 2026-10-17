# The solution to Su-Tsu’s puzzle

To solve the system of congruences in Example 5, first let m=3 · 5 · 7=105, M₁=m/3=35, M₂=m/5=21, and M₃=m/7=15. We see that 2 is an inverse of M₁=35 modulo 3, since 35≡2 (mod 3); 1 is an inverse of M₂=21 modulo 5, since 21≡1 (mod 5); and 1 is an inverse of M₃=15 (mod 7), since 15≡1 (mod 7). The solutions to this system are those x such that

x ≡ a₁M₁ y₁ + a₂ M₂ y₂ + a₃ M₃y₃
=2 · 35 · 2+3 · 21 · 1+2 · 15 · 1 (mod 105)=233 ≡ 23 (mod 105).

It follows that 23 is the smallest positive integer that is a simultaneous solution. We conclude that 23 is the smallest positive integer that leaves a remainder of 2 when divided by 3, a remainder of 3 when divided by 5, and a remainder of 2 when divided by 7.