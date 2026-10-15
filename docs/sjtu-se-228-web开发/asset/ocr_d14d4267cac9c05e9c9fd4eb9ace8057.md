# Inheritance strategy

+   - Single table per class hierarchy strategy

```
Airbus airbus = new Airbus();
airbus.setManufacturer("Airbus");
airbus.setType("320");
airbus.setCapacity("320");
session.save(airbus);
```

```
Boeing boeing = new Boeing();
boeing.setManufacturer("Boeing");
boeing.setType("777");
boeing.setComfort("Great");
session.save(boeing);
```

```
Plane plane = new Plane();
plane.setManufacturer("Il");
plane.setType("78");
session.save(plane);
```