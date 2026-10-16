# 求 FOLLOW

```
E  ::= −TE′
E′ ::= +TE′ | ε
T  ::= FT′
T′ ::= *FT′ | ε
F  ::= (E) | i
```

```
FIRST(F) = {(, i}
FIRST(T′) = {*, ε}
FIRST(T) = {(, i}
FIRST(E′) = {+, ε}
FIRST(E) = {(, i}
```

```
FOLLOW(E) = {#, )}  ∵ 因为E是识别符号 ∴ # ∈ FOLLOW(E)
                     又 F ::= (E) ∴ ) ∈ FOLLOW(E)

FOLLOW(E′) = {#, )}  ∵ E ::= TE′ ∴ FOLLOW(E) 加入 FOLLOW(E′)

FOLLOW(T) = {+, ), #}  ∵ E′ ::= +TE′，∴ FIRST(E′) − {ε} 加入 FOLLOW(T)
                     又 E′ ⇒ ε，∴ FOLLOW(E′) 加入 FOLLOW(T)

FOLLOW(T′) = FOLLOW(T) = {+, ), #}
                     ∵ T ::= FT′ ∴ FOLLOW(T) 加入 FOLLOW(T′)

FOLLOW(F) = {*, +, ), #}  ∵ T ::= FT′ ∴ FOLLOW(F) = FIRST(T′) − {ε}
                     又 T′ ⇒ ε，∴ FOLLOW(T) 加入 FOLLOW(F)
```