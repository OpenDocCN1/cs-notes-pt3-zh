
## Second attempt: using a tuple

n = 5, c = 10

| x | x₁ | x₂ | x₃ | x₄ | x₅ |
|---:|---:|---:|---:|---:|---:|
| p | 6 | 3 | 5 | 4 | 6 |
| w | 2 | 2 | 6 | 5 | 4 |

![](img/4208ee4325ab94ec0c685a689680f88f_96_0.png)

- Calculate f values using array
  - \(f(5,0)=0,\ldots,f(5,4)=6,\ldots,f(5,10)=6\)
  - \(f(4,0)=0,\ldots,f(4,4)=6,\ldots,f(4,9)=10,\ f(4,10)=10\)
  - \(\ldots\)
- Save step points only for each \(i\)
  - Define a tuple \((a,b)\), where \(a=y\) and \(b=f(i,y)\)
  - \((a,b)\) corresponds to an optimal loading with capacity \(a\) and value \(b\)
  - Put all tuples into a set \(P_i\)
  - \(P_n\) can be got easily. \(P_n=\{(0,0),(w_n,p_n)\}\)
  - \(P_1\) contains our goal! Why?

## Tuple method: principle

- Let \(Q=\{(s,t)\mid w_i\le s<c,\ (s-w_i,t-p_i)\in P_{i+1}\}\)
  - \(Q\) corresponds to \(P_i\) in which item \(i\) **has been selected**
  - \(P_{i+1}\) corresponds to \(P_i\) in which item \(i\) **has not been selected**
  - Thus, \(P_i = Q \cup P_{i+1}\)
- Merge \(Q\) and \(P_{i+1}\) to get \(P_i\)
