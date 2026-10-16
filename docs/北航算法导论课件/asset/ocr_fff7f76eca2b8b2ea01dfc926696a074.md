# Comparison between Divide-and-conquer and Dynamic programming

|  | Divide-and-conquer | Dynamic programming |
|---|---|---|
| **similarity** | solves problems by combining the solutions to subproblems. | solves problems by combining the solutions to subproblems. |
| **difference** | 1) partition the problem into **independent subproblems**, 2) solve the subproblems **recursively**, 3) **combine** their solutions to solve the original problem. | the subproblems are **not independent**, that is, when subproblems **share** subsubproblems.（子问题不独立，不同子问题共享相同的子子问题） |
|  | might do more work than necessary, **repeatedly** solving the common subsubproblems. | solves every subsubproblem **just once** and then **saves its answer in a table**, avoiding recomputing the answer every time the subsubproblem is encountered. |