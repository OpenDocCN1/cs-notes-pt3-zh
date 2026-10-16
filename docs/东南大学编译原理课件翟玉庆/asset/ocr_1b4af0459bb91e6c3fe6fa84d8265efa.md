# Algorithm

```
Set ip to point to the first symbol of w$;
While (1) {
    if ($ is on top of the stack an ip points to $) /*success*/
        return;
    else {
        let a be the topmost terminal symbol on the stack;
        let b be the symbol pointed to by ip;
        if (a⋖b || a≐b) /*Shift*/
        {
            push b onto the stack;
            advance ip to the next input symbol;
        }
    }
```