# 7.3.3 带有数组引用的赋值语句的翻译

翻译模式如下：

+   2. E→E1+E2
+   {E.addr: =newtemp;
+   emit（E.addr=E₁.addr+E₂.addr）}

+   3. E→（E1）
+   {E.addr : =E1.addr}