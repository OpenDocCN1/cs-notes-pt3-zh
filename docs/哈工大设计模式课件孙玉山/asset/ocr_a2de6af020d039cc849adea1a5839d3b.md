# Example of design using strategy pattern

```
public class BarChartGraph extends JPanel implements ChartGraph{
    private Shape rectangle[];
    private double[] height;
    private int inputLen;

    public BarChartGraph(double[] height){
        this.height = height;
        setBackground(Color.pink);
        inputLen = height.length;
        rectangle = new Shape[inputLen];
    }
    public void paintComponent(Graphics g){
        super.paintComponent(g);
        以下代码绘制条形图
    }
}
```