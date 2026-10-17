

根据里氏代换原则，任何接收父类型的地方，都应当能够接收子类型。因此，实际上系统所需要的，仅仅是类型与这些抽象产品角色相同的一些实例，而不是这些抽象产品的实例。换言之，也就是这些抽象产品的具体子类的实例。

工厂类负责创建抽象产品的具体子类的实例如下图所示。这就是抽象工厂模式用意的基本含义。

![](img/3b4669cf00b2833fe526284506f3f342_60_0.png)

## 第三段

接下来的一个问题就是，如果每个抽象产品都有多于一个的具体子类的话，工厂角色怎么知道实例化哪一个子类呢？比如下面的类图中就给出了两个抽象产品，而每一个抽象产品都有两个具体产品。

抽象工厂模式提供两个具体工厂角色，分别对应于这两个具体产品角色。每一个具体工厂角色仅负责某一个具体产品角色的实例化。每一个具体工厂类负责创建抽象产品的某一个具体子类的实例如下图所示。

![](img/3b4669cf00b2833fe526284506f3f342_60_1.png)

涂有颜色的两个具体产品属于同一个产品族。

## 产品族：指位于不同产品等级结构中，功能相关联的产品组成的家族。P90303

### 例如：

- 抽象产品1代表水果，具体有香蕉和苹果；
- 抽象产品2代表蔬菜，具体有白菜和土豆；

则南方的香蕉和南方的白菜可以是一个产品族、北方的苹果和北方的土豆也可以是一个产品族。

理解了这三个步骤，就不难理解“抽象工厂”这个名字的来源了。“抽象”来自“抽象产品角色”，而“抽象工厂”就是抽象产品角色的工厂。

## 三. 举例：系统的设计

从上图可以看出，抽象工厂模式涉及到以下的角色。

1. **抽象工厂（AbstractFactory）角色**：担任这个角色的是工厂方法模式的核心，它是与应用系统的商业逻辑无关的。通常使用抽象类实现，而所有的具体工厂类必须实现这个抽象类。

2. **具体工厂类（Concrete Factory）角色**：这个角色直接在客户端的调用下创建产品的实例。这个角色含有选择合适的产品对象的逻辑，而这个逻辑是与应用系统的商业逻辑紧密相关的。通常使用具体类实现这个角色。

3. **抽象产品（Abstract Product）角色**：担任这个角色的类是工厂方法模式所创建的对象的父类，或它们共同拥有的接口。通常使用抽象类实现这一角色。

4. **具体产品（Concrete Product）角色**：抽象工厂模式所创建的任何产品对象都是某一个具体产品类的实例。这是客户端最终需要的东西，其内部一定充满了应用系统的商业逻辑。通常使用具体类实现这个角色。

![](img/3b4669cf00b2833fe526284506f3f342_61_0.png)

![](img/3b4669cf00b2833fe526284506f3f342_62_0.png)

说明：

1. 在此实例中，产品等级结构有两个：CEasyGame，CDiffucuteGame。

2. 从抽象工厂派生出两个工厂：CLocalGameFactory，CNetGameFactory。

3. 每一个工厂负责一个产品族：
   - CLocalGameFactory 负责生产：CLocalEasyGame 和 CLocalDiffucuteGame
   - CNetGameFactory 负责生产：CNetEasyGame 和 CNetDiffucuteGame

```cpp
class CDiffucuteGame//产品父类 1
{
public:
    virtual void play() = 0;
    CDiffucuteGame();
    virtual ~CDiffucuteGame();
};
CDiffucuteGame::CDiffucuteGame()
{
}
CDiffucuteGame::~CDiffucuteGame()
{
}

class CEasyGame//产品父类 2
{
public:
    virtual void play() = 0;
    CEasyGame();
    virtual ~CEasyGame();
};
CEasyGame::CEasyGame()
{
}
CEasyGame::~CEasyGame()
{
}

class CGameFactory://工厂父类/考虑扩充:开闭原则
{
public:
    virtual CDiffucuteGame * createDiffucuteGame()=0;
    virtual CEasyGame * createEasyGame()=0;
    CGameFactory();
    virtual ~CGameFactory();
};
CGameFactory::CGameFactory()
{
}
CGameFactory::~CGameFactory()
{
}

class CLocalDiffucuteGame : public CDiffucuteGame
{
public:
    void play();
    CLocalDiffucuteGame();
    virtual ~CLocalDiffucuteGame();
};
CLocalDiffucuteGame::CLocalDiffucuteGame()
{
}
CLocalDiffucuteGame::~CLocalDiffucuteGame()
{
}
void CLocalDiffucuteGame::play()
{
    cout<<"This is a Local Diffucute Game :"<<endl;
}

class CLocalEasyGame : public CEasyGame
{
public:
    void play();
    CLocalEasyGame();
    virtual ~CLocalEasyGame();
};
CLocalEasyGame::CLocalEasyGame()
{
}
CLocalEasyGame::~CLocalEasyGame()
{
}
void CLocalEasyGame::play()
{
    cout<<"This is a LocalEasy Game:"<<endl;
}

class CLocalGameFactory : public CGameFactory
{
public:
    CDiffucuteGame * createDiffucuteGame();
    CEasyGame * createEasyGame();
    CLocalGameFactory();
    virtual ~CLocalGameFactory();
};
CLocalGameFactory::CLocalGameFactory()
{
}
CLocalGameFactory::~CLocalGameFactory()
{
}
CEasyGame * CLocalGameFactory::createEasyGame()
{
    return new CLocalEasyGame;
}
CDiffucuteGame * CLocalGameFactory::createDiffucuteGame()
{
    return new CLocalDiffucuteGame;
}

class CNetDiffucuteGame : public CDiffucuteGame
{
public:
    void play();
    CNetDiffucuteGame();
    virtual ~CNetDiffucuteGame();
};
CNetDiffucuteGame::CNetDiffucuteGame()
{
}

CNetDiffucuteGame::~CNetDiffucuteGame()
{
}

void CNetDiffucuteGame::play()
{
    cout<<"This a Net Diffucute Game :"<<endl;
}

class CNetEasyGame : public CEasyGame
{
public:
    void play();
    CNetEasyGame();
    virtual ~CNetEasyGame();
};
CNetEasyGame::CNetEasyGame()
{
}

CNetEasyGame::~CNetEasyGame()
{
}

void CNetEasyGame::play()
{
    cout<<"This is a Net Easy Game!"<<endl;
}

class CNetGameFactory : public CGameFactory
{
public:
    CDiffucuteGame * createDiffucuteGame();
    CEasyGame * createEasyGame();
    CNetGameFactory();
    virtual ~CNetGameFactory();
};
CNetGameFactory::CNetGameFactory()
{
}
