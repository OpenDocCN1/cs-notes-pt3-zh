```
void main(void) {
    ab=sqrt( (xa-xb)* (xa-xb)+(ya-yb)* (ya-yb) ); //边ab长
    bd=sqrt( (xb-xd)* (xb-xd)+(yb-yd)* (yb-yd) ); //边bd长
    ad=sqrt( (xa-xd)* (xa-xd)+(ya-yd)* (ya-yd) ); //边ad长
    s=(ab+bd+ad)/2; //s
    s1=sqrt( s*(s-ab)*(s-bd)*(s-ad) );

    bc=sqrt( (xb-xc)* (xb-xc)+(yb-yc)* (yb-yc) ); //边BC长
    cd=sqrt( (xc-xd)* (xc-xd)+(yc-yd)* (yc-yd) ); //边CD长
    s=(bc+bd+cd)/2; //边BD长bd前边已经计算
    s2=sqrt( s*(s-bc)*(s-bd)*(s-cd) );
    ss=s1+s2; // 总面积S=S1+S2
    ss=ss/1000; // 折合成亩
    m=ss*950; // 计算总产量
    printf("m=%10.3f\n",m); // 打印输出
}
```