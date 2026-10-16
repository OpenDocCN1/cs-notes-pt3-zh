```
d2 = sqr(b*(x+0.5)) +sqr(a*(y-1)) - sqr(a*b);
    while(y>0)
    { if (d2 <0) { d2 +=b*b*(2*x+2)+a*a*(-2*y+3);
            x++; y--; }
        else {d2 += a*a*(-2*y+3); y--; }
        putpixel(x,y,color); }
}
```

# 程序演示