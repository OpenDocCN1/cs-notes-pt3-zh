3、若项目 A→α。∈k，那么对输入符号 a，若 a∈FOLLOW(A)，则置 ACTION[k,a]=r_j，其中 A→α 为文法 G′ 的第 j 个产生式。

4、若项目 E′→E。∈k，则置 ACTION[k,#]=accept

5、ACTION 表中不能用步骤 2~4 填入信息的空白格，均置 error