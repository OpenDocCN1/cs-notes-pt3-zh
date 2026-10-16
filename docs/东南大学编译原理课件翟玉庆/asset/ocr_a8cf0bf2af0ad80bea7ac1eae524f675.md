# Chapter 2 Language & Syntax Description

# Section 3 Grammar construction and simplification

# 1、 Constructing a grammar from a language

Example 4: Let L₄={ω | ω ∈(0,1)* and the number of 1 appeared in ω is even}

Try to construct the grammar G₄ from L₄

```
S → ε
```

```
S →0S,  S → 1A
```

```
A →0A , A →1S
```