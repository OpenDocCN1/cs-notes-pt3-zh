# # 图的同构

定义：设图 \( G = \langle V, E, \psi \rangle \) 和 \( G' = \langle V', E', \psi' \rangle \)。如果存在双射 \( f: V \to V' \) 和双射 \( g: E \to E' \)，使得对于任意的 \( e \in E \)，\( v_1, v_2 \in V \) 都满足

\(\psi'(\text{g}(\text{e})) = \begin{cases} \{ f(v_1), f(v_2) \} & \text{若 } \psi(e) = \{ v_1, v_2 \} \\ \langle f(v_1), f(v_2) \rangle & \text{若 } \psi(e) = \langle v_1, v_2 \rangle \end{cases}\)

则称 \( G \) 与 \( G' \) 同构，记作 \( G \cong G' \)，并称 \( f \) 和 \( g \) 为 \( G \) 和 \( G' \) 之间的<u>同构映射</u>，简称同构。