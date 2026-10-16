```
public class CarModel implements Observable{
private ArrayList<Observer> observersList;
private ImageIcon imgIcon;
private URL url;
private String[] carNameList;
private String carSelected;
private String bitPrice;
private boolean isBitBtnClicked = false;
private boolean isSearchBtnClicked = false;
static final String CARFILES = "CarFiles/";
static final String CARIMAGES = "CarImages/";

public CarModel(){
observersList = new ArrayList<Observer>();
carNameList=new String[200];
}
public void setCarList(String[] cars){
carNameList = cars;
}
public String[] getCarList(){
return  carNameList;
}
```