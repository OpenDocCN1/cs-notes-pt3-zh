# CHAPTER 4  Syntax ANALYSIS

# Section 2 TOP-DOWN PARSING

E.g. Consider the following grammar, and parse the string `id+id*id$`

+   1. E → TE'
+   2. E' → +TE'
+   3. E' → ε
+   4. T → FT'
+   5. T' → *FT'
+   6. T' → ε
+   7. F → i
+   8. F → (E)