# BCNF Decomposition Algorithm

```
result := {R};
done := false;
compute F⁺;
while (not done) do
    if (there is a schema Rᵢ in result that is not in BCNF)
        then begin
            let α → β be a nontrivial functional dependency that
                holds on Rᵢ such that α → Rᵢ is not in F⁺,
                and α ∩ β = ∅;
            result := (result − Rᵢ) ∪ (Rᵢ − β) ∪ (α, β);
        end
    else done := true;
```

Note: each Rᵢ is in BCNF, and decomposition is lossless-join.