# CHAPTER 4 Syntax ANALYSIS
Section 2 TOP-DOWN PARSING

10、 Construction of a predictive parser

4) Construction of Predictive Parsing Tables

Main Idea: Suppose A →α is a production with a in FIRST(α). Then the parser will expand A by α when the current input symbol is a. If α → ε, we should again expand A by α if the current input symbol is in FOLLOW(A), or if the $ on the input has been reached and $ is in FOLLOW(A).