# 3.2.3 Derivations and the language defined by a grammar

• Let G = (V,Σ,S,→) be a CFG. The “directly derives” relation (⇒) is defined as { (αAy, αβy) | A→β }.

# • Example

Let G be the grammar with productions S → aSbS | ε

+   S ⇒ aSbS
+   aSbS ⇒ aaSbSbS
+   aaSbSbS ⇒ aabSbS
+   aabSbS ⇒ aabbS
+   aabbS ⇒ aabbaSbS
+   aabbaSbS ⇒ aabbabS
+   aabbabS ⇒ aabbab

> **nonterminal** is LHS of production  
> **string** is RHS of production

![](bbox=[0.77, 0.67, 1.0, 0.99])

![](bbox=[0.0, 0.91, 0.09, 0.99])