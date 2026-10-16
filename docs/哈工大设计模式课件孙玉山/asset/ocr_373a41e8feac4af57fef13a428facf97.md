# Example of Mediator Pattern

```
public class HotelGUI extends JFrame {
    public HotelGUI (BusinessMediator bMdtr) {
        bMdtr.registerAirlineGUI(this);
    }
    class ButtonListener implements ActionListener {
        public void actionPerformed(ActionEvent ae) {

            if (ae.getActionCommand().equals(SUBMIT)) {
                setCusName();
                String cusInfo = getCusName();
                bMediator.updateAllGuis(AIR, cusInfo);
            }
        }
    }
}
```

Source code for the mediator class