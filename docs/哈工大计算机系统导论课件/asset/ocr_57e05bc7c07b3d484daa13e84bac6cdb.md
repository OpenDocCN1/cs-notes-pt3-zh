# # 测试样例的性能

```
```c
void combine1(vec_ptr v, data_t *dest)
{
	long int i;
	*dest = IDENT;
	for (i = 0; i < vec_length(v); i++) {
		data_t val;
		get_vec_element(v, i, &val);
		*dest = *dest OP val;
	}
}
```
```

计算向量元素的和或积

| 方法 | Integer | Double FP |
|------|---------|-----------|
| 操作 OP | + | * | + | * |
| Combine1 未优化 | 22.68 | 20.02 | 19.98 | 20.18 |
| Combine1 -O1 | 10.12 | 10.12 | 10.17 | 11.14 |