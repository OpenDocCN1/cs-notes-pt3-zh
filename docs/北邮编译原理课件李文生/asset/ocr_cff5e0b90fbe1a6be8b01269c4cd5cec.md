例：有如下产生PASCAL类型子集的文法：

*type→simple | ↑id | array[simple] of type*
*simple→integer | char | num dotdot num*（文法4.2）

分析输入串：array [num dotdot num] of char

+   - *type*的三个候选式，有：
+     - `FIRST(simple)={ integer, char, num }`
+     - `FIRST(↑id)={ ↑ }`
+     - `FIRST(array[simple] of type)={ array }`
+   - *simple*的三个候选式，有：
+     - `FIRST(integer)={ integer }`
+     - `FIRST(char)={ char }`
+     - `FIRST(num dotdot num)={ num }`