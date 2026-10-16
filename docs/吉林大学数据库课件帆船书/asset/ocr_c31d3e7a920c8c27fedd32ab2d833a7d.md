# Boyce-Codd Normal Form

A relation schema R is in BCNF with respect to a set F of functional dependencies if for all functional dependencies in F+ of the form

```
α → β
```

where α ⊆ R and β ⊆ R, at least one of the following holds:

+   ■ α → β is trivial (i.e., β ⊆ α)

+   ■ α is a superkey for R

Example schema not in BCNF:

```
instr_dept (ID, name, salary, dept_name, building, budget )
```

because dept_name→ building, budget holds on instr_dept, but dept_name is not a superkey