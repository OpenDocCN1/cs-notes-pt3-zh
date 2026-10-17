# # Decomposition(分解)

Main refinement technique: decomposition
E.g. replacing (ABCD) with, (AB) and (BCD), or (ACD) and
(ABD), or (ABC) and (CD), or (AB), (BC) and (CD) or (AD), (BCD)

E.g.: Decompose the Lending-schema into:
Branch-schema = (branch-name, branch-city, assets)
Loan-info-schema = (branch-name, customer-name,
loan-number, amount)

All attributes of an original schema (R) must appear in the
decomposition (R1, R2): R = R1 ∪ R2

Lossless-join decomposition (无损连接分解).
For all possible relations r on schema R

r = ΠR1 (r) ⋈ ΠR2 (r)

Requirement
for decomp.