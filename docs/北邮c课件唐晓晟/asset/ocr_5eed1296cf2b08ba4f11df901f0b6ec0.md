# 14.6.3.1 异常的用户映射

本段描述异常的默认 unexpected_handler 决定，它是通常 >over >ride> 中 std::set_unexpected() 设置的

重新定义 unexpected() 激活时，我们先使用资源申请即初始化技术。为 unexpected() 搞设定一个类 STC

```
typedef void(*unexpected_handler)();
 unexpected_handler set_unexpected(unexpected_handler);
 class STC{
  unexpected_handler old;
 public:
  STC(unexpected_handler f){old=set_unexpected(f);}
  ~STC(){set_unexpected(old);}
 };
```

# 异常的用户映射示例

假设 void g() throw(Yerr) 是可能调用 unexpected() 的函数。数据发送失败原因是发送到网络环境中...

定义一个类，使它具有希望的 unexpected() 定义

```
class Yunexpected:public Yerr{};
 void throwY() throw(Yunexpected){ throw Yunexpected();}
 // 在使用 unexpected() 请设置时，throwY 抛出具有未预期异常类型为 Yunexpected
 void networked_g() throw(Yerr){
  // STC xx(&throwY); // 并且在反向描述 Yerr 产生的
  // 因为 Yunexpected 是从 Yerr 派生的
  g();
 } // 现在 unexpected() 抛出 Yunexpected，但丢去了异常的类型
```

# 14.6.3.2 找回异常的类型

```
class `Unexpected:public Yerr{
 public:
  Network_exception* pe;
  Yunexpected(Network_exception* p):pe(p?p->clone():0){}
  ~Yunexpected(){delete pe;}
 };
 // clone() 在有异常时为异常提供一个拷贝，当异常是对象时存在
 void throwY() throw(Yunexpected){
  try{
   throwY(); // throw 出 Yunexpected 时
   throw; // 需要保持原有异常
  }
  catch(Network_exception& p){
   throw Yunexpected(&p);
  }
  catch(...){
   throw Yunexpected(0);
  }
 }
```

实际的异常是 Network_exception

# 14.7 未捕捉的异常

如果抛出的一个异常未被捕捉，那么就会调用函数 std::terminate()

未捕捉的异常由 _uncaught_handler 确定，它由 <exception> 里的 std::set_terminate() 设置

提出 terminate() 的原因是，少数情况下，设强制能用不那么精确的错误处理技术终止异常处理过程

如果希望在发生未捕捉异常时保证进行清理工作，可以为 main() 添加一个捕捉一切的处理器 (但是仍然无法捕捉在全局变量的构造和析构中抛出的异常)