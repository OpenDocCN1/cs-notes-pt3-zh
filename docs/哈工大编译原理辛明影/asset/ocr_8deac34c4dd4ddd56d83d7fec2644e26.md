# 数组元素地址计算的翻译方案设计

下标变量访问的产生式

L → id[Elist] | id

Elist → Elist, E | E

改造后的文法：

L → Elist ] | id

Elist → Elist, E | id[E