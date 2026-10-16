
## 卷积神经网络（CNN）

### LeNet-5: 1989

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_702_0.png)

C5为卷积层

- 120个神经元，可以看作120个特征图，大小为1×1
- 每个神经元与S4层全部16个特征图的5×5邻域相连
- 连接数=参数数： (5×5×16+1)×120=48,120

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_703_0.png)

- 在MNIST 60,000训练集上的错误率为0.95%
- 60,000+540,000 数据增强，错误率0.8%

### AlexNet: 2012

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_704_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_705_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_705_1.png)

AlexNet 学到的第一层卷积核

### Other Nets

- ZF Net: 2013
- GoogLeNet: 2014
- VGGNet: 2014
- ResNet: 2015

### CNN可视化

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_707_0.png)

Layer 1

Layer 2

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_708_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_708_1.png)

Layer 4

Layer 5

## 自编码机（AutoEncoder）

- AutoEncoder是一种无监督的学习算法，它利用反向传播算法，让目标值等于输入值：

  $x \approx h_{w,b}(x)$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_709_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_710_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_711_0.png)

输入的特征表示

Input Features

## 其它深度学习模型

- DBN（Deep Belief Networks，深度信念网络）
- RNN（Recursive neural networks，递归神经网络）
- LSTM（Long short term memory，长短时记忆网络）
- DBM（Deep Boltzmann machines，深度玻尔兹曼机）
- Stacked (de-noising) auto-encoders，栈式自编码机
- Deep Q-networks，深度Q网络
- ...

## 机器学习

### Machine Learning

北京航空航天大学计算机学院智能识别与图像处理实验室

IRIP Lab, School of Computer Science and Engineering, Beihang University

黄迪 刘庆杰

2019年秋季学期

Fall 2019

### 批梯度下降

使用所有样本的梯度之和进行参数更新，叫**批梯度下降**（Batch gradient descent，BGD）

$$\mathbf{w}^{(\tau+1)}=\mathbf{w}^{\tau}-\eta\frac{1}{N}\sum_{i=1}^{N}\Delta E(\mathbf{x}_i;\mathbf{w}^{\tau})$$

- 计算量大
- 易陷入局部极小值

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_715_0.png)

### SGD的缺点

- 学习率难以选择

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_717_0.png)

- 批量大小对学习效果有影响

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_718_0.png)

(a) 按Iteration的损失变化

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_718_1.png)

(b) 按Epoch的损失变化

- 高维空间存在大量鞍点，优化困难

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_719_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_719_1.png)

### 可变学习率

- 固定学习率不是一个好的选择
- 学习的不同阶段梯度不同
- 自适应学习率
  - 线性衰减

    $\eta^k = \alpha \eta^{k-1}\quad \alpha = 0.5, 0.2,$
  - 指数衰减

    $\eta^k = \eta^0 e^{-k t}$
  - ...

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_720_0.png)

### Adagrad

- 对稀疏参数进行大幅更新和对频繁参数进行小幅更新
- 适合处理稀疏数据

$$\eta^\tau = \frac{\eta^0}{\sqrt{\sum_{t=1}^{\tau}\Delta E^2(\mathbf{w}^t)+\epsilon}}$$

$$\mathbf{w}^{(\tau+1)} = \mathbf{w}^{\tau} - \eta^{\tau}\Delta E(\mathbf{w}^{(\tau)})$$

### RMSprop

- Adagrad引起学习率衰减

  $$\eta^\tau = \frac{1}{\sqrt{\sum_{t=1}^{\tau}\Delta E^2(\mathbf{w}^t)}+\epsilon}\eta^1$$

学习率衰减

- 减弱梯度累积

  $$\mathbf{w}^{(\tau+1)}=\mathbf{w}^{\tau}-\frac{\eta^0}{\sqrt{g^{(\tau)}}+\epsilon}\Delta E(\mathbf{w}^{(\tau)})$$

### 动量SGD

- SGD在遇到局部极值和鞍点时容易震荡
- 引入动量 momentum，抑制梯度的震荡

$$\mathbf{w}^{(\tau+1)}=\mathbf{w}^{\tau}-\eta\frac{1}{m}\sum_{i=1}^{m}\Delta E(\mathbf{x}_i;\mathbf{w}^{(\tau)})$$

$$\nabla_{\mathbf{w}}E^{(\tau)}$$

$g^{(\tau)}$ 表示 $\tau$ 时刻的优化方向，且 $g^{(0)}=\nabla_{\mathbf{w}}E^{(0)}$

$\tau$ 时刻的优化方向：$g^{(\tau)}=\alpha g^{(\tau-1)}+\eta\nabla_{\mathbf{w}}E^{(\tau)}$

$$\mathbf{w}^{(\tau+1)}=\mathbf{w}^{\tau}-g^{\tau}$$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_725_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_725_1.png)

### Nesterov梯度（NAG）

- 具有一定的预测性

$$\mathbf{w}^{\tau'} = \mathbf{w}^{\tau} + \beta\nabla_{\mathbf{w}}E^{(\tau-1)}$$

$$g^{(\tau)} = \alpha g^{(\tau-1)} + \eta\nabla_{\mathbf{w}}E^{(\tau')}$$

$$\mathbf{w}^{(\tau+1)} = \mathbf{w}^{\tau} - g^{\tau}$$

