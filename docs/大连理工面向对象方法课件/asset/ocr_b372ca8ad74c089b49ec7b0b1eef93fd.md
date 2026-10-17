```
void play();
CNetDifficuteGame();
virtual ~CNetDifficuteGame();
};
CNetDifficuteGame::CNetDifficuteGame()
{
}

CNetDifficuteGame::~CNetDifficuteGame()
{
}

void CNetDifficuteGame::play()
{
    cout<<"This a Net Difficute Game :"<<endl;
}
```

```
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
```

```
class CNetGameFactory : public CGameFactory
{
public:
    CDifficuteGame * createDifficuteGame();
    CEasyGame * createEasyGame();
    CNetGameFactory();
    virtual ~CNetGameFactory();
};
CNetGameFactory::CNetGameFactory()
```