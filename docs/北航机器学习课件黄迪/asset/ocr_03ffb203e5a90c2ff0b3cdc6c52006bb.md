# 生成式模型和判别式模型

p(C₁|x) = p(x|C₁)p(c₁) / [p(x|C₁)p(c₁)+p(x|C₂)p(c₂)] = 1 / [1+exp(-a)] = σ(a)

a = ln p(C₁|x)/p(C₂|x) = ln [p(x|C₁)p(C₁) / p(x|C₂)p(C₂)]

+   生成式模型(Generative Model)
+   估计类条件密度并计算a

+   判别式模型(Discriminative Model)
+   把a视为线性函数 a = wᵀx + w₀ 直接估计