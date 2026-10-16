# 单例模式

+   模式扩展
+   懒汉式单例类

```
LazySingleton
- instance : LazySingleton = null
- LazySingleton ()
+ getInstance () : LazySingleton

instance

creates

if(instance==null)
    instance=new LazySingleton();
return instance;
```