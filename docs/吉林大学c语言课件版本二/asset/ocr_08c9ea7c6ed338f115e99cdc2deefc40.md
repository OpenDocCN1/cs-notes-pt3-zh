1 A B C D E F G      A      B C D E F G A
2 B C D E F G A      B B B    C D E F G A B
3 C D E F G A B      C C C C C D E F G A B C
4 D E F G A B C      D D D D D D E F G A B C D
5 E F G A B C D      C C C C C F G A B C D E
6 F G A B C D E      B B B    G A B C D E F
7 G A B C D E F      A        A B C D E F G
上半部分
for(j=i;i<=7;j++)  打印字符' A'+j-
for(i=1;j<i;j++)  打印字符' A'+j-
for(k=1;k<6-i;k++) 打印空格
for(k=1;k<2*i;k++) 打印字符' A'+i-
for(k=1;k<6-i;k++) 打印空格
for(l=i+1;l<=7;l++) 打印字符' A'+l-
for(l=1;l<=i;l++)  打印字符' A'+l-