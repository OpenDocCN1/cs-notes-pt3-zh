```
int main()
try {  // predefine names:
    define_name("pi",3.1415926535);
    define_name("e",2.7182818284);
    calculate();
    keep_window_open();  // cope with Windows console mode
    return 0;
}
catch (exception& e) {
    cerr << e.what() << endl;
    keep_window_open("~~");
    return 1;
}
catch (...) {
    cerr << "exception \n";
    keep_window_open("~~");
    return 2;
}
```