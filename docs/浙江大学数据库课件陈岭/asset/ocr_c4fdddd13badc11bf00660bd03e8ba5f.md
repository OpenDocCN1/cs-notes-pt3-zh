# # Uses of Attribute Closure

There are 3 kind uses of the attribute closure algorithm:

+   1) **Testing for superkey** --- (α → R ?)
+   
+      To test if α is a superkey, we compute α⁺, and check if α⁺ contains all attributes of R, i.e. check if R ⊆ α⁺

+   2) **Testing functional dependencies** --- (α → β ?)
+   
+      To check if a functional dependency α → β holds (or, in other words, is in F⁺), just check if β ⊆ α⁺.
+   
+      It’s a simple and cheap test, and very useful

+   3) **Computing closure of F** --- (F⁺ = ?)
+   
+      For each γ ⊆ R, we find the closure γ⁺, and for each S ⊆ γ⁺, we output a functional dependency γ → S. All γ → S form F⁺