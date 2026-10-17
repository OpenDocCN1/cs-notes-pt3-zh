# # 图的运算

**定理：** 设图 \( G_1 = \langle V_1, E_1, \psi_1 \rangle \) 和 \( G_2 = \langle V_2, E_2, \psi_2 \rangle \) 为可运算的。

(1) 如果 \( V_1 \cap V_2 \neq \Phi \) ，则存在唯一的 \( G_1 \cap G_2 \) 。

(2) 存在唯一的 \( G_1 \cup G_2 \) 和 \( G_1 \oplus G_2 \) 。

**证：** 设 \( G_1 \) 和 \( G_2 \) 同为有向图，若同为无向图也可同样证明。

(1) 定义 \( \psi : E_1 \cap E_2 \rightarrow (V_1 \cap V_2) \times (V_1 \cap V_2) \) 为：对任意的 \( e \in E_1 \cap E_2 \)，\( \psi(e) = \psi_1(e) = \psi_2(e) \)。显然 \( \langle (V_1 \cap V_2), (E_1 \cap E_2), \psi \rangle = G_1 \cap G_2 \)。设图 \( G = \langle V_1 \cap V_2, E_1 \cap E_2, \psi \rangle \) 和 \( G' = \langle V_1 \cap V_2, E_1 \cap E_2, \psi' \rangle \) 均为 \( G_1 \) 和 \( G_2 \) 的交。因为 \( G \subseteq G_1 \)，对任意 \( e \in E_1 \cap E_2 \)，\( \psi(e) = \psi_1(e) \)。因为 \( G' \subseteq G_1 \)，对任意 \( e \in E_1 \cap E_2 \)，\( \psi'(e) = \psi_1(e) \)。这表明 \( \psi = \psi' \)。因此，\( G = G' \) 。