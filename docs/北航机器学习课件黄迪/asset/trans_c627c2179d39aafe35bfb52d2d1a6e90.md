

## 循环神经网络 (Recurrent neural Network, RNN)

● RNN训练-Back Prop Through Time(BPTT)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_805_0.png)

### RNN训练-Back Prop Through Time(BPTT)

+ 计算W的偏导，需要对每个t求偏导

∂E/∂W = Σ_{t=1}^{T} ∂E_t/∂W

+ 链式法则

∂E_t/∂W = Σ_{k=1}^{t} ∂E_t/∂y_t ∂y_t/∂h_t ∂h_t/∂h_k ∂h_k/∂W

+ ■ 已知 $h_t = W\left(f(h_{t-1}) + W^{(hx)} x_{[t]}\right)$

+ ■ 可得

$\frac{\partial h_t}{\partial h_k} = \prod_{j=k+1}^{t} \frac{\partial h_j}{\partial h_{j-1}}$

$\frac{\partial h_t}{\partial h_k} = \prod_{j=k+1}^{t} \frac{\partial h_j}{\partial h_{j-1}} = \prod_{j=k+1}^{t} W^T \operatorname{diag}[f'(h_{j-1})]$

+ RNN中gradient vanishing/exploding

+ 已知 ∂h_t/∂h_k = ∏_{j=k+1}^{t} ∂h_j/∂h_{j-1} = ∏_{j=k+1}^{t} W^T diag[f'(h_{j-1})]

+ 根据 ||xy|| ≤ ||x|| · ||y||

||∂h_j/∂h_{j-1}|| ≤ ||W^T|| ||diag[f'(h_{(j-1)})]|| ≤ β_W β_h 代表上限

||∂h_t/∂h_k|| = ||∏_{j=k+1}^{t} ∂h_j/∂h_{j-1}|| ≤ (β_W β_h)^{t-k}

当与间隔较远时，梯度会很快的变的很大或很小

## Long Short Term Memory (LSTM)

+ • LSTM由重复的单元连接而成

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_809_0.png)

+ • 当成最成功，应用最广泛的神经网络结构之一

### LSTM单元（cell）组成

神经单元

按位操作

前向传播

合并串联

复制

LSTM通过门控单元控制信息的流通

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_810_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_810_1.png)

+ - “遗忘门”

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_811_0.png)

$f_t = \sigma\left(W_f \cdot [h_{t-1}, x_t] + b_f\right)$

# ➢ 选择哪些信息应该被遗忘

先前输出（即隐藏状态）的信息和来自当前输入的信息经sigmoid函数激活，输出介于0~1之间。越接近0意味着越容易被忘记，越接近1则越容易被保留。

“输入门”

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_812_0.png)

i_t = σ(W_i·[h_{t-1}, x_t] + b_i)

Ĉ_t = tanh(W_C·[h_{t-1}, x_t] + b_C)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_812_1.png)

# Cell新状态

+ 1. 先前输出和当前输入经sigmoid函数，计算出哪些值更重要；
+ 2. 同时，把先前输出和当前输入给tanh函数，生成候选状态；
+ 3. 最后，把tanh的输出与sigmoid的输出相乘，生成更新状态

### ● 状态更新

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_813_0.png)

$C_t = f_t \otimes C_{t-1} + i_t \otimes \widetilde{C}_t$

# ➤ 更新cell状态

+ 1. 先前cell状态和遗忘门输出的向量点乘，由于越不重要的值越接近0，原隐藏状态中不重要的信息被丢弃。
+ 2. 新的输出，与当前cell的候选状态相加，输出更新后的cell状态。

## 生成对抗网络

## Generative Adversarial Networks(GAN)

判别式模型 vs 生成式模型

Discriminant Model

p(y|x)

Generative Model

p(x,y)

### ● 判别式模型 vs 生成式模型

|  | Discriminative model | Generative model |
|---|---|---|
| **Goal** | Directly estimate $P(y|x)$ | Estimate $P(x|y)$ to then deduce $P(y|x)$ |
| **What's learned** | Decision boundary | Probability distributions of the data |
| **Illustration** | [判别式模型示意图：两类数据点及决策边界] | [生成式模型示意图：两类数据分布区域] |
| **Examples** | Regressions, SVMs | GDA, Naive Bayes |

+ 生成模型包含两个步骤：
+ > 密度估计
+ > 采样

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_818_0.png)

另一种生成数据的思路：

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_819_0.png)

+ - **生成网络**从潜在空间（latent space）中随机采样作为输入，其输出结果需要尽量模仿训练集中的真实样本。

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_820_0.png)

# 如何学习生成网络？

生成网络从潜在空间（latent space）中随机采样作为输入，其输出结果需要尽量模仿训练集中的真实样本。

Each dimension of input vector represents some characteristics.

Longer hair

blue hair

Open mouth

隐空间可以看作是真实数据某些属性/特征的一种编码

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_821_0.png)

判别网络的输入则为真实样本或生成网络的输出，其目的是将生成网络的输出从真实样本中尽可能分辨出来。

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_822_0.png)

+ • 对抗训练
+ ➢ 生成网络要尽可能地欺骗判别网络。
+ ➢ 判别网络将生成网络生成的样本与真实样本中尽可能区分出来。

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_823_0.png)

+ • 两个网络相互对抗、不断调整参数，最终目的是使判别网络无法判断生成网络的输出结果是否真实。

