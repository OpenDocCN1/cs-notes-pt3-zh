# I/O流的状态

C++ I/O流的状态用ios_base中一组状态标志位来表示，同时定义了一组判断、操纵这些标志位的成员函数，常用的有

+   - bool good()const: 刚进行的操作成功时返回 true，否则返回 false;
+   - bool fail()const: 与good()相反，刚进行的操作失败时返回 true，否则返回 false;