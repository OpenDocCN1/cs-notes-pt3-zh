# using声明

+   - 在使用的位置上引入名字空间成员，类似于定义

```
namespace blip {
    int bi = 16, bj = 15, bk = 23;
}
int bj = 0;
void manip() {
    using blip::bi;
    ++bi;                         // 设置 blip::bi 为 17
    using blip::bj;               // 隐藏全局域中的 bj
    ++bj;                         // 设置 blip::bj 为 16
    int bk;                       // bk 在局部域中声明
    using blip::bk;      // 错误：在 manip() 中重复定义 bk
}
```