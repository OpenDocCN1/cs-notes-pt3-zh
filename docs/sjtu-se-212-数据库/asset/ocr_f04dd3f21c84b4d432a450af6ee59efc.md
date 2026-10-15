# Nested-Loop Join

•To compute the theta join r ⋈ s
for each tuple t_r in r do begin
  for each tuple t_s in s do begin
    test pair(t_r, t_s) to see if they satisfy the join condition
    if they do, add t_r · t_s to the result.
  end
end
r is called the outer relation and s the inner relation of the join.
Requires no indices and can be used with any kind of join condition.
Expensive since it examines every pair of tuples in the two relations.