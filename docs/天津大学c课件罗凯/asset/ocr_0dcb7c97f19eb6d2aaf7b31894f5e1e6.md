# # Revisiting the Swap Function

# ## swap function using reference parameters

```
```cpp
void swap(char & ch1, char & ch2) {
    char ch = ch1;
    ch1 = ch2;
    ch2 = ch;
}
```
```

```
```cpp
int main() {
    char a = 'y';
    char b = 'n';
    swap(a, b);
    cout << a << b << endl;
    return 0;
}
```
```