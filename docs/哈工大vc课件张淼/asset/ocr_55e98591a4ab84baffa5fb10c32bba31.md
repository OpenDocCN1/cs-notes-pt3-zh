```
#include <math.h>
#include <iostream.h>
class Point
{public: //外部接口
    Point(int xx=0, int yy=0)
    {X=xx;Y=yy;}
    int GetX() {return X;}
    int GetY() {return Y;}
private: //私有数据成员
    int X,Y;
};
```