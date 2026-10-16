# 【Proposition】

An optimal schedule exists if min { b<sub>i</sub>, a<sub>j</sub> } ≥ min { b<sub>j</sub>, a<sub>i</sub> } for any pair of adjacent jobs J<sub>i</sub> and J<sub>j</sub>. All the schedules with this property have the same completion time.

# Algorithm

```
{
    Sort { a<sub>1</sub>, ..., a<sub>N</sub>, b<sub>1</sub>, ..., b<sub>N</sub> } into non-decreasing sequence ;
    m = minimum element ;
    do {
        if ( ( m == a<sub>i</sub> ) && ( J<sub>i</sub> is not in the schedule ) )
            Place J<sub>i</sub> at the left-most empty position ;
        else if ( ( m == b<sub>i</sub> ) && ( J<sub>i</sub> is not in the schedule ) )
            Place J<sub>i</sub> at the right-most empty position ;
        m = next minimum element ;
    } while ( m );
}
```

T = O( N log N )

# 【Example】

Given N = 4, J = [
3 4 8 10
6 2 9 15
]

Sorting ⇒ { b<sub>2</sub> a<sub>1</sub> a<sub>2</sub> b<sub>1</sub> a<sub>3</sub> b<sub>3</sub> a<sub>4</sub> b<sub>4</sub> }

T<sub>1342</sub> = 38

![](bbox=[0.684, 0.747, 0.934, 0.801])

![](bbox=[0.664, 0.851, 0.964, 0.901])