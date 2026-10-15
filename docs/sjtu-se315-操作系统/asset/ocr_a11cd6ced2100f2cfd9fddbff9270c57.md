# The abort protocol

An exokernel must also be able to take resources from library operating systems that fail to respond satisfactorily to revocation requests

If a library OS fails to respond quickly, the secure bindings need to be broken “by force”

An exokernel simply breaks all secure bindings to the resource and informs the library operating system