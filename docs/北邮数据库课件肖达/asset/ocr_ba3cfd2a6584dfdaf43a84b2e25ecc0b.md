# 规则

# 创建规则

+   - CREATE RULE <规则名> AS <条件表达式>
+   - <条件表达式>可以是能用于WHERE子句中的任何表达式，可以包含算术运算符、关系运算符和谓词，如IN LIKE、BETWEEN等，但必须以字符@开头。
+   - 如:

+   - @Birthday >= '1980-01-01' and @Birthday <= getdate()
+   - @Grade IN ('1','2','3','4','5')
+   - @value LIKE '[a-z]%[0-9]'

# 例：创建规则ID_Rule

+   - CREATE RULE ID_Rule
+   - AS @ID LIKE '[0-9][0-9][0-9]'