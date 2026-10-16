# Testing for Dependency Preservation

+   To check if a dependency α → β is preserved in a decomposition of R into R₁, R₂, ..., Rₙ we apply the following test (with attribute closure done with respect to F)

+   result = α
+   while (changes to result) do
+     for each Rᵢ in the decomposition
+       t = (result ∩ Rᵢ)⁺ ∩ Rᵢ
+       result = result ∪ t

+   If result contains all attributes in β, then the functional dependency α → β is preserved.

+   We apply the test on all dependencies in F to check if a decomposition is dependency preserving

+   This procedure takes polynomial time, instead of the exponential time required to compute F⁺ and (F₁ ∪ F₂ ∪ ... ∪ Fₙ)⁺