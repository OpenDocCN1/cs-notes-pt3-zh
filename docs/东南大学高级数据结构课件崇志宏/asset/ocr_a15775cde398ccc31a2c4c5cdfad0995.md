# Amortized cost

The amortized cost for the *i*th operation of MTF with respect to Φ is

ĉᵢ = cᵢ + Φ(Lᵢ) − Φ(Lᵢ₋₁)
≤ 2r + 2(|A| − |B| + tᵢ)
= 2r + 2(|A| − (r − 1 − |A|) + tᵢ)
= 2r + 4|A| − 2r + 2 + 2tᵢ
= 4|A| + 2 + 2tᵢ
≤ 4(r* + tᵢ)
= 4cᵢ*.

![](bbox=[0.2, 0.26, 0.26, 0.36])