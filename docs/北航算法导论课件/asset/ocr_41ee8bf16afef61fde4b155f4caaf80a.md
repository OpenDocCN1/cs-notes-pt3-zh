# 5.2 Indicator random variables（指示随机变量）

![](bbox=[0.332, 0.181, 0.963, 0.384])

Given a sample space and an event A, we define the indicator random variable（给定采样空间和事件 A，指示随机变量…）

$$I\{A\}=\begin{cases}1 & \text{if A occur,}\\0 & \text{if A does not occur.}\end{cases}$$

▢  *Lemma*

For an event, let $X_A=I\{A\}$. Then $E[X_A]=Pr\{A\}$.

*Proof* Letting ~A be the complement of A, we have
$$E[X_A]=E[I\{A\}]$$
$$\qquad=1\cdot Pr\{A\}+0\cdot Pr\{~A\}\qquad\text{\{definition of expected value\}}$$
$$\qquad=Pr\{A\}.$$