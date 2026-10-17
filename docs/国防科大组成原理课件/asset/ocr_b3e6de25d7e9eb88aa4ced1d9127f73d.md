# 积分求π的并行程序

# JIAJIA

# MPI

```
jia_init(argc,argv);
pi=jia_alloc(8);

h = 1.0/N;
for(i=jiapid+1;i<=N;i+=jiahosts)
    { mypi = ... }
jia_lock(1);
    pi += mypi;
jia_unlock(1);
printf pi;
jia_exit();
```

```
MPI_Init(argc,argv);
MPI_Comm_size();
MPI_Comm_rand();
h = 1.0/N;
for(i=myid+1;i<=N;i+=numprocs)
    { mypi = ... }
MPI_Reduce(mypi,pi,1 ... );
printf pi;
MPI_Finalize();
```