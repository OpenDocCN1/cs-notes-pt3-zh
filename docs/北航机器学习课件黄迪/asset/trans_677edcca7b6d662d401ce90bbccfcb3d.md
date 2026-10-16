

## 机器学习
Machine Learning

北京航空航天大学计算机学院

School of Computer Science and Engineering, Beihang University

黄迪 刘庆杰

2019年秋季学期

Fall 2019

## 课前回顾

## 训练和测试

数据获取
实际运用

通用数据集 (非观测)
训练集 (观测)
测试集 (非观测)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_71_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_71_1.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_71_2.png)

- Training is the process of making the system able to learn.
- No free lunch rule:
  - Training set and testing set come from the same distribution
  - Need to make some assumptions or bias

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_72_0.png)

## 评价标准

- There are several factors affecting the performance:
  - **Types of training** provided
  - The form and extent of any initial **background knowledge**
  - The **type of feedback** provided
  - The **learning algorithms** used
- Two important factors:
  - Modeling
  - Optimization

## 机器学习目标

- Supervised: Low E-out or maximize probabilistic terms

error = 1/N Σ_{n=1}^N [y_n ≠ g(x_n)]

E-in: for training set
E-out: for testing set

Eout(g) ≤ Ein(g) ± O( √(d_VC / N) ln N )

- Unsupervised: Minimum quantization error, Minimum distance, MAP, MLE (Maximum Likelihood Estimation)

Under-fitting VS. Over-fitting (fixed N)

error
d_VC
Eout
Model complexity
Ein

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_75_0.png)

### Components of generalization error

- **Bias:** how much the average model over all training sets differ from the true model?
  - Error due to inaccurate assumptions/simplifications made by the model
- **Variance:** how many models estimated from different training sets differ from each other

- **Under-fitting:** model is too “simple” to represent all the relevant class characteristics
  - High bias and low variance
  - High training error and high test error

- **Over-fitting:** model is too “complex” and fits irrelevant characteristics (noise) in the data
  - Low bias and high variance
  - Low training error and high test error

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_78_0.png)

Models with too few parameters are inaccurate because of a large bias (not enough flexibility).

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_78_1.png)

Models with too many parameters are inaccurate because of a large variance (too much sensitivity to the sample).

E(MSE) = noise² + bias² + variance

Unavoidable Error
Error due to Incorrect Assumptions
Error due to Variance of Training Samples

See the following for explanations of bias-variance (also Bishop’s “Neural Networks” book):

- http://www.stat.cmu.edu/~larry/=stat707/notes3.pdf
- http://www.inf.ed.ac.uk/teaching/courses/mlsc/Notes/Lecture4/BiasVariance.pdf

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_80_0.png)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_81_0.png)

## 回归问题举例

### 曲线拟合

sin(2πx)

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_83_0.png)

y(x, w) = w₀ + w₁x + w₂x² + … + wₘxᴹ = Σ_{j=0}^M w_j x^j

### 平方误差函数

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_84_0.png)

E(w) = 1/2 Σ_{n=1}^{N} { y(x_n, w) - t_n }^2

### M=0

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_85_0.png)

### M=1

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_86_0.png)

### 🔴 M=3

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_87_0.png)

### M=9

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_88_0.png)

### M=9, 增加训练样本数目: N=15

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_89_0.png)

### M=9，增加训练样本数目：N=100

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_90_0.png)

### 多项式系数

![](img/292e77b9b7b40db2ea6f49ac62f8aa0f_91_0.png)

|  | M = 0 | M = 1 | M = 3 | M = 9 |
|---|---|---|---|---|
| $w_0^*$ | 0.19 | 0.82 | 0.31 | 0.35 |
| $w_1^*$ |  | -1.27 | 7.99 | 232.37 |
| $w_2^*$ |  |  | -25.43 | -5321.83 |
| $w_3^*$ |  |  | 17.37 | 48568.31 |
| $w_4^*$ |  |  |  | -231639.30 |
| $w_5^*$ |  |  |  | 640042.26 |
| $w_6^*$ |  |  |  | -1061800.52 |
| $w_7^*$ |  |  |  | 1042400.18 |
| $w_8^*$ |  |  |  | -557682.99 |
| $w_9^*$ |  |  |  | 125201.43 |

