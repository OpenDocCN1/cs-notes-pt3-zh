# 四、语句的类型检查

```
S→id:=E { if (lookup(id.entry)==E.type)
    S.type=void;
    else S.type=type_error; }
```

```
S→if E then S₁ { if (E.type==boolean)
    S.type=S₁.type;
    else S.type=type_error; }
```

```
S→while E do S₁ { if (E.type==boolean)
    S.type=S₁.type;
    else S.type=type_error; }
```

```
S→S₁;S₂ { if (S₁.type==void) && (S₂.type==void)
    S.type=void ;
    else S.type=type_error; }
```

```
P→D;S { if (S.type==void) P.type=void;
    else P.type=type_error }
```