# 3. Pipes and Filters architecture

# Functionalities of each filter

+   - Scanner: Lexical Analysis（词法分析）
+     - Misspellings: such as “String” into “Sting”, “Super”, “supper”
+   - Parser: Syntax Analysis（语法分析）
+     - Omission, wrong order of tokens
+   - Semantic checker: Semantic Analysis（语义分析）
+     - Incompatible types: e.g., “float”, “double”
+   - Byte code generator (字节代码生成器): byte code generation:
+     - C/C++ compiler: from source code to assembly code
+     - Java compiler: from Java code to bytecode.
+     - Java跨平台其实就是基于相同的bytecode规范做不同平台的虚拟机，我们的Java程序编译成bytecode后就可以在不同平台跑了。
+   - Byte code optimizer: optimizing byte code
+   - Machine code generator: generating machine code