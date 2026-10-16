# Testing Decomposition for BCNF

+   To check if a relation Rᵢ in a decomposition of R is in BCNF,
+   - Either test Rᵢ for BCNF with respect to the restriction of F to Rᵢ (that is, all FDs in F⁺ that contain only attributes from Rᵢ)
+   - or use the original set of dependencies F that hold on R, but with the following test:
+     - for every set of attributes α ⊆ Rᵢ, check that α⁺ (the attribute closure of α) either includes no attribute of Rᵢ - α, or includes all attributes of Rᵢ.
+     - If the condition is violated by some α → β in F, the dependency α → (α⁺ - α) ∩ Rᵢ can be shown to hold on Rᵢ, and Rᵢ violates BCNF.
+     - We use above dependency to decompose Rᵢ