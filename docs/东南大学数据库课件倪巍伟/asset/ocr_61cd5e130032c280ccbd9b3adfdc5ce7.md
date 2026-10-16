为了从已知的函数依赖推导出其他函数依赖，Armstrong提出了一套推理规则，我们常称为Armstrong公理（Armstrong saxions）。其推理规则可归结为如下三条：
A1: 自反律（reflexivity）
如果 Y ⊆ X ⊆ U，则 X → Y 成立。这是一个平凡函数依赖。
A2: 扩展律（augumentation）
如果 X → Y 成立，且 Z ⊆ U，则 X Z → Y Z 成立。式中，X Z 和 Y Z 是 X ∪ Z 和 Y ∪ Z 的简写，以后将沿用此表示法。
A3: 传递律（transitivity）
如果 X → Y，Y → Z 成立，则 X → Z 成立。