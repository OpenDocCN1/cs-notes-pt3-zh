# # Resource Acquisition (2)

```
typedef int semaphore;
semaphore resource_1;
semaphore resource_2;
void process_A(void) {
    down(&resource_1);
    down(&resource_2);
    use_both_resources();
    up(&resource_2);
    up(&resource_1);
}
void process_B(void) {
    down(&resource_1);
    down(&resource_2);
    use_both_resources();
    up(&resource_2);
    up(&resource_1);
}
```

Figure 6-2. (a) Deadlock-free code.