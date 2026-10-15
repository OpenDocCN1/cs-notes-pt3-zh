
## Sample derived class

```
class ColorPt: public Pt {
    public:
        ColorPt(int xv,int cv);
        ColorPt(Pt* pv,int cv);
        ColorPt(ColorPt* cp);
        int getColor();
        virtual void move(int dx);
        virtual void darken(int tint);
    protected:
        void setColor(int cv);
    private:
        int color;
};
```

Public base class gives supertype
Overloaded constructor
Non-virtual function
Virtual functions
Protected write access
Private member data

## Run-time representation

Point object

Point vtable

Code for move

vptr
x
3

ColorPoint object

ColorPoint vtable

Code for move

vptr
x
5
c
blue

Code for darken

Data at same offset

Function pointers at same offset

![](img/af430dff16b82a0fe61ce7dee05dcf9c_41_0.png)

## Compare to Smalltalk

Point object
Point class
Template
Method dictionary
ColorPoint object
ColorPoint class
Template
Method dictionary

## Why is C++ lookup simpler?

- Smalltalk has no static type system
  - Code p message:pars could refer to any object
  - Need to find method using pointer from object
  - Different classes will put methods at different place in method dictionary

- C++ type gives compiler some superclass
  - Offset of data, fctn ptr same in subclass and superclass
  - Offset of data and function ptr known at compile time
  - Code p->move(x) compiles to equivalent of (* (p->vptr[1]))(p,x) if move is first function in vtable

data passed to member function; see next slides

## Looking up methods, part 2

Point object

Point vtable

Code for move

vptr
x
3

ColorPoint object

ColorPoint vtable

Code for move

vptr
x
5
c
blue

darken()

Code for darken

```
Point cp = new ColorPt(5,blue);
cp->move(2);    // (* (cp->vptr[0]))(cp,2)
```

## Calls to virtual functions

- One member function may call another

```
class A {
    public:
        virtual int f(int x);
        virtual int g(int y);
};
int A::f(int x) { ... g(i) ...;}
int A::g(int y) { ... f(j) ...;}
```

- How does body of f call the right g?

- If g is redefined in derived class B, then inherited f must call B::g

## "This" pointer (analogous to self in Smalltalk)

- Code is compiled so that member function takes "object itself" as first argument

```
Code      int A::f(int x) { ... g(i) ...;}
compiled as  int A::f(A *this, int x) { ... this->g(i) ...;}
```

- "this" pointer may be used in member function

- Can be used to return pointer to object itself, pass pointer to object itself to another function, ...

## Non-virtual functions

- How is code for non-virtual function found?
- Same way as ordinary “non-member” functions:
  - Compiler generates function code and assigns address
  - Address of code is placed in symbol table
  - At call site, address is taken from symbol table and placed in compiled code
  - *But* some special scoping rules for classes
- Overloading
  - Remember: overloading is resolved at compile time
  - This is different from run-time lookup of virtual function

## Scope rules in C++

- **Scope qualifiers**
  - binary `::` operator, `->`, and `.`
  - `class::member`, `ptr->member`, `object.member`
- **A name outside a function or class,**
  - not prefixed by unary `::` and not qualified refers to global object, function, enumerator or type.
- **A name after `X::`, `ptr->` or `obj.`**
  - where we assume ptr is pointer to class X and obj is an object of class X
  - refers to a member of class X or a base class of X

## Virtual vs Overloaded Functions

```
class parent { public:
    void printclass() {printf("p ");};
    virtual void printvirtual() {printf("p ");};  };
class child : public parent { public:
    void printclass() {printf("c ");};
    virtual void printvirtual() {printf("c ");};  };
main() {
    parent p; child c; parent *q;
    p.printclass(); p.printvirtual(); c.printclass(); c.printvirtual();
    q = &p; q->printclass(); q->printvirtual();
    q = &c; q->printclass(); q->printvirtual();
}
```

Output: p p c c p p ? ?
