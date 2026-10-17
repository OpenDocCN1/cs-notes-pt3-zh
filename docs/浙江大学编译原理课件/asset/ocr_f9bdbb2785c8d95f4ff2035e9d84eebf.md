# 4.3.1 First Sets

• Definition:

Let X be a grammar symbol (a terminal or non-terminal) or ε. Then First(X) is a set of terminals or ε, which is defined as follows:

+   1. If X is a terminal or ε, then First(X) = {X};
+   2. If X is a non-terminal, then for each production choice X → X₁ X₂ … Xₙ, First(X) contains First(X₁) − {ε}.

![](bbox=[0.777, 0.665, 1.0, 0.999])

![](bbox=[0.0, 0.905, 0.095, 0.999])