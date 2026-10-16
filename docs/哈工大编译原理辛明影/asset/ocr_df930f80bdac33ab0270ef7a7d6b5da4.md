# # 7.2.3嵌套过程中声明语句的翻译

```
```
P → prog id (input,output) M D; S {addwidth (top(tblptr), top(offset)); pop(tblptr); pop(offset) }
```
```

```
```
M → ε {t := mktable(nil); push(t,tblptr); push(0,offset) }
```
```

```
```
D → D₁ ; D₂
```
```

```
```
D → proc id ;N D₁; S {t := top(tblptr); addwidth(t,top(offset));pop(tblptr);pop(offset); enterproc(top(tblptr),id.name,t) }
```
```

```
```
D→id:T {enter(top(tblptr),id.name,T.type,top(offset)); top(offset): =top (offset) + T.width}
```
```

```
```
N → ε {t := mktable(top(tblptr) ); push(t,tblptr); push(0,offset) }
```
```