最后考虑输出部分，我们把结果输出成两个 26×13 的表，每个表元素是相应字母偶的出现次数：

* a b c d e ... m
a
b
...
z

* n o p q r ... z
a
b
...
z

out 输出
def
outone('a','m') 输出a..m部分
outone('n','z') 输出n..z部分
结束