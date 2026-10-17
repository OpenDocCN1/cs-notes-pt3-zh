# 8.6.2 Several Instances of a Resource Type

一个资源类型的多个实例

+   - **Available:** A vector of length *m* indicates the number of available resources of each type.
+   
+     可用：一个长度*m*的向量代表每一种资源类型有效的数目
+   
+   - **Allocation:** An *n* × *m* matrix defines the number of resources of each type currently allocated to each process.
+   
+     分配：一个 *n* × *m* 的矩阵定义了当前分配的每一种资源类型的实例数目
+   
+   - **Request:** An *n* × *m* matrix indicates the current request of each process. If *Request* [*i*,*j*] = *k*, then process *Pᵢ* is requesting *k* more instances of resource type *Rⱼ*.
+   
+     请求：一个 *n* × *m* 的矩阵使命了当前的进程请求。如果 *Request* [*i*,*j*] = *k*，那么进程 *Pᵢ* 请求 *k* 个资源 *Rⱼ* 的实例

![](bbox=[0.867, 0.855, 0.998, 0.997])