# GridLayout布局管理器

+   - GridLayout类有三种构造方法：
+   - public GridLayout()
+     在一行中放置所有的组件，各组件间的水平间距为0像素。
+   - public GridLayout(int rows, int cols)
+     生成一个rows行，cols列的管理器，最多能放置 rows*cols 个组件。（课本有误）。
+     rows或cols可以有一个为0。若rows为0，这表示每行放置cols个组件，根据具体组件数，可以有任意多行；若cols为0，这表示共有rows行，根据具体组件数，每行可以放置任意多个组件。
+     组件间的水平和竖直间距为0像素。
+   - public GridLayout(int rows, int cols, int horizontalGap, int verticalGap )
+     各组件间的水平和竖直间距为指定值。