# Proof in Detail (V)

The following function

v(c,j,z) = { the number j' of the next instruction when the configuration c is operated on by the jth instruction with code z, 0, if j > 0, if j = 0 }

is primitive recursive if

v(c,j,z) = { j + 1, if rm(4,z) ≠ 3, j + 1, if rm(4,z) = 3 ∧ (c)_{v1(z)} ≠ (c)_{v2(z)}, v3(z), if rm(4,z) = 3 ∧ (c)_{v1(z)} = (c)_{v2(z)} }