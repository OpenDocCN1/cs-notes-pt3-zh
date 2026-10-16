# 观察者模式

```
Observable
- changed : boolean = false
- obs : Vector
+ Observable ()
+ addObserver (Observer o) : void
+ deleteObserver (Observer o) : void
+ notifyObservers () : void
+ notifyObservers (Object arg) : void
+ deleteObservers () : void
+ setChanged () : void
+ clearChanged () : void
+ hasChanged () : boolean
+ countObservers () : int
```

```
Observer
+ update (Observable o, Object arg) : void
```

```
ConcreteObservable
```

```
ConcreteObserver
+ update (Observable o, Object arg) : void
```

obs