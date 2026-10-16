# 迭代器模式

# ◆ 模式扩展

+   - Java迭代器代码示例：

```
Iterator iterator = collection.iterator();  // collection是已实例化的集合对象
iterator.next();                         // 跳过第一个元素
iterator.remove();                       // 删除第一个元素
```

```
iterator.remove();
iterator.next();  //该语句不能去掉，去掉则程序运行抛异常，因为第二次删除时将找
                //不到可供删除的元素。
iterator.remove();
//上面代码片段可用于删除两个相邻的元素
```