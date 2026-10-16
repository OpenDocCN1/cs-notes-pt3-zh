```
SP(S1, S2, ...,Sn)
    if S1=>1 and ... and Sn=>1 then
        for I :=1 to n do
            Si := Si - 1; SV(S1, S2, ...,Sn)
        endfor
    else
        wait in Si;
    endif
    for I :=1 to n do
        Si := Si + 1;
        wake waited proces
    endfor
```