# Chapter 7 Runtime Environments

# Section 2 Storage allocation strategies

# 4. Stack allocation

# 4) Stack allocation for nested procedures

(4) displays

+   - Suppose control is in an activation of a procedure pj at nesting depth j, then the display of activation of pj is:

|  |  |
|---|---| 
| j | Sp for pj | 
| j−1 | Sp for pj-1 | 
|  | ...... | 
| 0 | Sp for p0 | 
|  | d[j+1] |