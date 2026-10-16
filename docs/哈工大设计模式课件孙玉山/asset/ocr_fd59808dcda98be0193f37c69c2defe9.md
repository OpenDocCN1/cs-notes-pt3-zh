# Example of design using strategy pattern

```
class ButtonListener implements ActionListener {
    public void actionPerformed(ActionEvent ae) {
        if (ae.getActionCommand().equals(SORT)) {
            if (type.equals(BUBBLE))
                sa = new BubbleSort();
            if (type.equals(HEAP))
                sa = new HeapSort();
            if (type.equals(INSERT))
                sa = new InsertSort();
            if (type.equals(QUICK))
                sa = new QuickSort();

            context = new Context(sa);
            intArray = context.sortIntArray(intArray);
            long eTime = context.getExeTime();
        }
    }
}
```

+   1. 用户创建策略子类对象 sa
+   2. 将sa作为创建Context类的对象的参数传递给 Context
+   3. 在用户类中使用Context对象调用 sortIntArray(intArray) getExeTime()方法