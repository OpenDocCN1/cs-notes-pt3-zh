# ## 3.5 LR分析器

例 \( E \rightarrow E + T \mid T \)
\( T \rightarrow T * F \mid F \)
\( F \rightarrow (E) \mid \text{id} \)

| 状态 | 动作 | 转移 |
|---|---|---|
| | id + * ( ) $ | E T F |
| 0 | s5 s4 | 1 2 3 |
| 1 | s6 acc | |
| 2 | r2 s7 r2 r2 | |
| 3 | r4 r4 r4 r4 | |
| 4 | s5 s4 | 8 2 3 |