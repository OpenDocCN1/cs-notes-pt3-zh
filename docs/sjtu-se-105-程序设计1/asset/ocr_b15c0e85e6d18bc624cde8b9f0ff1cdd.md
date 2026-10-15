# 跳过“垃圾”

```
```cpp
void skip_to_int()
{
    if (cin.fail()) {          // we found something that wasn’t an integer
        cin.clear();            // we’d like to look at the characters
        char ch;
        while (cin>>ch) {       // throw away non-digits
            if (isdigit(ch)) {
                cin.unget();    // put the digit back,
                                // so that we can read the number
                return;
            }
        }
    }
    error("no input");         // eof or bad: give up
}
```
```