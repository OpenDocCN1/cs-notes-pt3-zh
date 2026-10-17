

## Using an instance

```cpp
int main() {
    Time t, t2;
    // t.hour = 12;
    t.setHour(12);
    t.setMin(67);
    t.print();
    t2.print();
    cout << "\n\n";
    return 0;
}
```

```cpp
class Time {
public:
    void setHour(int hr) {
        hour = 0;
        if (hr >= 0 && hr <= 23)
            hour = hr;
    } // end of setHour
private:
    int hour, min;
};
```

## Using an instance

```cpp
int main() {
    Time t, t2;

    // t.hour = 12;   // hour is private
    t.setHour(12);    // set the hour of t
    t.setMin(67);
    t.print();          // use the print function of t

    t2.print();         // this is still a problem !!!
    cout << "\n\n";
    return 0;
}
```

## New version of the class definition

```cpp
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

## New version of the class definition

```cpp
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

- 1. Same name as the class
- 2. No return type

## Where do you think the Time function is being called (used)

```cpp
int main() {
    Time t(12, 30), t2(-1, 78);

    t.print();
    cout << endl;
    t2.print();

    cout << endl << endl;
    return 0;
}
```

## Where do you think the Time function is being called (used)

```cpp
int main() {
    Time t(12, 30), t2(-1, 78);

    t.print();
    cout << endl;
    t2.print();

    cout << endl << endl;
    return 0;
}
```

## Using the constructor

```cpp
int main() {
    Time t(12, 30);
    Time t2(-1, 78);
    t.print();
    cout << endl;
    t2.print();

    cout << endl << endl;
    return 0;
}
```

```cpp
Time(int hr, int mn) {
    setHour(hr);
    setMin(mn);
}
```

```cpp
void setHour(int hr) {
    hour = 0;
    if (hr >= 0 && hr <= 23) {
        hour = hr;
    }
} // end of setHour
```

## Constructor Functions

- Special features of Constructor Function:
  - (understand and **memorize**)
  - same names as the class
  - no return type

## Constructor Functions

- **Special features of Constructor Function:** (understand and *memorize*)
  - same names as the class
  - no return type
  - called when a instance is created
  - every class has one… *if the programmer doesn’t create one* then one is given by the compiler

## Using the constructor function

```cpp
int main() {
    Time t(12, 30), t2(-1, 78);
    Time t3;

    t.print();
    cout << endl;
    t2.print();

    cout << endl << endl;
    return 0;
}
```

```cpp
// in Time class
Time(int hr, int mn) {
    setHour(hr);
    setMin(mn);
}
```

> **NOTE:** variable t3 would have used the “free” constructor, but since we created a constructor, we no longer get the free one

## Old Example of Creating and Using an instance

```cpp
int main() {
    Time t, t2;

    t.hour = 12;
    t.min = 30;
    t.print();

    t2.print();
    cout << "\n\n";
    return 0;
}
```

## Old Example of Creating and Using an instance

```cpp
int main() {
    Time t, t2;              // uses the “free” constructor

    t.hour = 12;
    t.min = 30;
    t.print();

    t2.print();
    cout << "\n\n";
    return 0;
}
```

