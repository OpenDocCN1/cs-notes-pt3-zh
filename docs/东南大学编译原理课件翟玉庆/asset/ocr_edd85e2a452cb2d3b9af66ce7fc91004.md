# CHAPTER 4 SYNTAX ANALYSIS

# Section 5 LR parsers

# 12、 SLR(1) Parsing Table Algorithm

Notes: In the above grammar, the shift/reduce conflict arises from the fact that the SLR parser construction method is not powerful enough to remember enough left context to decide what action the parser should take on input = having seen a string reducible to L. That is “R=” can be a part of any right sentential form. So when “L” appears on the top of stack and “=” is the current character of the input buffer, we can not reduce “L” into “R”.