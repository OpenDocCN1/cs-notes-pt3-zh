# 反向传播(BP)算法

![](bbox=[0.07, 0.32, 0.42, 0.7])

Layer i

Layer j

Layer k

a_j = Σ_i w_ji z_i   z_j = h(a_j)

∂E_n / ∂w_ji = ∂E_n / ∂a_j · ∂a_j / ∂w_ji

δ_j ≡ ∂E_n / ∂a_j

∂a_j / ∂w_ji = z_i

∂E_n / ∂w_ji = δ_j z_i