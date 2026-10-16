# 4.3.4 条件临界区
Conditional Critical Region

+   - 背景
+     - PV操作低级，容易用错
+   - 条件临界区形式
+     - region V when B do S
+   - 执行S条件
+     - 没有其它进程处于与V相关的条件临界区中
+     - 进入S时B为true