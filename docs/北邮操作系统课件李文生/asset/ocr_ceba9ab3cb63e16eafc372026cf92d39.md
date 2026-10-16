# Several Instances of a Resource Type

# Several time-varying data structures used

+   - **Available**: A vector of length *m* indicates the number of available resources of each type.
+   - **Allocation**: An *n* × *m* matrix defines the number of resources of each type currently allocated to each process.
+   - **Request**: An *n* × *m* matrix indicates the current request of each process. If *Request* [*i,j*] = *k*, then process *P_i* is requesting *k* more instances of resource type *R_j*.

Rows in *Allocation* and *Request* can be treated as vectors, and referred to as *Allocation_i* and *Request_i* respectively