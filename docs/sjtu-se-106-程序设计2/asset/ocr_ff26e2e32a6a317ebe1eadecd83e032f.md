# 例10-13、例10-14

函数对象

+   - 使用两种方式定义表示乘法的函数对象
+     - 通过定义普通函数（例10-13）
+     - 通过重载类的“()”运算符（例10-14）

+   - 用到以下算法：
+     template<class InputIterator, class Type, class BinaryFunction>
+     Type accumulate(InputIterator first, InputIterator last, Type val, BinaryFunction binaryOp);
+     - 对[first, last)区间内的数据进行累“加”，binaryOp为用二元函数对象表示的“加”运算符，val为累“加”的初值