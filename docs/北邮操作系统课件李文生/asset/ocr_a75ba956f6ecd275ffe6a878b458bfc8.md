# Data Structures for the Banker’s Algorithm

*n* = number of processes
*m* = number of resources types

+   - **Available:** Vector of length *m*. If available [*j*] = *k*, there are *k* instances of resource type *R_j* available.

+   - **Max:** *n* × *m* matrix. If *Max* [*i,j*] = *k*, then process *P_i* may request at most *k* instances of resource type *R_j*.

+   - **Allocation:** *n* × *m* matrix. If Allocation[*i,j*] = *k* then *P_i* is currently allocated *k* instances of *R_j*.

+   - **Need:** *n* × *m* matrix. If *Need*[*i,j*] = *k*, then *P_i* may need *k* more instances of *R_j* to complete its task.

*Need* [*i,j*] = *Max*[*i,j*] − *Allocation* [*i,j*]