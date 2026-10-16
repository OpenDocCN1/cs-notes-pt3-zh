
## Chapter 5 Syntax-Directed Translation

### Section 1 Syntax-Directed Definitions

#### 1. Definitions

4. **Dependency graph**  
   A graph that represents dependencies between attributes set up by the semantic rules.

   **Notes:**
   1. From the dependency graph, we can derive an evaluation order for the semantic rules.
   2. Evaluation of the semantic rules defines the values of the attributes at the nodes in the parse tree.
   3. Semantic rules may have side effects, e.g., printing a value.

5. **Annotated parse tree**  
   A parse tree showing the values of attributes at each node.

   **Notes:** The process of computing the attribute values at the nodes is called annotating or decorating the parse tree.

#### 2. Form of a Syntax-Directed Definition

Each grammar production A → α has associated with it a set of semantic rules of the form b = f(c1, c2, …, ck), where f is a function.

1. b is a synthesized attribute of A; c1, c2, …, ck are attributes belonging to the grammar symbols of the production.
2. b is an inherited attribute of one of the grammar symbols on the right side of the production; c1, c2, …, ck are attributes belonging to the grammar symbols of the production.

**Notes:** In either case, we say that attribute b depends on attributes c1, c2, …, ck.

#### 3. Attribute Grammar

A syntax-directed definition in which the functions in semantic rules cannot have side effects.

**Notes:**
1. Functions in semantic rules will often be written as expressions.
2. Occasionally, semantic rules are written as procedure calls or program fragments (in this case, we name the attribute of the non-terminal as a dummy attribute).
3. Values for attributes of terminals are usually supplied by the lexical analyzer.

**E.g.**

| Production | Semantic rules |
| --- | --- |
| A → E **n** (**n** for new-line) | Print(E.val) (A has a dummy attribute) |
| E → E^(1) * E^(2) | E.val = E^(1).val * E^(2).val |
| E → E^(1) + E^(2) | E.val = E^(1).val + E^(2).val |
| E → (E^(1)) | E.val = E^(1).val |
| E → digit | E.val = digit.lexval |

#### 4. Synthesized Attributes

2. Annotation for a parse tree for an S-attributed definition: By evaluating the semantic rules for the attributes at each node *bottom up*, *from the leaves to the root*.

**E.g. Annotated parse tree for `3 * 5 + 4 n`**

![](img/353f619caa6c5715591f2105bdfa2865_375_0.png)
![](img/353f619caa6c5715591f2105bdfa2865_376_0.png)
![](img/353f619caa6c5715591f2105bdfa2865_377_0.png)

#### 5. Inherited Attributes

Although it is always possible to rewrite a syntax-directed definition to use only synthesized attributes, it is often natural to use a syntax-directed definition with inherited attributes.

**E.g. Syntax-directed definition with inherited attribute L.in**

| Production | Semantic rules |
| --- | --- |
| D → T L | L.in = T.type |
| T → int | T.type = integer |
| T → real | T.type = real |
| L → L^(1), id | L^(1).in = L.in<br>addtype(id.entry, L.in) |
| L → id | addtype(id.entry, L.in) |

**E.g. Parse tree with inherited attribute `in` at each node labeled L. (`real id1, id2, id3`)**

![](img/353f619caa6c5715591f2105bdfa2865_380_0.png)
![](img/353f619caa6c5715591f2105bdfa2865_381_0.png)

#### 6. Dependency Graphs

1. **Definition**  
   A directed graph that describes the inter-dependencies among the inherited and synthesized attributes at the nodes in a parse tree.

2. **Constructing a dependency graph for a given parse tree**
