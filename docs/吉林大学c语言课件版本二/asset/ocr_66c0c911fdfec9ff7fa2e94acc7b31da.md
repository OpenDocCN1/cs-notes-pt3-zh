```
/* 复数加法 */
complex_type complex_add(complex_type x,
    complex_type y){
    complex_type add;
    add.real_part=x.real_part+y.real_part;
    add.imaginary_part=x.imaginary_part+y.imaginary_part;
    return add;
}
```