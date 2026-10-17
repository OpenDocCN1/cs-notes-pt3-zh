# Rosen, section 8.4, example 7

Find the zero-one matrix of the transitive closure of the relation R given by:

M_R = [[1 0 1],[0 1 0],[1 1 0]]

![](bbox=[0.28, 0.3, 0.6, 0.58])

M_R^[2] =

![](bbox=[0.7, 0.28, 0.98, 0.6])

M_R* = M_R ∨ M_R^[2] ∨ M_R^[3]

M_R^[2] = M_R ⊙ M_R = [[1 0 1],[0 1 0],[1 1 0]] ⊙ [[1 0 1],[0 1 0],[1 1 0]] = [[1 1 1],[0 1 0],[1 1 1]]