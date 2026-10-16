# 基本块划分的例子

B₁

```
(ASSIG,1,-,y)
```

B₂

```
(LABEL,-,-,L)
(AND,A,B,t₀)
(THEN,t₀,-,-)
```

B₃

```
(ASSIG,0,-,x)
(ELSE,-,-,-)
```

B₄

```
(ASSIG,0,-,y)
```

B₅

```
(ENDIF,-,-,-)
(ADDI,x,1,t₁)
(ASSIG,t₁,-,x)
```

B₆

```
(SUBI,y,1,t₂)
(ASSIG,t₂,-,y)
(WHILE,-,-,-)
(ADDI,x,y,t₃)
(GT,t₃,0,t₄)
(DO,t₄,-,-)
```

B₇

```
(SUBI,x,1,t₅)
(ASSIG,t₅,-,x)
(ENDWHILE,-,-,-)
```

B₈

```
(ASSIG,0,-,z)
```