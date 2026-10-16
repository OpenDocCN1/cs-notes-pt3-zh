# 条件随机场
(Conditional Random Fields)

+   特征函数为布尔函数，当满足特征条件时为1，否则为0。其中：
+   
+   $f_j(y_{i-1}, y_i, x, i) = \begin{cases} 1 & T(\text{condition}) \\ 0 & \text{otherwise} \end{cases}$

+   CRF的概率计算： 前向-后向算法

+   CRF的参数学习： 改进的迭代尺度法（IIS），梯度下降法，拟牛顿法

+   CRF的预测算法： 维特比算法