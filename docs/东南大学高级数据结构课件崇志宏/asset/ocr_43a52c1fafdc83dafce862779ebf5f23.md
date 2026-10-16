query:

```
select ?a, ?t where {
?b hasAuthor ?a . ?b hasTitle ?t .
?b inLanguage French . ?b inCategory Crime . ?b wonPrize ?p .
?b features ?m . ?m inList WorldHeritage . ?m locatedIn Africa }
```

join graph:

![](bbox=[0.22, 0.21, 0.92, 0.38])

operator tree
(excerpt):

![](bbox=[0.08, 0.52, 0.95, 0.88])

Figure 1: Query, Join Graph and Operator Tree