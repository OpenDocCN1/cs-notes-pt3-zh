# 4NF Decomposition Algorithm

result := {R};
done := false;
compute D+;
Let Dᵢ denote the restriction of D+ to Rᵢ

while (not done)
  if (there is a schema Rᵢ in result that is not in 4NF) then
    begin
      let α ⟶⟶ β be a nontrivial multivalued dependency that holds on Rᵢ such that α → Rᵢ is not in Dᵢ, and α∩β=φ;
      result := (result - Rᵢ) ∪ (Rᵢ - β) ∪ (α, β);
    end
  else done := true;

Note: each Rᵢ is in 4NF, and decomposition is lossless-join