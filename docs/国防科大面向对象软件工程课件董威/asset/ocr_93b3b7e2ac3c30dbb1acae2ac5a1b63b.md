# § 6.3 UML动态建模机制
§ 6.3.1 顺序（Sequence）图

![](bbox=[0.008, 0.156, 0.997, 0.981])

参与对象：An Order Entry window；An Order；An Order Line；A Stock Item

Prepare()

*[for all order lines] prepare()

hasStock:=check()

[hasStock]
remove()

needsRecord:=needsToRecord()

[needsReorder]
new

[hasStock]new

Object

Message

Iteration

Condition

Self-Delegation

Return

A Reorder Item

A Delivery Item

Creation