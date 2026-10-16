# Definition of “some” Clause

F <comp> some r ⇔ ∃ t ∈ r such that (F <comp> t)
Where <comp> can be: <, ≤, >, =, ≠

(5 < some
0
5
6
) = true
(read: 5 < some tuple in the relation)

(5 < some
0
5
) = false

(5 = some
0
5
) = true

(5 ≠ some
0
5
) = true (since 0 ≠ 5)

(= some) ≡ in
However, (≠ some) ≠ not in