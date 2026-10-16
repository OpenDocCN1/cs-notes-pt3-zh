# CHAPTER 4 SYNTAX ANALYSIS

# Section 5 LR parsers

# 13、 LR(1) item

Note: 1)The look-ahead has no effect in an item of the form (A→α•β,a), where β is not ε,but an item of the form (A→α•,a) calls for a reduction by A→α only if the next input symbol is a.

2)The set of such a’s will always be a proper subset of FOLLOW(A).