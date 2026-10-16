

## 模式识别

## 数字识别

1 1 / 1 1 7 1 1 1
2 2 2 2 2 2 2 2 2
3 3 3 3 3 3 3 3 3
4 4 4 4 4 4 4 4 4
5 5 5 5 5 5 5 5 5
6 6 6 6 6 6 6 6 6
7 7 7 7 7 7 7 7
8 8 8 8 8 8 8 8
9 9 9 9 9 9 9 9
0 0 0 0 0 0 0 0

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_21_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_21_1.png)

模式识别尤其关注面向应用的鲁棒特征提取

## 数据挖掘

- 消费习惯分析

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_22_0.png)

数据挖掘旨在从特定业务数据中找出潜在的知识

## 计算机视觉

## 生物特征识别和目标检测

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_23_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_23_1.png)

计算机视觉通过机器学习技术提升图像视频处理方法

## 计算机视觉

🔴 生物特征识别和目标检测

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_24_0.png)

## 计算机视觉

生物特征识别和目标检测

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_25_0.png)

"panda"
57.7% confidence

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_25_1.png)

+ ε

=

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_25_2.png)

"gibbon"
99.3% confidence

计算机视觉通过机器学习技术提升图像视频处理方法

## 自然语言处理

## 自动翻译与人机对话

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_26_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_26_1.png)

自然语言处理运用机器学习技术改进主要步骤的性能

## 交通出行

- 自动驾驶与出行推荐

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_28_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_28_1.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_28_2.png)

## 社交媒体

## 网络行为预测与推荐

社交网络世界地图
2014年12月

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_29_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_29_1.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_29_2.png)

## 基本概念

i.i.d.

样本集合

标签

训练集

测试集

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_33_0.png)

## 机器学习算法

## 机器学习主要问题

| | 监督学习 | 非监督学习 |
|---|---|---|
| 离散 | 分类或归类 | 聚类 |
| 连续 | 回归 | 降维 |

## 机器学习算法

- 监督学习 Supervised Learning {x_n ∈ R^d, y_n ∈ R}^N_{n=1}
  - 预测
  - 分类 (离散标签), 回归 (实值)
- 非监督学习 Unsupervised Learning ({x_n ∈ R^d}^N_{n=1})
  - 聚类
  - 概率分布估计
  - 寻找关联 (在特征中)
  - 降维
- 半监督学习 Semi-supervised Learning
- 强化学习 Reinforcement Learning
  - 决策制定 (机器人, 象棋机)

## 机器学习算法示意图

监督学习

非监督学习

半监督学习

## 监督学习算法流程

监督学习

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_37_0.png)

## 非监督算法流程

非监督学习

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_38_0.png)

## 分类问题举例

## 训练过程

训练图像

图像特征

训练标签

分类器训练

训练好的分类器

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_39_0.png)

## 分类问题举例

测试过程

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_40_0.png)

## 回归问题举例

- 曲线拟合

sin(2πx)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_41_0.png)

y(x, w) = w₀ + w₁x + w₂x² + … + wₘxᴹ = Σ_{j=0}^M w_j x^j

## 回归问题举例

平方误差函数

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_42_0.png)

E(w) = 1/2 Σ_{n=1}^{N} { y(x_n, w) - t_n }^2

## 回归问题举例

- ● $M=0$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_43_0.png)

## 回归问题举例

M=1

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_44_0.png)

## 回归问题举例

🔴 $M=3$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_45_0.png)

## 回归问题举例

M=9

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_46_0.png)

## 回归问题举例

过拟合问题

均方根误差 Root-Mean-Square (RMS) Error:

$E_{RMS} = \sqrt{2E(\mathbf{w}^*)/N}$

$E(\mathbf{w}) = \frac{1}{2} \sum_{n=1}^{N} \{y(x_n, \mathbf{w}) - t_n\}^2$

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_47_0.png)

## 训练和测试

数据获取

实际运用

通用数据集
(非观测)

训练集
(观测)

测试集
(非观测)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_48_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_48_1.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_48_2.png)

## 训练和测试

- 训练是使系统能够学习的过程。
- 无免费午餐规则:
  - 训练集和测试集来自同一分布
  - 需要做出一些假设或偏见

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_49_0.png)

