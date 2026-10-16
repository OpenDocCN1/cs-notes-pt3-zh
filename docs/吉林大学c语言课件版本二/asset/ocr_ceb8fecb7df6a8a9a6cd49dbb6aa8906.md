```
/* 复数乘法 */
complex_type complex_mul ( complex_type x,
                           complex_type y ) {
    complex_type product ;
    product.real_part = x.real_part * y.real_part
                     + x.imaginary_part * y.imaginaty_part ;
    product.imaginary_part = x.real_part * y.imaginary_part
                     + x.imaginaty_part * y.real_part ;
    return  product ;
}
```