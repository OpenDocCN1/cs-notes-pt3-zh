# 设计Point类

```
class Point {
    private Object x;                // 表示x坐标
    private Object y;                // 表示y坐标
    public void setX(Object x) {
        this.x = x;
    }
    public void setY(Object y) {
        this.y = y;
    }
    public Object getX() {
        return this.x;
    }
    public Object getY() {
        return this.y;
    }
};
```