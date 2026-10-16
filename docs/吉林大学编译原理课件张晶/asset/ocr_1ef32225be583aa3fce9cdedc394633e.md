# 3. 赋值语句的中间代码

+   ◆ 赋值语句的形式为：Left := Right，

+   ◆ 赋值语句的四元式结构为：

+   > Left 的中间代码

+   > Right 的中间代码

+   > (FLOAT , Right , _ , t )

+   > (ASSIG , Right(t) , - , Left )