# MouseMotionAdapter

```
super.addMouseMotionListener(new MouseMotionAdapter(){
    public void mouseDragged(MouseEvent e) { // 鼠标拖拽时调用
        System.out.println("鼠标拖拽到: X = " +
            e.getX() + ", Y = " + e.getY());
    }
});
```