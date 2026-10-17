# # 重言式和永假式

+   \(P \lor \neg P \Leftrightarrow T\), \(P \land \neg P \Leftrightarrow F\)

+   永真式与永假式取决于公式本身的结构，不依赖变元的真值指派。

+   例如\((P \land Q \lor R) \lor \neg(P \land Q \lor R)\)就是一个永真式

+   \((P \land Q \lor R) \land \neg(P \land Q \lor R)\)就是一个永假式

+   永真式的性质：若公式\(A\)是永真式，并且\(P_1\), \(P_2\), ..., \(P_n\)是出现于\(A\)中的变元，若用公式\(B\)代换\(A\)中的原子变元\(P_i(i=1,2,...,n)\),所得到的公式设为\(A'\), 则\(A'\)也是永真式。（注意代换过程从左向右要进行到底）。对非永真式，这条性质不一定成立。