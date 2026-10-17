# # 谓词公式的类型

例7 判断下列公式中，哪些是永真式，哪些是矛盾式？

+   (1) \(\forall xF(x)\rightarrow(\exists x\exists yG(x,y)\rightarrow\forall xF(x))\)

重言式 \(p\rightarrow(q\rightarrow p)\) 的代换实例，故为永真式。

+   (2) \(\neg(\forall xF(x)\rightarrow\exists yG(y))\wedge\exists yG(y)\)

矛盾式 \(\neg(p\rightarrow q)\wedge q\) 的代换实例，故为永假式。

+   (3) \(\forall x(F(x)\rightarrow G(x))\)

解释\(I_1\): 个体域N, \(F(x):x>5\), \(G(x):x>4\), 公式为真  
解释\(I_2\): 个体域N, \(F(x):x<5\), \(G(x):x<4\), 公式为假  
结论: 非永真式的可满足式