# 设计要点：

+   - 每个计算机部件类都有一个getPrice()方法，与一个accept()方法。
+   - PriceVisitor通过accept()方法，调用getPrice()方法，达到计算价格的目的。
+   - 类似地，PartsInfoVisitor类负责调用getDescription方法，实现获取部件的具体描述。