```
```cpp
private:
    static MazeFactory* __instance;
};
```
```

相应的实现是：

`MazeFactory* MazeFactory::__instance = 0;`

```cpp
MazeFactory* MazeFactory::Instance () {
    if (__instance == 0) {
        __instance = new MazeFactory;
    }
    return __instance;
}
```

然后：我们考虑当存在MazeFactory的多个子类，而且应用必须决定使用哪一个子类时的情况。我们将通过环境变量选择适当的种类并根据该环境变量的值增加代码用于实例化适当的MazeFactory子类。Instance 操作是增加这些代码的好地方，因为它已经实例化了MazeFactory：

```
```cpp
MazeFactory* MazeFactory::Instance () {
    if (__instance == 0) {
        const char* mazeStyle = getenv("MAZESTYLE");

        if (strcmp(mazeStyle, "bombed") == 0) {
            __instance = new BombedMazeFactory;

        } else if (strcmp(mazeStyle, "enchanted") == 0) {
            __instance = new EnchantedMazeFactory;

            // ... other possible subclasses

        } else {        // default
            __instance = new MazeFactory;
        }
    }
    return __instance;
}
```
```

注意，无论何时定义一个新的 MazeFactory 的子类，Instance 都必须被修改。在这个应用中这可能没什么关系，但对于定义在一个框架中的抽象工厂来说，这可能是一个问题。

一个可能的解决办法将是使用在实现一节中所描述的注册表的方法。此处动态链接可能也很有用——它使得应用不需要装载那些用不着的子类。

介绍多线程的情况，参见后文。