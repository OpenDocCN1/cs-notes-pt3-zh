```
// simple Date (control access)
class Date {
    int y,m,d;    // year, month, day
public:
    Date(int y, int m, int d); // constructor: check for valid date and initialize

    // access functions:
    void add_day(int n);    // increase the Date by n days
    int month() { return m; }
    int day() { return d; }
    int year() { return y; }
};

// ...
Date my_birthday(1950, 12, 30);    // ok
cout << my_birthday.month() << endl;    // we can read
my_birthday.m = 14;    // error: Date::m is private
```