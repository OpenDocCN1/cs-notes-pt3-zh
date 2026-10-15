# IntSet示例

+   - 表示不变式:
+     - 在任何方法执行前和执行后都必须遵守的规则
+   - 由于是数组，并且数组具有最大尺寸，因此:
+     - 我们需要选择最大尺寸，并修改类的概況
+     - // OVERVIEW: a mutable set of integers, |set| <= 100
+     - 我们还需要修改insert函数的effect注释
+     - // EFFECTS: this = this + {v} if room, throws int 100 otherwise