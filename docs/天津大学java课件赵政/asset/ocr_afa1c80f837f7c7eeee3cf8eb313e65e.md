# 例 P121　public 和 private 对访问的作用

```
/* This program demonstrates the difference between
public and private.
*/
class Test {
    int a;                 // default access
    public int b;          // public access
    private int c;         // private access
    // methods to access c
    void setc(int i) {     // set c's value
        c = i;
    }
    int getc() {           // get c's value
        return c;
    }
}
```

![](bbox=[0.612, 0.2, 1.0, 1.0])