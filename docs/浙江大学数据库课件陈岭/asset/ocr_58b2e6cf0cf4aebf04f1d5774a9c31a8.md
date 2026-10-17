# # Example of Attribute Set Closure

# ## Exam1: R = (A, B, C, G, H, I)

+   - F = {A → B
+     A → C
+     CG → H
+     CG → I
+     B → H}

+   - (AG)+
+     1. result = AG
+     2. result = ABCG    (A → C and A → B)
+     3. result = ABCGH    (CG → H and CG ⊆ ABCG)
+     4. result = ABCGHI (CG → I and CG ⊆ ABCGH)

+   - Is AG a candidate key?

# ### 1. Is AG a super key? α⁺

Does AG → R ? == is (AG)+ ⊇ R   :. AG is a superkey

# ### 2. Is AG a candidate key? - Is any subset of AG a superkey?

+   1. Does A → R?   ⇒   Is (A)+ ⊇ R   :. (A)+ = ABCH
+   2. Does G → R?   ⇒   Is (G)+ ⊄ R   :. (G)+ = G

+   - Is AB a candidate key?   :. AG is a candidate key