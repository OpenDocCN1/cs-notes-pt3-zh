# 定义4.12：闭包(closure)

设I是文法G的一个LR(0)项目集合，closure(I)是从I出发，用下面的方法构造的项目集：

+   (1) I中的每一个项目都属于closure(I);

+   (2) 若项目A→α·Bβ属于closure(I)，且B→η是G的一个产生式，若B→·η不属于closure(I)，则将B→·η加入closure(I);

+   (3) 重复规则(2)，直到closure(I)不再增大为止。