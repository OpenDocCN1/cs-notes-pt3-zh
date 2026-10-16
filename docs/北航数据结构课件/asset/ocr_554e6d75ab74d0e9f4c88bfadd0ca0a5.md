```
for i←1 to n do
  p←link[i]
  while (p≠nil) do
    if (adjvex(p)=k) then
      [ if (link[i]=p) then
          link[i]←next(p)
        else
          next(q)←next(p)
        r←p
        p←next(p)
        call RET(r) ]
    else
      [ if (adjvex(p)>k) then
          adjvex(p)←adjvex(p)−1
        q←p
        p←next(p) ]
  end
end
```