# Fisher准则

求 $J_F(w)$ 取得最大值的 $w$ $J_F(w) = \frac{(\tilde{m}_1 - \tilde{m}_2)^2}{\tilde{S}_1^2 + \tilde{S}_2^2}$

$\tilde{m}_i = \frac{1}{N_i} \sum_{y \in \eta_i} y = \frac{1}{N_i} \sum_{x \in \chi_i} w^T x = w^T (\frac{1}{N_i} \sum_{x \in \chi_i} x) = w^T m_i$

$(\tilde{m}_1 - \tilde{m}_2)^2 = (w^T m_1 - w^T m_2)^2 = w^T (m_1 - m_2)(m_1 - m_2)^T w = w^T S_b w$

$\tilde{S}_i^2 = \sum_{y \in \eta_i} (y - \tilde{m}_i)^2 = \sum_{x \in \chi_i} (w^T x - w^T m_i)^2 = w^T [\sum_{x \in \chi_i} (x - m_i)(x - m_i)^T] w = w^T S_i w$

$\tilde{S}_1^2 + \tilde{S}_2^2 = w^T (S_1 + S_2) w = w^T S_w w \implies J_F(w) = \frac{w^T S_b w}{w^T S_w w}$

**Lagrange乘子法求解:**

$w^* = S_w^{-1} (m_1 - m_2)$

分类时确定分界阈值 $y_0$，与 $y = w^{*T} x$ 比较进行决策。