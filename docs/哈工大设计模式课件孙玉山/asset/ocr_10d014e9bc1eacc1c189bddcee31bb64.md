# 3. Observer Pattern

```
Observable watched = new Subject();
Observer watcher = new ConcreteObserver1();
watched.register(watcher);
```

Diagram for general Observer pattern (no central dispatcher module)