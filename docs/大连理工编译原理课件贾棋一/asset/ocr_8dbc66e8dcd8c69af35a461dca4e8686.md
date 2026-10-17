# 3.2 语言和文法

# 3.2.3 验证文法产生的语言

$G:S\rightarrow(S)S\mid\varepsilon\quad L(G)=\text{配对的括号串的集合}$

按推导步数进行归纳：推出的是配对括号串

+   - 归纳基础：$S\Rightarrow\varepsilon$
+   - 归纳假设：少于 $n$ 步的推导都产生配对的括号串
+   - 归纳步骤：$n$ 步的最左推导如下：
+     $S\Rightarrow(S)S\Rightarrow^*(x)S\Rightarrow^*(x)y$