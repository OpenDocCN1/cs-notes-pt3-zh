# Translation from English to Logic

# Examples:

+   1. “Some student in this class has visited Mexico.”

**Solution:** Let $M(x)$ denote “$x$ has visited Mexico” and $S(x)$ denote “$x$ is a student in this class,” and $U$ be all people.

```
$\exists x\,(S(x)\land M(x))$
```

+   2. “Every student in this class has visited Canada or Mexico.”

**Solution:** Add $C(x)$ denoting “$x$ has visited Canada.”

```
$\forall x\,(S(x)\to(M(x)\lor C(x)))$
```