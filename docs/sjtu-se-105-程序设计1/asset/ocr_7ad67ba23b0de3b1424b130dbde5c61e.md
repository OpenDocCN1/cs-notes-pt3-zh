# 类模板中的友元声明

+   - 一般模板友元关系
+     - 友元可以是类模板或函数模板
+     - `template<class Type> class Bar{
+       template <class Type> friend class Foo1;
+       template <class Type> friend void templ_fcn1(const T&);
+       //....
+     }`
+     - Foo1的任意实例都可以访问Bar的任意实例的私有元素
+     - templ_fcn1的任意实例可以访问Bar的任意实例
+     - 对Bar的每个实例而言，Foo和templ_fcn1的所有实例都是友元