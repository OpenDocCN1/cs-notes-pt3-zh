# 类模板的static成员

+   - 可以通过类类型的对象访问类模板的static成员
+     - 也可以通过使用作用域操作符直接访问成员
+       Foo<int> fi, fi2; // instantiates Foo<int> class
+       size_t ct = Foo<int>::count(); // instantiates Foo<int>::count
+       ct = fi.count(); // ok: uses Foo<int>::count
+       ct = fi2.count(); // ok: uses Foo<int>::count
+       ct = Foo::count(); //error: which template instantiation?