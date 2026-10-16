```
```cpp
while (ai != poly.end() && bi != b.poly.end()) { //not null
    if (ai->exp == bi->exp) {
        int sum = ai->coef + bi->coef;
        if (sum) c.poly.InsertBack(temp.Set(sum, bi->exp));
        ai++; bi++; // to next term
    }
    else if (ai->exp < bi->exp) {
        c.poly.InsertBack(temp.Set(bi->coef, bi->exp));
        bi++; // next term of b
    }
    else {
        c.poly.InsertBack(temp.Set(ai->coef, ai->exp));
        ai++; // next term of a
    }
}
```
```