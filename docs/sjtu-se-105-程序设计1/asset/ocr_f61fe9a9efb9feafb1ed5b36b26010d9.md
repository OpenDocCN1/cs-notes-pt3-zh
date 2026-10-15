```
//
Date d(2004, Date::jan, 7);        // a variable
const Date d2(2004, Date::feb, 28); // a constant
d2 = d;        // error: d2 is const
d2.add(1);     // error d2 is const
d = d2;        // fine
d.add(1);      // fine

d2.f(); // should work if and only if f() doesn't modify d2
// how do we achieve that? (say that's what we want, of course)
```