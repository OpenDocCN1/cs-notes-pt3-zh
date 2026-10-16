# ★产生问题的原因
属性间约束关系（即数据间的依赖关系）太强

# ★解决问题的方法：分解关系

+   解二：
+   - `students`（`sno`，sname）
+   - `courses`（`cno`，`tno`，cname）
+   - `teachers`（`tno`，`cno`，tname）
+   - `enrolls`（`sno`，`cno`，grade）

+   解三：
+   - `students`（`sno`，sname）
+   - `courses`（`cno`，cname）
+   - `teachers`（`tno`，tname）
+   - `enrolls`（`sno`，`cno`，grade）
+   - `teaching`（`tno`，`cno`）