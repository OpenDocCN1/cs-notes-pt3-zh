# BorderLayout布局管理器

+   - Window、Dialog和Frame的缺省布局管理器

+   - BorderLayout布局方式提供了更复杂的布局控制方法，它包括5个区域：North, South, East, West和Center，其方位依据上北下南左右西右东。当容器的尺寸发生变化时，各组件的相对位置不变，但中间部分组件的尺寸会发生变化，南北组件的高度不变，东西组件的宽度不变。

+   - BorderLayout类有二种构造方法：

+   - public BorderLayout()
+     各组件间的水平和垂直间距为缺省值0个像素。

+   - public BorderLayout(int horizontalGap, int verticalGap)
+     各组件间的水平和垂直间距为指定值。