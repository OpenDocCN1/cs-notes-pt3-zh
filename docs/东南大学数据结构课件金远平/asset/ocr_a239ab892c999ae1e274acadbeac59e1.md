# 2.3.1 Polynomial Representation

# Representation 1

private:

```
int degree; // degree ≤ MaxDegree
```

```
float coef[MaxDegree+1];
```

Let a be A(x)=aₙxⁿ + aₙ₋₁xⁿ⁻¹+,...,+ a₁x+ a₀

```
a.degree=n;
```

```
a.coef[i] = aₙ₋ᵢ, 0 ≤ i ≤ n
```

Simple algorithms for many operations.