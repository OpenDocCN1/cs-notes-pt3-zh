![](bbox=[0.03, 0.12, 0.22, 0.42])

```
procedure QUICKSORT( K, s, t )
if (s<t) then
[
 i←s
 j←t+1
 temp←K[s]
 loop
  repeat
   i←i+1
  until (temp≤K[i] or i=t)
  repeat
   j←j-1
  until (temp≥K[j] or j=s)
  if (i<j) then
   call SWAP( K[i], K[j] )
  else
   exit
 forever
call SWAP( K[s], K[j] )
call QUICKSORT( K, s, j-1 )
call QUICKSORT( K, j+1, t ) ]
end
```

![](bbox=[0.6, 0.22, 0.92, 0.32])