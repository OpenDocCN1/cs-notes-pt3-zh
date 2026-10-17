```
//求m 和 n 的最大公约数
public static int gongyue(int m, int n) {
    while(m % n != 0) {
        int temp = m % n;
        m = n;
        n = temp;
    }
    return n;
}
//求m 和 n 的最小公倍数
public static int gongbei(int m, int n) {
    return m * n / gongyue(m, n);
}
```