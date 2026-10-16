# FlowLayout

FlowLayout属于流式布局管理器，使用此种布局方式，所有的组件会像流水一样依次进行排列， FlowLayout类的常用方法及常量如下。

| No. | 方法及常量 | 类型 | 描述 |
|-----|------------|------|------|
| 1 | public static final int CENTER | 常量 | 居中对齐 |
| 2 | public static final int LEADING | 常量 | 与容器的开始端对齐方式一样 |
| 3 | public static final int LEFT | 常量 | 左对齐 |
| 4 | public static final int RIGHT | 常量 | 右对齐 |
| 5 | public static final int TRAILING | 常量 | 与容器的结束端对齐方式一样 |
| 6 | public FlowLayout() | 构造 | 构造一个新的 FlowLayout，居中对齐，默认的水平和垂直间距是 5 个单位 |
| 7 | public FlowLayout(int align) | 构造 | 构造一个 FlowLayout，并指定对齐方式 |
| 8 | public FlowLayout(int align,int hgap,int vgap) | 构造 | 指定对齐方式、水平、垂直间距 |