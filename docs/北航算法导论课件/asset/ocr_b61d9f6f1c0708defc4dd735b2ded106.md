# 34.7.1 Conjunctive Normal Form (CNF, 合取范式)

+   - A logical (Boolean) formula is in Conjunctive Normal Form if it is a conjunction (合取) of clauses.
+     - If c=T, then c∧c₁∧...∧cₖ = c₁∧...∧cₖ
+     - If c=F, then c∧c₁∧...∧cₖ = F

+   - The following formula is in conjunctive normal form:
+     - (p∨q∨s)∧(¬q∨r)∧(¬p∨r)∧(¬r∨s)