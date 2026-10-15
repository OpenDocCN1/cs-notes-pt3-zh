# Basic Code – Single Threaded

```
GetEvents(date) {
  List events = EventMap.find(date).copy();
  return events;
}
```

```
AddEvent(data, newEvent) {
  EventMap.find(date) += newEvent;
}
```