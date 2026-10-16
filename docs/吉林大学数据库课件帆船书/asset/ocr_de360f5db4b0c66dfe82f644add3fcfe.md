# # Immediate Database Modification Example

| Log | Write | Output |
|---|---|---|
| `<T_0 start>`<br>`<T_0, A, 1000, 950>`<br>`<T_0, B, 2000, 2050>`<br><br>`<T_0 commit>`<br>`<T_1 start>`<br>`<T_1, C, 700, 600>`<br><br>`<T_1 commit>` | `A = 950`<br>`B = 2050`<br><br>`C = 600` | `B_B, B_C`<br><br>`B_A` |

> > 🟥 Note: *B*<sub>X</sub> denotes block containing X.

![](bbox=[0.603, 0.438, 0.932, 0.64])