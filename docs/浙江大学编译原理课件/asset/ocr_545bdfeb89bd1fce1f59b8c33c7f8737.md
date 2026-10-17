# # 7.5.3 Pass by Value-Result

+   - If pass by reference is used, **a** has value 3 after p is called.
+   - If pass by value-result, **a** has value 2 after p is called.

```
```cpp
Void p(int x, int y)
{
 ++x;
 ++y;
}
main( )
{ int a=1;
 p(a, a);
 return 0;
}
```
```