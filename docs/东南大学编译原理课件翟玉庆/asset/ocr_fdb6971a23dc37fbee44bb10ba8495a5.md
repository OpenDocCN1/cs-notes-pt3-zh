# CHAPTER 4  SYNTAX ANALYSIS

# Section 5  LR parsers

# 17、LALR(look-ahead-LR)

2)The sets of LR(1) states having the same core

+   - The states which have the same items but the look-ahead symbols are different, then the states are having the same core.

Notes: We may merge these sets with common cores into one set of states.