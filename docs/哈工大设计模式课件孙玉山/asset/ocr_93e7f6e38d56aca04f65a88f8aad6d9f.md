# Design Example Using the State Pattern

```
public void passStateObjToContext(){
    if(state.equals(OVERDRAWNSTATE))
        stateObj = new OverDrawnState();
    else if (state.equals(NOFEESTATE))
        stateObj = new NoTransactionFeeState();
    else if (state.equals(FEESTATE))
        stateObj = new TransactionFeeState();
    context.setStateObj(stateObj);
}
public String getState(){
    return state;
}
public void setContext(BankContext context){
    this.context = context;
}
public abstract void deposit(double amount);
public abstract void withdraw(double amount);
public abstract boolean isOverDrawnLimitReached();
}
```