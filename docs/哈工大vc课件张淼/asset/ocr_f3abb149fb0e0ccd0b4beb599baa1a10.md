# 窗口类的类型

如果我们希望某一变量的数值既有 CS_VREDRAW特性，又有CS_HREDRAW特性，我们只需使用二进制OR（|）操作符将他们进行或运算相组合，如style=CS_VREDRAW | CS_HREDRAW | CS_NOCLOSE。如果我们希望在某一变量原有的几个特征上去掉其中一个特征，用取反（~）之后再进行与（&）运算，就能够实现，如在刚才的style的基础上去掉 CS_NOCLOSE特征，可以用style & ~CS_NOCLOSE实现。