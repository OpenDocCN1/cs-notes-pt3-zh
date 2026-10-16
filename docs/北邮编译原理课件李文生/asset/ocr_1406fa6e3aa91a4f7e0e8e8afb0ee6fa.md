```
L→id { L.place=id.place; L.offset=null }
```

```
Elist→id[E { Elist.place=E.place;
Elist.ndim=1;
Elist.array=id.place }
```

```
e₁=i₁
```

```
Elist→Elist₁,E { t=newtemp;
m=Elist₁.ndim+1;
emit(t ':=' Elist₁.place '×' limit(Elist₁.array,m));
emit(t ':=' t '+' E.place);
Elist.array=Elist₁.array;
Elist.place=t;
Elist.ndim=m }
```

```
e₂=e₁×n₂+i₂
e₃=e₂×n₃+i₃
eₖ=eₖ₋₁×nₖ+iₖ
```

```
L→Elist] { L.place=newtemp;
emit( L.place ':=' Elist.array '-' invariant(Elist.array));
L.offset=newtemp;
emit(L.offset ':=' w '×' Elist.place) }
```