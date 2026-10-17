（**略讲**）创建 Singleton 类的子类的一个更灵活的方法是使用一个单件注册表。可能的 Singleton 类的集合不是由 Instance 定义的，Singleton 类可以根据名字在一个众所周知的注册表中注册它们的单件实例。

```
class Singleton
{
public:
    static void Register(const string& name, Singleton*);
    static Singleton* Instance();
protected:
    static Singleton* Lookup(const string& name);
private:
    static Singleton* _instance;
    static map<string, Singleton*> _registry;
};
```