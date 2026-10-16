# 3NF Decomposition Algorithm

```
Let F_c be a canonical cover for F;
 i := 0;
 for each functional dependency α → β in F_c do
  if none of the schemas R_j, 1 ≤ j ≤ i contains α β
   then begin
    i := i + 1;
    R_i := α β
   end
 if none of the schemas R_j, 1 ≤ j ≤ i contains a candidate key for R
 then begin
  i := i + 1;
  R_i := any candidate key for R;
 end
 /* Optionally, remove redundant relations */
 repeat
  if any schema R_j is contained in another schema R_k
   then /* delete R_j */
    R_j = R;;
    i=i-1;
 return (R1, R2, ..., R_i)
```