```
a:=1;
while a<=10 do
    begin if a<>b then A[a]:=A[b]+2
        else a:=a+1;
        b:=b+1;
    end
```

(ASSIG, 1,—,a)
( WHILE , — , — , — )
(<= ,  a, 10, t₀)
( DO , t₀ , — , — )
(<> ,  a,b,t₁)
( THEN , t₁ , — , — )
( SUBI ,a , 1 , t₂ )
( MULTI , t₂ , 1 , t₃ )
( AADD , A , t₃ , t₄ )
( SUBI ,b , 1 , t₅ )
( MULTI , t₅ , 1 , t₆ )
( AADD , A , t₆ , t₇ )
( ADDI , t₇ , 2 , t₈ )

(ASSIG, t₈,—,t₄)
( ELSE , — , — , — )
( ADDI, a , 1, t₉ )
( ASSIG, t₉,—,a )
( ENDIF , — , — , — )
( ADDI, b , 1, t₁₀ )
( ASSIG, t₁₀,—,b )
( ENDWHILE ,—, — , — )