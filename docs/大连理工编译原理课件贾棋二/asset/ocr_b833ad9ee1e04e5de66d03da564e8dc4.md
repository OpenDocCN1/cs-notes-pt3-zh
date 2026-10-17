# 例题 3

为文法

$S \to (L) \mid a$

$L \to L,S \mid S$

写一个翻译方案，它打印出每个 a 在句子中是第几个字符。例如，当句子是 $(a,(a,(a,a),(a)))$ 时，打印的结果是 2 5 8 10 14。

```
$S' \to \{S.in := 0\}\ S$

$S \to \{\{L.in := S.in + 1\}\ L\ \{S.num := L.num + 2\}\}$

$S \to a\ \{S.num := 1;\ print(S.in+1)\}$

$L \to \{L_1.in := L.in\}\ L_1,\ \{S.in := L_1.in + L_1.num + 1\}\ S\ \{L.num := L_1.num + S.num + 1\}$

$L \to \{S.in := L.in\}\ S\ \{L.num := S.num\}$
```