+   - 对非常小的对象使用按值传递
+   - 对大对象使用按常量引用传递
+   - 优先使用返回结果而不是通过引用参数来修改对象
+   - 只有在必需时才使用按引用调用
+   - 例如
+     class Image { /* objects are potentially huge */ };
+     void f(Image i); ... f(my_image); // oops: this could be s-l-o-o-o-w
+     void f(Image& i); ... f(my_image); // no copy, but f() can modify my_image
+     void f(const Image&); ... f(my_image); // f() won"t mess with my_image

```
class Image { /* objects are potentially huge */ };
void f(Image i); ... f(my_image); // oops: this could be s-l-o-o-o-w
void f(Image& i); ... f(my_image); // no copy, but f() can modify my_image
void f(const Image&); ... f(my_image); // f() won"t mess with my_image
```