

## 编译原理与编译程序构造

翟玉青，张志正

[yqzhai@seu.edu.cn](mailto:yqzhai@seu.edu.cn)

seu_zzz@seu.edu.cn

## 主要参考资料

+   1. Compilers: Principles, Techniques, and Tools (2nd Edition), A.V Aho, Ravi Sethi, J.D Ullman, 人民邮电出版社, 2008
+   2. Modern Compiler Implementation in C, Andrew W Appel, 人民邮电出版社, 2005
+   3. Modern Compiler Implementation in Java, Andrew W Appel, 高等教育出版社, 2003
+   4. 编译原理及编译程序构造，秦振松，东南大学出版社, 1997
+   5. 程序设计语言编译原理，陈火旺，国防工业出版社, 2000

## 编译器在系统中的作用

![](img/353f619caa6c5715591f2105bdfa2865_2_0.png)

## 为什么要开设编译课程？

2、 你在编译器中使用的许多算法和模型都是基础性的，在其他地方也会有用：

- automata, regular expressions (lex’ing)
- context-free grammars, trees (parsing)
- hash tables (symbol table)
- dynamic programming

## 为什么要开设编译课程？

# dynamic programming

- Characterize the structure of an optimal solution.
- Recursively define the value of an optimal solution.
- Compute the value of an optimal solution in a bottom-up fashion.
- Construct an optimal solution from computed information.

## 为什么要开设编译课程？

3、 编写更高效的程序

Notes: Compiler writing spans programming languages, machine architecture, language theory, algorithms, and software engineering. And the ideas behind principles and techniques of a compiler writing can be used many times in the career of a computer scientist.

## 为什么要开设编译课程？

4. 编译器中使用的分析和生成技术对更广泛的一类问题也很有用，例如解析命令行或搜索查询，分析或生成标记语言。

## 如何讲授编译课程？

![](img/353f619caa6c5715591f2105bdfa2865_8_0.png)

Translating: Oral Translating    Compiling: Written Translating

## 程序如何被处理和运行？

![](img/353f619caa6c5715591f2105bdfa2865_9_0.png)

## 课程目标

+   1. 提供 **解析技术** 的知识。
+   2. 提供使用不同解析技术进行 **错误检测和恢复** 的知识。
+   3. 提供编程语言的 **语义和语法分析** 方面的概念。
+   4. 提供中间代码生成和 **优化** 方面的概念。

## 课程框架

+   1、 编译导论
+   2、 编程语言和语法定义
+   3、 词法分析
+      理论模型：正则文法和有限自动机
+      实现：词法分析程序
+      工具 : LEX
+   4、 语法分析
+      理论模型：上下文无关文法和下推自动机，LL(1) 文法，LR 文法
+      实现：递归下降分析
+         算符优先分析
+         LR 分析
+         使用含二义性文法
+      工具: YACC

## 课程框架

+   5、中间代码生成和语法制导翻译
+   6、类型检查和运行环境
+   7、代码优化：块优化，循环优化，全局优化
+   8、目标代码生成

## 如何学习本课程？

+   1、 注重深入理解原理
+   2、 注意各章节之间的关系
+   3、 多做练习，多实践并将理论与实验结合起来

## 如何评价？

+   1、 练习 – 10%
+   2、 实验 – 20% （共 2 次实验）
+   3、 期末考试 –70%

## 第 1 章 编译导论

### 1、 什么是编译器？

**非常通用的定义：** 它是一段将一种（人工）语言 Lang1 的程序翻译成另一种（人工）语言 Lang2 的程序的软件。

**更狭义的定义：** 我们主要关注的是 Lang1 是人类喜欢编程的编程语言，而 Lang2 是（或更接近于）机器语言，计算机能够“理解”并执行的情况。

**额外规定：** 即使输入不是 Lang1 的有效程序，编译器也应给出某种反馈。也就是说，它应给出错误信息，解释为什么输入不是有效程序。

