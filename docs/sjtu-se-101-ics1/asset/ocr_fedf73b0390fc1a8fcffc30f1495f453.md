```
```c
/*dynamically load the shared library that contains addvec() */
handle = dlopen("./libvector.so", RTLD_LAZY);
if (!handle) {
        fprintf(stderr, "%s\n", dlerror());
        exit();
}

/*get a pointer to the addvec() function we just loaded */
addvec = dlsym(handle, "addvec");
if ( (error = dlerror()) != NULL ) {
        fprintf(stderr, "%s\n", error);
        exit(1);
}
```
```