# Example of design using strategy pattern

```
public class PieChartGraph extends JPanel implements ChartGraph{
    private double[] slices;
    private Shape arcs[];
    private double total = 0.0D;
    private int inputLen;
    final static double X = 100.0D;
    final static double Y = 20.0D;
    final static double W = 100.0D;
    final static double H = 100.0D;

    public PieChartGraph(double[] slices){
        this.slices = slices;
        inputLen = slices.length;
        arcs = new Shape[inputLen];
        setBackground(Color.pink);
    }
    public void paintComponent(Graphics g){
        //饼形图代码
    }
}
```