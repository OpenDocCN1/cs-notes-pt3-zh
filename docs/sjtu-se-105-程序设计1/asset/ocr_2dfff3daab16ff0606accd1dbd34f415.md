```
// simple Date (some people prefer implementation details last)
class Date {
public:
    Date(int y, int m, int d); // constructor: check for valid date and initialize
    void add_day(int n);       // increase the Date by n days
    int month();
    // ...
private:
    int y,m,d;                 // year, month, day
};

Date::Date(int yy, int mm, int dd)    // definition; note :: "member of"
    :y(yy), m(mm), d(dd) { /* ... */ };  // note: member initializers

void Date::add_day(int n) { /* ... */ };  // definition
```

![](bbox=[0.68, 0.38, 0.99, 0.68])