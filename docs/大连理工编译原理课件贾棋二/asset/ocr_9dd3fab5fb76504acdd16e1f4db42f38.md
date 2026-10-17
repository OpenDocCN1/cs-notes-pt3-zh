# # 4.3 L属性定义的自上而下计算

# ## 例 左递归的消除引起继承属性

| 产生式 | 语义规则 |
|---|---|
| \( E \rightarrow E_1 + T \) | \( E.nptr := mknode('+', E_1.nptr, T.nptr) \) |
| \( E \rightarrow T \) | \( E.nptr := T.nptr \) |
| \( T \rightarrow T_1 * F \) | \( T.nptr := mknode('*', T_1.nptr, F.nptr) \) |
| \( T \rightarrow F \) | \( T.nptr := F.nptr \) |
| \( F \rightarrow (E) \) | \( F.nptr := E.nptr \) |
| \( F \rightarrow \text{id} \) | \( F.nptr := mkleaf(\text{id}, \text{id.entry}) \) |
| \( F \rightarrow \text{num} \) | \( F.nptr := mkleaf(\text{num}, \text{num.val}) \) |