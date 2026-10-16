# 辅助过程部分

用C语言书写一些语义动作中用到的辅助程序

+   - 名字为 yylex() 的词法分析程序必须提供

+   - 函数 main
+   ```
+   main()
+   {
+       return yyparse();
+   }
+   ```

+   - YACC 生成的 yyparse 过程调用一个扫描过程 yylex

+   - yyparse 每次调用 yylex() 时，得到一个二元式的记号：<记号，属性值>。
+     - 返回的记号必须事先在 YACC 说明文件的第一部分中用 %token 声明
+     - 属性值必须通过 YACC 定义的变量 yylval 传给分析程序