+   为了避免下面这种冗长的写法
+   ```
+   std::cout << "Please enter stuff... \n";
+   ```
+   可以写一条 “using 声明”
+   ```
+   using std::cout; // when I say cout, I mean std::cout
+   cout << "Please enter stuff... \n"; // ok: std::cout
+   cin >> x; // error: cin not in scope
+   ```

+   或者可以写一条 “using 指示符”
+   ```
+   using namespace std; // “make all names from namespace std available”
+   cout << "Please enter stuff... \n"; // ok: std::cout
+   cin >> x; // ok: std::cin
+   ```