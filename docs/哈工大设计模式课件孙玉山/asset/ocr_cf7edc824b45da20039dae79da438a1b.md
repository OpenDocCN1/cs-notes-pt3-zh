# Design Example Using the State Pattern

```
private static void createAndShowGUI(){
    JFrame f = new JFrame("State Pattern-Traffic Light");
    TrafficLightGUI tf = new TrafficLightGUI();
    f.getContentPane().add(tf);
    f.setVisible(true);
}
public static void main(String args[]) {
    Runnable doCreateAndShowGUI = new Runnable() {
        public void run() {
            createAndShowGUI();
        }
    };
    SwingUtilities.invokeLater(doCreateAndShowGUI);
}
```