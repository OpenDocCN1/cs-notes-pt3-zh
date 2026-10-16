```
```text
while (!q.IsEmpty()) {
    v = q.Front();
    q.Pop();
    for (all vertices w adjacent to v)  // actual code uses an
                                         // iterator
        if (!visited[w]) {
            q.Push(w);
            visited[w] = true;
        }
    }   // end of while
delete [] visited;
}
```
```