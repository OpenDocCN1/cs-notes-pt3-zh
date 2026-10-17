# Reading from a file into an Array

```
```cpp
// read MAX_ARRAY_SIZE int’s from a file, or until end
//   end of file

int nums[MAX_ARRAY_SIZE];
int cnt = 0;
int currentInput;
while((cnt < MAX_ARRAY_SIZE) && (fin >> currentInput)){
    nums[cnt] = currentInput;
    ++cnt;
}
```
```

![](bbox=[0.221, 0.52, 0.671, 0.862])