# 表5-2　带有继承属性L.in的语法制导定义

| 产生式 | 语义规则 |
|---|---|
| $D\to TL$ | $L.in:=T.type$ |
| $T\to\mathbf{int}$ | $T.type:=\mathbf{integer}$ |
| $T\to\mathbf{real}$ | $T.type:=\mathbf{real}$ |
| $L\to L_1,\mathbf{id}$ | $L_1.in:=L.in$<br>$addtype(\mathbf{id}.entry,L.in)$ |
| $L\to\mathbf{id}$ | $addtype(\mathbf{id}.entry,L.in)$ |