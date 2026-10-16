```
if(ClipTest(dx, XR − x1, &u1, &u2))
    if(ClipTest(− dy, y1 − YB, &u1, &u2))
        if(clipTest(dy, YT − y1, &u1, &u2)){
            if(u2 < 1.0){
                x2 = x1 + u2*dx; y2 = y1 + u2*dy;
            }
            if(u1 > 0.0){
                x1= x1 + u1*dx; y1 = y1 + u1*dy;
            }
            displayline(x1, y1, x2, y2)
            return;
        }
    }
```