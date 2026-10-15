```
bool Book::borrow_book(){
    if(!borrowed)
        borrowed= true;
    else
        error("you can not borrow a borrowed book!");
    return borrowed;
};
```

```
bool Book::return_book(){
    if(borrowed)
        borrowed= false;
    else
        error("you can not return a returned book!");
    return borrowed;
};
```