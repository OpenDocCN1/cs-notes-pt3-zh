# New version of the class definition

```
class Time {
public:
    Time(int hr, int mn) {
        setHour(hr);
        setMin(mn);
    }

    void print() {
        cout << hour << ":" << min;
    }

    void setHour(int hr) {
        ......
    } // end of setHour

private:
    int hour, min;
};
```

> What do you notice that is different about the Time function?