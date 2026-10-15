# Normal Form Theorem

Normal Form Theorem. $M(\bar{x})$ is partially decidable iff there is a primitive recursive predicate $R(\bar{x},y)$ such that $M(\bar{x})$ iff $\exists y.R(\bar{x},y)$.

Proof. If $R(\bar{x},y)$ is primitive recursive and $M(\bar{x}) \Leftrightarrow \exists y.R(\bar{x},y)$, then the computable function “if $\mu y R(\bar{x},y)$ then 1 else $\uparrow$” is the partial characteristic function of $M(\bar{x})$.

Conversely suppose $M(\bar{x})$ is partially decided by $P$. Let $R(\bar{x},y)$ be $P(\bar{x}) \downarrow$ in $y$ steps.

Then $R(\bar{x},y)$ is primitive recursive and $M(\bar{x}) \Leftrightarrow \exists y.R(\bar{x},y)$.