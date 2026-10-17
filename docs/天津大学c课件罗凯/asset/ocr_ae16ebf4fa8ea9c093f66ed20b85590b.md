# So what does this look like?

```
```cpp
#ifndef TIME_H
#define TIME_H

class Time {
public:
    Time( );
    Time(int hr, int mn );

    bool equals( Time tm );
    bool lessThan( Time tm );
    void print();
    void setHour(int hr);
    void setMin(int mn);

private:
    int hour, min;
};

#endif
```
```

![](bbox=[0.77, 0.669, 0.977, 0.792])