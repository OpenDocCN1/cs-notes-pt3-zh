# CHAPTER 3 LEXICAL ANALYSIS

# Section 7 Regular Grammar to an NFA

2、 Right-linear grammar to FA

+   - Method :
+     - For each production, construct the function move.

a) For the productions similar as A₁ → aA₂, construct move(A₁,a)= A₂.

b) For the productions similar as A₁ → a, construct move(A₁,a)= T.

c) For each a in Σ, move(T,a)=Φ, that means the accepting states do not recognize any terminal symbol.