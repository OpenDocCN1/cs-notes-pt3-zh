# (Recall from chapter 2 about foreign key)

Assume there exists relation r and s: r(A, **B**, C), s(**B**, D), we say attribute **B** is **foreign key** from relation r, and r is called *referencing relation* (参照关系), and s is called *referenced relation* (被参照关系).

+   - e.g.
+     - ◆ 学生(学号, 姓名, 性别, **专业号**, 年龄) --参照关系
+     - 专业(**专业号**, 专业名称) --被参照关系（目标关系）
+     - 其中属性 **专业号** 称为关系 *学生* 的外码。

+   - ◆ Account(**account-number**, **branch-name**, balance) --参照关系
+     - Branch(**branch-name**, branch-city, assets) --被参照关系

参照关系中外码的值必须在被参照关系中实际存在，或为 null。