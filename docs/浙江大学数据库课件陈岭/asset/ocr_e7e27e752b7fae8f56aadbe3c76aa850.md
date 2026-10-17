# (2) Create Table Construct

An SQL relation is defined using the create table command:

```
CREATE TABLE r(A₁ D₁, A₂ D₂, ..., Aₙ Dₙ,
              (integrity constraint₁),
              ...,
              (integrity constraintₖ))
```

+   - **r** is the name of the relation
+   - each **Aᵢ** is an attribute name in the schema of relation **r**
+   - **Dᵢ** is the data type of values in the domain of attribute **Aᵢ**