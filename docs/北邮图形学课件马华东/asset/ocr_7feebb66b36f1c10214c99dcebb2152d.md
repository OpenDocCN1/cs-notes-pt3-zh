```
void main()
{
    glutInitDisplayMode(GLUT_SINGLE|GLUT_RGB);    //单缓存, RGB颜色模式
    glutCreateWindow("Simple"); //创建窗口,名为Simple
    glutDisplayFunc(RenderScene);    //设显示回调函数
    SetupRC();    //自定义的初始化例程
    glutMainLoop();    //让GLUT框架开始运行,处理交互事件
}
```