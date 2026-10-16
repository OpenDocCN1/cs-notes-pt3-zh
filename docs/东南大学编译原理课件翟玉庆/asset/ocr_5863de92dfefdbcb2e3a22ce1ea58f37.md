# CHAPTER 4 Syntax ANALYSIS
Section 2 TOP-DOWN PARSING

# 10、 Construction of a predictive parser

# 1) FIRST & FOLLOW

# FIRST:

+   - If α is any string of grammar symbols, let FIRST(α) be the set of terminals that begin the string derived from α.
+   - If α ⟹* ε, then ε is also in FIRST(α)
+   - That is :
+     α ∈ V*, First(α) = {a | α → a......, a ∈ V_T }