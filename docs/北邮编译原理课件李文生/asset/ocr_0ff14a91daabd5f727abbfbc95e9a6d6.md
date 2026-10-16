# 3. 涉及数组元素的赋值语句
——S属性定义

S→L:=E
E→E₁+E₂
E→(E₁)
E→L
L→id | id [ Elist ]
Elist→Elist₁ , E | E

语句 X:=A [ i, j ]的分析树

![](bbox=[0.55, 0.35, 0.9, 0.97])

改写文法：
L→id | Elist ]
Elist→Elist₁ , E | id[E