# 16.1 An activity-selection problem

• **n activities require exclusive use of a common resource.**

+   ◆ Set of activities $S = \{a_1, a_2, \ldots, a_n\}$
+   
+   ◆ $a_i$ needs resource during period $[s_i, f_i)$

• **Example:** $S$ sorted by finish time:

| $i$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| $s_i$ | 1 | 2 | 4 | 1 | 5 | 8 | 9 | 11 | 13 |
| $f_i$ | 3 | 5 | 7 | 8 | 9 | 10 | 11 | 14 | 16 |

![](bbox=[0.103, 0.503, 0.635, 0.934])

Maximum-size mutually compatible set:
$\{a_1, a_3, a_6, a_8\}$.

Not unique: also
$\{a_2, a_5, a_7, a_9\}$.