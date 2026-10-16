# Test

```
import java.text.DecimalFormat;
import javax.swing.JOptionPane;
public class Test {
    public static void main( String args[] )
    {
        Employee employee; // superclass reference
        String output = "";
        Boss boss = new Boss( "John", "Smith", 800.0 );
        CommissionWorker commissionWorker =
            new CommissionWorker(
            "Sue", "Jones", 400.0, 3.0, 150 );
        PieceWorker pieceWorker =
            new PieceWorker( "Bob", "Lewis", 2.5, 200 );
        HourlyWorker hourlyWorker =
            new HourlyWorker( "Karen", "Price", 13.75, 40 );
        DecimalFormat precision2 = new DecimalFormat( "0.00" );
        employee = boss;
```