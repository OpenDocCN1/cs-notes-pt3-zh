# Subtyping

# Subtyping in principle

+   - A <: B if every A object can be used without type error whenever a B object is required

+   - Example:

```
Point:
  int getX();
  void move(int);
```

Public members

```
ColorPoint:
  int getX();
  int getColor();
  void move(int);
  void darken(int tint);
```

Public members

# C++: A <: B if class A has public base class B

+   - This is weaker than necessary Why?