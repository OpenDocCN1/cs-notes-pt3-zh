# 计算机部件销售的例子

+   - 本设计与例2设计的不同之处：
+     在本设计中，使用了CompositeStructure类。ComputerPartsGUI类根据用户请求提交的计算机部件名称，
+     - 创建各个相应的部件对象，然后，
+     - 将这些对象添加到复合对象CompositeStructure中。

+   - CompositeStructure对象负责接受访问者PriceVisitor对象，对该复合对象所包含的各个对象访问。