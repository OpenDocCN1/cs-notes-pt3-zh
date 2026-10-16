# CHAPTER 4 SYNTAX ANALYSIS

# Section 5 LR parsers

# 17、 LALR(lookahead-LR)

+   1) Basic idea

Merge the set of LR(1) states having the same core

Notes: (3) After the set of LR(1) states are merged, an error may be caught lately, but the error will eventually be caught, in fact, it will be caught before any more input symbols are shifted.