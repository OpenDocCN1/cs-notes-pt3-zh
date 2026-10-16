# 访问控制权限

+   Java中存在四种访问权限:
+   - private访问权限
+   - default（默认）访问权限
+   - protected访问权限
+   - public访问权限

| 范围 | private | default | protected | public |
| --- | --- | --- | --- | --- |
| 同一类 | √ | √ | √ | √ |
| 同一包中的类 |  | √ | √ | √ |
| 不同包的子类 |  |  | √ | √ |
| 其他包中的类 |  |  |  | √ |