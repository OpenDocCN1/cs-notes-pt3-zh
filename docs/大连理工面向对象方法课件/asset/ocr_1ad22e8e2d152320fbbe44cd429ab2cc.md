```
```cpp
}

void Time::printStandard()
{
    cout << ((hour == 0 || hour == 12) ? 12 : hour % 12)
         << ":" << (minute < 10 ? "0" : "") << minute
         << ":" << (second < 10 ? "0" : "") << second
         << " " << (hour < 12 ? "AM" : "PM");
}
```
```

```
```cpp
//FIG2_5.CPP
#include <iostream>
#include "time1.h"
main()
{
    Time t;
    cout << "The initial military time is ";
    t.printMilitary();
    cout << "\nThe initial Standard time is ";
    t.printStandard();
    t.setTime(13,27,6);
    cout << "\n\nMilitary time after set Time is ";
    t.printMilitary();
    cout << "\nStandard time after set Time is ";
    t.printStandard();
    t.setTime(99,99,99);
    cout << "\n\nAfter attempting invalid settings:\n"
         << "Military time: ";
    t.printMilitary();
    cout << "\nStandard time: ";
    t.printStandard();
    cout << endl;
    return 0;
}
```
```

# 输出结果：

The initial military time is 00: 00: 00
The initial standard time is 12: 00: 00AM