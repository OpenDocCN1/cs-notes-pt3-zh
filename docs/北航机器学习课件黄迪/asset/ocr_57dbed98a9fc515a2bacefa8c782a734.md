# 混合高斯模型

γ(z_k) ≡ p(z_k = 1|x)

= \frac{p(z_k = 1)p(x|z_k = 1)}{\sum_{j=1}^{K} p(z_j = 1)p(x|z_j = 1)}

= \frac{π_k \mathcal{N}(x|μ_k, Σ_k)}{\sum_{j=1}^{K} π_j \mathcal{N}(x|μ_j, Σ_j)}