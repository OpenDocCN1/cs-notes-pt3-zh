```
//initialize the error term to compensate for a nonzero
intercept
NError =2*Δy-Δx
//begin the main loop
for i=1 to Δx
WritePixel(x, y , value)
if (NError>=0) then
if (Flag) then //Δy>Δx
x=x+sx
else
Y=Y+1
y=y+sy
end if // End of Flag
NError = NError -2*Δx
end if // End of NError
```