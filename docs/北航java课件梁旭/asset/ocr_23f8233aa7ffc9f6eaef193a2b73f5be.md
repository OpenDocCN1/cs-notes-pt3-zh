# 常用容器类(Container)

+   - 1、窗口（Frame）
+   - 在Java中，生成一个窗口通常是用Window的子类Frame来进行实例化，不直接用Window类。
+   - 生成的窗口，如果不添加响应代码，不能响应用户的操作，如“关闭窗口”等。
+   - 例:
+     - public class li81 extends Frame{
+     - public static void main(String args[]){
+     - li81 fr=new li81("This is a contianer");//窗口名
+     - }}