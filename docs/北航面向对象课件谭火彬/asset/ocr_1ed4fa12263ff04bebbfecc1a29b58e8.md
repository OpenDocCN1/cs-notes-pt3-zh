# 开始设计： 正方形

```
public class Rectangle {
    private int width;
    private int height;
    public void setWidth(int w) {
        width = w;
    }
    public int getWidth() {
        return width;
    }
    public void setHeight
        height = h;
    }
    public int getHeight()
        return height;
    }
}
```

```
public class Square
extends Rectangle {
    public void setWidth(int w){
        super.setWidth(w);
        super.setHeight(w);
    }
    public void setHeight(int h) {
        super.setWidth(h);
        super.setHeight(h);
    }
}
```

![](bbox=[0.05, 0.28, 0.25, 0.75])