# Another look at promptAndReadInt()

```
```cpp
// promptAndReadInt(): prompt and read next integer
int promptAndReadInt() {
    cout << "Enter a whole number:";
    char ch;
    cin >> ch;
    while( isdigit( ch ) == false ) // cctype lib
        cin >> ch;
    cin.putback( ch );
    int response;
    cin >> response;

    return response;
}
```
```