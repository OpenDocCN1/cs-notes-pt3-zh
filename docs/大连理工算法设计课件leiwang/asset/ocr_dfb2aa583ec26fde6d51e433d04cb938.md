# Indicator random variables

Given a sample space and an event $A$, we define the **indicator random variable**

$$I\{A\}=\begin{cases}1 & \text{if } A \text{ occurs},\\0 & \text{if } A \text{ does not occur.}\end{cases}$$

# Lemma

For an event $A$, let $X_A=I\{A\}$. Then $E[X_A]=\Pr\{A\}$.

**Proof** Letting $A$ be the complement of $A$, we have

$$E[X_A]=E[I\{A\}]$$

$$=1\cdot\Pr\{A\}+0\cdot\Pr\{A\}\qquad\text{(definition of expected value)}$$

$$=\Pr\{A\}.$$

Some examples...