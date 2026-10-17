# # 例 P135 不能访问超类中被声明成 private 的成员

```
/* In a class hierarchy, private members remain private
to their class.
This program contains an error and will not compile.
*/
// Create a superclass.
class A {
int i; // public by default
private int j; // private to A
void setij(int x, int y) {
i = x;
j = y;
}
}
```