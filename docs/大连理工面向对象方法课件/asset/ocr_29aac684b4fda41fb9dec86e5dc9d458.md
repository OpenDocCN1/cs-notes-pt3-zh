```
}

CNetGameFactory::~CNetGameFactory()
{
}
```

```
CEasyGame * CNetGameFactory::createEasyGame()
{
    return new CNetEasyGame;
}
```

```
CDifficuteGame* CNetGameFactory::createDifficuteGame()
{
    return new CNetDifficuteGame;
}
```

上面两个方法返回两个产品的2个产品，而不论用户选择什么游戏类型。

```
void playGame(int i,int j)//必须用
{
    ClocalGameFactory cLocalGameFactory;//具体工厂对象
    CNetGameFactory cNetGameFactory; //具体工厂对象
    if(1==i)
    {
        if(4==j)
        {
            cLocalGameFactory.createEasyGame()->play();
        }
        else
        {
            cLocalGameFactory.createDifficuteGame()->play();
        }
    }
    else if(2==i)
    {
        if(4==j)
        {
            cNetGameFactory.createEasyGame()->play();
        }
        else
        {
            cNetGameFactory.createDifficuteGame()->play();
        }
    }
}
```