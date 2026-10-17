# # 用test函数测试二维图形 （例6.4）

```
void test(TwoDimensionalShape & t){
t.show();
cout<<"面积为"<<t.getArea()<<endl;
}
```

```
// 主函数
void main(){
Square s(10);
Circle c(10);
test(s);
test(c);
}
```

![](bbox=[0.277, 0.764, 0.438, 0.951])

![](bbox=[0.471, 0.447, 0.973, 0.753])

如果二维图形又派生出了椭圆形，用于测试的test函数需要需改吗？这有何意义？