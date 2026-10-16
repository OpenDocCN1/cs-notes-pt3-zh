# Visitor Pattern

# ObjectStructure (Program) (can be omitted)

+   - Can enumerate its elements.
+   - May provide a high-level interface to allow the visitor to visit its elements.
+   - May either be a composite or a collection such as a list or a set.

+   - 该类可以使用一个聚合结构例如Java ArrayList将被访问对象集合在一起，然后再使用一个循环语句批量调用accept方法。