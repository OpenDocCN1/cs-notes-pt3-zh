# Ival_box的使用

```
void interact(Ival_box* pb)
{
    pb->prompt();
    int i = pb->get_value();
    if(pb->was_changed()){
        //...
    }
    else {
        //...
    }
}
```

```
class Ival_slider:public Ival_box{};
void some_fct()
{
    Ival_box* p1 = new Ival_slider(0,5);
    interact(p1);
    Ival_box* p2 = new Ival_dial(1,12);
    interact(p2);
}
```

大部分图形界面系统都提供了一个类，其中定义了屏幕实体的基本性质，如果采用"Big Bucks Inc"的系统，各个类定义如下

```
class Ival_box : public BBWindow{/*...*/};
class Ival_slider : public Ival_box{/*...*/};
class Ival_dial : public Ival_box{/*...*/};
class Flashing_ival_slider : public Ival_slider{/*...*/};
class Popup_ival_slider : public Ival_slider{/*...*/};
```

# 12.4.1.1 评论

+   - 缺点1：使用BBWindow作为Ival_box的基类（BBWindow）是一个实现细节，如果把Ival_box使用在其他的系统中，必须定义又不相同的版本
+     class Ival_box : public BBWindow{/*...*/};
+     class Ival_box : public CWindow{/*...*/};
+     class Ival_box : public IWindow{/*...*/};
+     class Ival_box : public LSWindow{/*...*/}
+   - 缺点2：每个派生类都共享着Ival_box里声明的基本数据，也即在Ival_box中不应包含具体数据
+   - 缺点3：修改BBWindow将使得很多程序就其重新相关代码
+   - 缺点4：无法在一个混合式的环境(多种图形界面系统)里使用

# 12.4.2 抽象类

+   - 解决上述问题
+     - 用户界面系统应该是一个实现细节，对于不希望了解细节的用户应该是隐藏的
+     - 类Ival_box应该不包括数据
+     - 在用户界面修改后，不应该要求重新编译那些使用Ival_box这一族类的代码
+     - 针对不同界面系统的Ival_box应该能在我们的程序库里共存
+   - 本小节介绍的是一种能够最清晰地映射到C++语言中的途径