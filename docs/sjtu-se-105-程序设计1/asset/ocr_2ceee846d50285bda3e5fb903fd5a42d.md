# Poly.Java

```
package PolyJava;

public class Poly {
    public static void main(String[] args) {
        try{
            IntSet s = new MaxIntSet();
            s.insert(3);
            System.out.printf(new Boolean(s.query(3)).toString());
        }catch(Exception e){
            e.printStackTrace();
        }
    }
}
```