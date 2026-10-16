# 3.3 CACHE与主存之间的映射

# 组相联映射（Set Associative Mapping）

+   映射关系：Cache 分成 K 组，每组分成 L 块；主存的块 J 以下列原则映射到 Cache 的组 I 中的任何一块。
+   I = J mod K

+   实际上主存与Cache都分成 K 组，主存每一组内的块数与Cache一组内的块数不一致，主存组M内的某一块只能映射到Cache组M内,但可以是组M内的任意一块。

![](bbox=[0.04, 0.57, 0.98, 0.84])