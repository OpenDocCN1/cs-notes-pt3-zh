

## Beng Chin 的哲学

Beng Chin 在处理研究问题和系统设计时秉持的哲学是，所有算法和结构都应简单、优雅且高效，以便能够轻松地嫁接进现有系统，并在实际应用中易于实现、维护和扩展。一个很好的例子就是他对新索引设计的思路；它们主要基于 B+ 树——设计简单优雅，性能高效、稳健且可扩展（例如 iDistance、Bx-tree、ST2B-tree）。
http://www.comp.nus.edu.sg/~ooibc/

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_241_0.png)

query:

```
select ?a, ?t where {
?b hasAuthor ?a . ?b hasTitle ?t .
?b inLanguage French . ?b inCategory Crime . ?b wonPrize ?p .
?b features ?m . ?m inList WorldHeritage . ?m locatedIn Africa }
```

join graph:

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_243_0.png)

operator tree
(excerpt):

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_243_1.png)

Figure 1: Query, Join Graph and Operator Tree

## Sideway Information Passing

- 1. Light-weight run-time method 轻量级运行时方法
  - Run-time optimizing operator tree based light-weight statistics information collection
- 2. Pipelined executions 流水线
- 3. Scale very well with increasing complex trees

## Column-Store Support for RDF Data Management: not all swans are white[4]

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_247_0.png)

Figure 7: Scalability experiment

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_248_0.png)

| S | P | O | C |
|---|---|---|---|
| &N.YT | endorses | S.B. Obama | c₂ |
| &N.YT | rdf:type | Newspaper | c₄ |
| Newspaper | rdf:type | rdfs:Class | c₃ |
| Newspaper | rdfs:subClassOf | Mass Media | c₃ |
| Mass Media | rdfs:subClassOf | Media | c₅ |
| Candidate | rdf:type | rdfs:Class | c₆ |
| S.B. Obama | rdf:type | Candidate | c₆ |
| endorses | rdf:type | rdf:Property | c₁ |
| endorses | rdfs:domain | Newspaper | c₁ |
| endorses | rdfs:range | Candidate | c₁ |
| Candidate | rdfs:subClassOf | Person | c₁ |
| supports | rdf:type | rdf:Property | c₁ |
| supports | rdfs:domain | Mass Media | c₁ |
| supports | rdfs:range | Person | c₁ |
| endorses | rdfs:subPropertyOf | supports | c₂ |
| &N.YT | endorses | S.B. Obama | c₂ |
| Media | rdf:type | rdfs:Class | c₃ |

# Fig. 1. Granularity Levels of Power

# Fig. 2. Relation S(s, p, o, c)

Fig. 3. Graph representation of Q(s, p, o, c)

## Beyond Triples: Quadruple Storage

To my knowledge, no reported research on the storage of quadruples by now!

- 1. Sextuple Indexing may not be efficient
- 2. Complex queries on quadruples
- 3. It is related with uncertain data management, a hot research point.
  - (s, p, o, p’), where p’ means the possibility of (s, p, o).

Fig. 4. Nodes a₁ and a₆ are connected by a path that follows the sequence of navigational axes next/next/edge/next/next⁻¹/node

## G:

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_252_0.png)

β = next::a/(next::[next::b/self::c])*/(edge::[next::d] | next::a)+

## SPARQ2L:Towards support for subgraph extraction queries in RDF Database[9]

```
SELECT ??p
WHERE {  ?x  ??p  ?x .
         ?z  compound:name  "Methionine".
         PathFilter(containsAny(??p, ?z) ) }
```

```
SELECT ??p
WHERE  {  ?x  ??p  ?y .
         ?x  foaf:name  "salesPersonA".
         ?y  company:is_CIO ?z.
         ?z  company:name "CompanyY".
         PathFilter( cost(??p) < 4 ) }
```

## Complex Query

To my knowledge, no reported research on complex query in database literature!

- 1. Long join chain
- 2. Complex star join
- 3. Support inference
  - Materialization method may not be available?
  - Sideway information passing?
  - Others??

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_255_0.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_255_1.png)

