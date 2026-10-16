# TestMediator

```
BusinessMediator mediator = new BusinessMediator();
new HotelGUI(mediator);
new AirlineGUI(mediator);
new TourGUI(mediator);
```

# AirlineGUI

-mdtr TourMediator

+   AirlineGUI(mediator)
+   getCusName()
+   getCusID()
+   getCusNation()
+   addCustomer(String cus)
+   +checkIn()
+   +checkSafety()
+   +displayInfoToScreen(text);

# HotelGUI

-mdtr TourMediator

+   HotelGUI(mediator)
+   getCusName()
+   getCusID()
+   getCusNation()
+   addCustomer(String cus)
+   +reserveRoom()
+   +checkIn()
+   +checkOut()
+   +displayInfoToScreen();

# BusinessMediator

hotelGui: HotelGUI;
airlineGui: AirlineGUI;
tourGui: TourGUI

+   +registerHotelGUI(HotelGUI hg)
+   +registerAirlineGUI(AirlineGUI ag)
+   +registerTourGUI(TourGUI tg)
+   +addAllCandidateCus(HOTEL,cusInfo)
+   +updateAllGuis(String text)

# TourGUI

-mdtr TourMediator

+   TourGUI(mediator);
+   getCusName()
+   getCusID()
+   getCusNation()
+   addCustomer(String cus)
+   +findHotel()
+   +checkIn()
+   +checkOut()
+   displayInfoToScreen();

Typical Interactions