```
void main(void) {
    printf("please input xa,ya,xb,yb,
    xc,yc,xd,yd:\n");
    scanf("%of%of%of%of%of%of %of%of ",&xa,&ya,
    &xb,&yb,&xc,&yc,&xd,&yd);

    s1 = areauvw (xa, ya, xb, yb, xd, yd );
    s2 = areauvw (xb, yb, xc, yc, xd, yd );

    ss=s1+s2;
    ss=ss/1000;    // 折合成亩
    m=ss*950;    // 计算总产量
    printf("m=%10.3f\\n",m); // 打印输出
}
```