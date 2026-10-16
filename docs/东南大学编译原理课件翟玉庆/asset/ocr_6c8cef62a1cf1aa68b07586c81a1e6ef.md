# CHAPTER 4  SYNTAX ANALYSIS

# Section 5  LR parsers

# 12、SLR(1) Parsing Table Algorithm

Note：Every SLR(1) grammar is unambiguous, but there are many unambiguous grammars that are not SLR(1).

+   E.G.
+   1. S' → S
+   2. S → L = R
+   3. S → R
+   4. L → *R
+   5. L → i
+   6. R → L