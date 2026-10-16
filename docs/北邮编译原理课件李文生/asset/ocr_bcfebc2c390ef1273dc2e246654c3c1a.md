# 定义4.16：闭包（closure）

设I是文法G的一个LR(1)项目集，closure(I)是从I出发，用下面的方法构造的项目集

+   1. I中的每一个项目都属于closure(I)；
+   2. 若项目[A→α·Bβ，a]属于closure(I)，且B→η是G的一个产生式，则对任何终结符号b∈FIRST(βa)，若项目[B→·η，b]不属于集合closure(I)，则将它加入closure(I)；
+   3. 重复规则(2)，直到closure(I)不再增大为止。