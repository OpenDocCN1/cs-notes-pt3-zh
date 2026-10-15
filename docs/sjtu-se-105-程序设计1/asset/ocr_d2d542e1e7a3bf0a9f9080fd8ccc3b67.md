# 函数声明

+   - 函数声明可以使得函数被提前使用
+   - 函数声明由函数返回类型、函数名和形式参数表构成。
+     ```
+     bool IsPrimer( int x);        //函数声明，判断x是否为素数
+     int main(){
+         for(int i=2; i<10000; i++)
+         if(IsPrimer(i))    //函数使用
+             cout<<i;
+     }
+     ```
+   - 函数声明中的参数名不是必需的
+     ```
+     bool IsPrimer( int x);        //函数声明，判断x是否为素数
+     bool IsPrimer( int );         //函数声明，判断参数是否为素数
+     ```