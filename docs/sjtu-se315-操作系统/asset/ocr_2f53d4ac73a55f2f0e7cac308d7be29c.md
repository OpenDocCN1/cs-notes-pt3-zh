# Recap: How to do with reader – write locks?

```
GetEvents(date) {
  readerStart(maRWLock);
  List events = EventMap.find(date).copy();
  readerFinish(mapRWLock);
  return events;
}
AddEvent(data, newEvent) {
  writerStart(maRWLock);
  EventMap.find(date) += newEvent;
  writerFinish(mapRWLock);
}
```