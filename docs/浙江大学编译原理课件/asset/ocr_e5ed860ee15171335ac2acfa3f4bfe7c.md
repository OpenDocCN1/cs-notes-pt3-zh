# # 6.2.2 Synthesized and inherited attributes

# ## Synthesized attributes

+   - An attribute is synthesized
+     - if all its dependencies point from child to parent in the parse tree.
+     - given a grammar rule A→X₁X₂... Xₙ, the only associated attribute equation with an a on the left-hand side is of the form:
+       - A.a = f(X₁.a₁,...,X₁.aₖ,...,Xₙ.a₁,... Xₙ.aₖ)

+   - S-attributed grammar:
+     An attribute grammar in which all the attributes are synthesized

![](bbox=[0.781, 0.662, 0.998, 0.998])

![](bbox=[0.0, 0.906, 0.107, 0.998])