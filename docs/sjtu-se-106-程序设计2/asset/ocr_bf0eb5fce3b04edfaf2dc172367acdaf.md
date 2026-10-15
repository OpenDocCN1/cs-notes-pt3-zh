# An Example of Smart Pointers

```
template <class T> class auto_ptr
{
    T* ptr;
public:
    explicit auto_ptr(T* p = 0) : ptr(p) {}
    ~auto_ptr()             {delete ptr;}
    T& operator*()          {return *ptr;}
    T* operator->()         {return ptr;}
};
```