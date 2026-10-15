# Trees and Class Hierarchies

+   - For the most part, classes in object-oriented languages such as C++ and Java are structured as a tree.
+   - One of the defining characteristics of the object-oriented paradigm is that classes form *hierarchies*. Any class can be designated as a *subclass* of some other class, which is called its *superclass*. As noted on this week’s section handout, most class hierarchies are tree-structured even though C++ permits more complicated structures.
+   - A class represents a *specialization* of its superclass. If you create an object that is an instance of a class, that object is also an instance of all other classes in the hierarchy above it in the superclass chain.
+   - When you define a new class in C++, that class automatically *inherits* the behavior of its superclass.