```
```cpp
if ((!maze[g][h]) && (!mark[g][h])) { //new position
    mark[g][h]=1;
    temp.x=i; temp.y=j; temp.dir=d+1;
    stack.Push(temp);
    i=g ; j=h ; d=N;  // move to (g, h)
}
else d++;  // try next direction
}
}
cout << “No path in maze.” << endl;
}
```
```