# CHAPTER 4  SYNTAX ANALYSIS

# Section 5  LR parsers

# 16、Construction of the canonical LR parsing table

+   - Input. An augmented grammar G′
+   - Output. The canonical LR parsing table functions action and goto for G′
+   - Method.

+   (1) Construct C={I₀,I₁,…Iₙ}, the collection of sets of LR(1) items for G′.
+   
+   (2) State i is constructed from Iᵢ. The parsing actions for state i are determined as follows: