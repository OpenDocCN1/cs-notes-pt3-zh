# Unstated Rules in JOS

A spawned program should have open only file descriptors 0, 1, and 2.
User pointers should be run through TRUP before used by the kernel