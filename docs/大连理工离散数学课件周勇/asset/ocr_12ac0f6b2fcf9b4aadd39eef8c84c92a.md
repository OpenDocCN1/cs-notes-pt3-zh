# # 主合取范式

+   - 主合取范式和真值表的关系：

+   - 右图为 \( A = P \land Q \lor R \) 对应的真值表：

| P | Q | R | 极大项 | \( P \land Q \lor R \) |
|---|---|---|--------|----------------------|
| 0 | 0 | 0 | \( P \lor Q \lor R \) | 0 |
| 0 | 0 | 1 | \( P \lor Q \lor \neg R \) | 1 |
| 0 | 1 | 0 | \( P \lor \neg Q \lor R \) | 0 |
| 0 | 1 | 1 | \( P \lor \neg Q \lor \neg R \) | 1 |
| 1 | 0 | 0 | \( \neg P \lor Q \lor R \) | 0 |
| 1 | 0 | 1 | \( \neg P \lor Q \lor \neg R \) | 1 |
| 1 | 1 | 0 | \( \neg P \lor \neg Q \lor R \) | 1 |
| 1 | 1 | 1 | \( \neg P \lor \neg Q \lor \neg R \) | 1 |

![](bbox=[0.047, 0.534, 0.479, 0.804])