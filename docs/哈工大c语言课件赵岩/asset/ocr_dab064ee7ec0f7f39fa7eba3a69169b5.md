# 错误方式1

```
void Swap(int *p1, int *p2) {
	int *p;
	p = p1; /*p1,p2为内部变量*/
	p1 = p2;
	p2 = p;
}
```