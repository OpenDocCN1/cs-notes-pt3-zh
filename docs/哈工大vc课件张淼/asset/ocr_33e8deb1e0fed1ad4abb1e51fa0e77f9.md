# Interface.cpp

```
// Implementation of class Interface--client receives this file only
// as precompiled object code, keeping the implementation hidden.
#include "Interface.h" // Interface class definition
#include "Implementation.h" // Implementation class definition

// constructor
Interface::Interface( int v )
: ptr ( new Implementation( v ) ) // initialize ptr to point to
{
    // a new Implementation object
    // empty body
} // end Interface constructor
```