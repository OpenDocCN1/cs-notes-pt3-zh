+   - 编译器按如下步骤解释多次出现的函数名
+     - 如果两个函数的参数表中参数的个数或类型不同，则认为这两个函数是重载的
+       ```
+       void print( const string & );
+       void print( vector<int> & );
+       ```
+     - 如果两个函数的返回类型和参数表精确匹配，则第二个声明被视为第一个的重复声明（编译不报错）
+       ```
+       void print( const string &str );
+       void print( const string & );
+       ```