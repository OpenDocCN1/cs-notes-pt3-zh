# I/O重定向

+   问题: Unix内核如何实现 I/O 重定向?
+   linux> ls > foo.txt

+   回答: 调用 dup2(oldfd, newfd)函数
+   复制描述符表表项 oldfd 到描述符表表项 newfd, 覆盖描述符表表项newfd以前的内容。

描述符表
调用 dup2(4,1)之前

描述符表
调用 dup2(4,1)之后