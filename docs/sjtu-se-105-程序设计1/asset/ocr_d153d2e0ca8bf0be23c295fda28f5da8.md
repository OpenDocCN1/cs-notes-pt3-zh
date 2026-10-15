![](bbox=[0.22, 0.18, 0.85, 0.55])

```
fstream fs(name.c_str());    // open for input and output
// ...
fs.seekg(5);    // move reading position ('g' for 'get') to 5 (the 6th character)
char ch;
fs>>ch;    // read and increment reading position
cout << "character[6] is " << ch << '(' << int(ch) << ")\n";
fs.seekp(1);    // move writing position ('p' for 'put') to 1 (the 2nd character)
fs<<'y';    // write and increment writing position
```