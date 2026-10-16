```
```java
class Controller implements ActionListener {
private CarAuctionGUI objCarGUI;
private CarModel cm;
private String carPrice;
public void actionPerformed(ActionEvent e){
String searchResult = null;
if (e.getActionCommand().equals(SEARCH)){
String selectedCar = objCarGUI.getSelectedCar();
cm.setSelectedCar(selectedCar); //更新模型数据
cm.setCarFileUrl();
cm.setupImageIcon();
cm.setSearchBtnClickInfo(true);
cm.notifyObservers(); //通知观察者
cm.setSearchBtnClickInfo(false);
}
if (e.getActionCommand().equals(CarAuctionGUI.BIT)){
carPrice = objCarGUI.getBitPrice();
cm.setBitPrice(carPrice); //更新模型数据
cm.setBitBtnClickInfo(true);
cm.notifyObservers(); //通知观察者
cm.setBitBtnClickInfo(false);
}
}
}
```
```