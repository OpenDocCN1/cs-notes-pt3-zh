# # 解法一： 直接翻译

# ## 十六进制数具有如下三种形式

n<sub>r</sub>n<sub>r-1</sub>n<sub>r-2</sub>...n<sub>1</sub>n<sub>0</sub>.n<sub>-1</sub>n<sub>-2</sub>...n<sub>-s</sub>

n<sub>r</sub>n<sub>r-1</sub>n<sub>r-2</sub>...n<sub>1</sub>n<sub>0</sub>

.n<sub>-1</sub>n<sub>-2</sub>...n<sub>-s</sub>

# ## 翻译成十进制数的公式

d=n<sub>r</sub>∗16<sup>r</sup>+n<sub>r-1</sub>∗16<sup>r-1</sup>+...+n<sub>0</sub>∗16<sup>0</sup>+n<sub>-1</sub>∗16<sup>-1</sup>+n<sub>-2</sub>∗16<sup>-2</sup>+...+n<sub>-s</sub>∗16<sup>-s</sup>=(...(((0)∗16+n<sub>r</sub>)∗16+n<sub>r-1</sub>)∗16...+n<sub>1</sub>)∗16+n<sub>0</sub>+n<sub>-1</sub>∗16<sup>-1</sup>+n<sub>-2</sub>∗16<sup>-2</sup>+...+n<sub>-s</sub>∗16<sup>-s</sup>