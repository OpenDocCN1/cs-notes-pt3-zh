# CHAPTER 4  Syntax ANALYSIS

# Section 2 TOP-DOWN PARSING

10.  Construction of a predictive parser

# 3) Computing FOLLOW(A)

+   (1) Place $ in FOLLOW(S), where S is the start symbol and $ is the input right end-marker.

+   (2) If there is A → αBβ in G, then add (First(β)-ε) to Follow(B).

+   (3) If there is A → αB, or A→αBβ where FIRST(β) contains ε, then add Follow(A) to Follow(B).