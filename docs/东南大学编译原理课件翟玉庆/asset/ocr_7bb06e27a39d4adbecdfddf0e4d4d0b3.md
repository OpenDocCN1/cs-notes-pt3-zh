+   - E.g. Syntax-directed definition with inherited attribute L.in

| Production | Semantic rules |
|---|---|
| D → T L | L.in=T.type |
| T → int | T.type= integer |
| T → real | T.type=real |
| L → L⁽¹⁾,id | L⁽¹⁾.in=L.in
addtype(id.entry, L.in) |
| L → id | addtype(id.entry, L.in) |