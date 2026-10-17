# First a little review

```
```cpp
#ifndef TIME_H
#define TIME_H

class Time {
public:
    Time();
    Time(int hr, int mn);

    bool equals(Time tm);
    ......
    void setHour(int hr);

    void setMin(int mn);

private:
    int hour, min;
};
#endif
```
```

+   - What are we doing with time.h

![](bbox=[0.77, 0.769, 0.976, 0.891])