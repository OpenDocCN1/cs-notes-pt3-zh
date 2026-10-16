# CarAuctionGUI

Main()
getSelectedCar(): String
getBitPrice(): String
getCarList(): String[]
setUpComboBox(String[] carList): void

```
cm = new CarModel();
cgiv = new CarGUIInfoView(cm);
cbiv = new CarBitInfoView(cm);
cm.register(cgiv);
cm.register(cbiv);
```

# <<interface>>
Observable

+register(Observer obs): void
+notifyObservers(): void

# CarModel

cgiv
cbiv

+setCarList(String[] cars): void
+getCarList(): String[]
+setSelectedCar(String sCar): void
+getSelectedCar(): String
+setBitPrice(String bPrice): void
+getBitPrice(): String
+setCarFileURL(): void
+getCarFileURL(): URL
+setupImageIcon(): void
+getImageIcon(): ImageIcon
+register(Observer obs): void
+notifyObservers(): void

# Controller

objCarGUI:CarAuctionGUI
cm: CarModel
carPrice: String

actionPerformed(ActionEvent e)

# <<interface>>
Observer

update(Observable subject): void

# CarGUIInfoView

cm(CarModel对象)
+update(): void

# CarBitInfoView

cm(CarModel对象)
+update(): void

链接

链接

链接

链接

二手车拍卖系统的典型交互