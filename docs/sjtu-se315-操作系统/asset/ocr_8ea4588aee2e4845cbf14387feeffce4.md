# Library Operating System

Most programs to be linked with *libraries* instead of communicating with the exokernel directly

The libraries hide low-level resources

An applications can choose the library which best suits its needs, or even build its own

The kernel only ensures that the requested resource is free, and the application is allowed to access it.

Allow programmer to implement custom abstractions, omit unnecessary ones, most commonly to improve performance