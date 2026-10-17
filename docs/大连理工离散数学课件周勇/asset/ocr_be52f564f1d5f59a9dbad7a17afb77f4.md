# # 前束范式

任意一个公式都可以转化成与之等价的前束范式，方法如下：

-消去公式中的联结词 \(\leftrightarrow\) 和 \(\rightarrow\)，例如

\( A \leftrightarrow B \iff (A \land B) \lor (\neg A \land \neg B) \)

\( A \rightarrow B \iff \neg A \lor B \)

-将公式内的否定符号深入到谓词变元前并化简到谓词变元前只有一个否定号；

-利用改名、代入规则使所有的约束变元均不同名，且使自由变元与约束变元亦不同名；

-扩充量词的辖域至整个公式。