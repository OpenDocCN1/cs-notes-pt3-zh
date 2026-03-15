# 高性能计算课程：2.1：MPI消息与集合操作（第二部分）

在本节课中，我们将继续学习MPI（消息传递接口）的进阶概念。上一节我们介绍了MPI环境和点对点通信，本节我们将深入探讨非阻塞通信和笛卡尔通信器，并了解如何将它们结合使用来模拟更复杂的应用场景，例如海洋模拟。

## 非阻塞通信

上一节我们介绍了阻塞通信，其特点是进程在发送或接收操作完成前会一直等待。本节中我们来看看如何避免这种等待，以提高程序的效率。

![](img/ce9b698bbbb38a18fb353ecc10c0a794_1.png)

非阻塞通信允许进程在发起通信操作后，立即继续执行后续代码，而不必等待通信完成。这通过 `MPI_Isend`（非阻塞发送）和 `MPI_Irecv`（非阻塞接收）函数实现。通信完成后，需要使用 `MPI_Wait` 或 `MPI_Waitall` 等函数进行同步，以确保数据已成功发送或接收。

![](img/ce9b698bbbb38a18fb353ecc10c0a794_3.png)

以下是使用非阻塞通信的一个简单示例的核心代码逻辑：

```c
MPI_Request request;
MPI_Status status;

![](img/ce9b698bbbb38a18fb353ecc10c0a794_5.png)

if (my_rank == 0) {
    // 非阻塞发送
    MPI_Isend(send_buffer, buffer_size, MPI_CHAR, 1, 0, MPI_COMM_WORLD, &request);
    printf("进程0：我已开始发送，现在可以做其他事情。\n");
    // ... 执行其他计算 ...
    MPI_Wait(&request, &status); // 等待发送完成
    printf("进程0：消息已发送。\n");
} else if (my_rank == 1) {
    // 非阻塞接收
    MPI_Irecv(recv_buffer, buffer_size, MPI_CHAR, 0, 0, MPI_COMM_WORLD, &request);
    printf("进程1：我已开始接收，现在可以做其他事情。\n");
    // ... 执行其他计算 ...
    MPI_Wait(&request, &status); // 等待接收完成
    printf("进程1：收到消息，字符数：%d\n", recv_count);
}
```

在这个例子中，两个进程在通信的同时都打印了信息，展示了非阻塞操作如何允许计算与通信重叠。

![](img/ce9b698bbbb38a18fb353ecc10c0a794_7.png)

## 笛卡尔通信器

在实际的科学计算中，问题域（如一个海洋区域）通常具有网格结构。MPI提供了笛卡尔通信器，可以方便地为进程创建这种拓扑结构。

与默认的 `MPI_COMM_WORLD` 不同，笛卡尔通信器将进程排列成一个虚拟的网格。每个进程在网格中都有坐标，并且可以轻松地找到其“邻居”（如上、下、左、右的进程）。这对于模拟在网格上传播的现象（如波浪、鱼群）非常有用。

以下是创建和使用一个3x4二维笛卡尔通信器的关键步骤：

![](img/ce9b698bbbb38a18fb353ecc10c0a794_9.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_11.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_12.png)

```c
int dims[2] = {3, 4}; // 网格维度
int periods[2] = {1, 1}; // 周期边界条件（1为真，0为假）
MPI_Comm comm_2d;

![](img/ce9b698bbbb38a18fb353ecc10c0a794_14.png)

// 从 MPI_COMM_WORLD 创建笛卡尔通信器
MPI_Cart_create(MPI_COMM_WORLD, 2, dims, periods, 0, &comm_2d);

![](img/ce9b698bbbb38a18fb353ecc10c0a794_16.png)

int my_cart_rank, my_coords[2];
// 获取在新通信器中的排名和坐标
MPI_Comm_rank(comm_2d, &my_cart_rank);
MPI_Cart_coords(comm_2d, my_cart_rank, 2, my_coords);

![](img/ce9b698bbbb38a18fb353ecc10c0a794_18.png)

// 准备进行“向下”移位通信
int shift_direction = 0; // 0 表示第一个维度（行）
int displacement = 1;    // 位移为1
int source, dest;
// 获取源进程和目标进程的排名（不实际通信）
MPI_Cart_shift(comm_2d, shift_direction, displacement, &source, &dest);

![](img/ce9b698bbbb38a18fb353ecc10c0a794_20.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_22.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_23.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_25.png)

// 现在可以在 source 和 dest 之间进行实际的通信（例如 MPI_Sendrecv）
int send_data = my_cart_rank;
int recv_data;
MPI_Sendrecv(&send_data, 1, MPI_INT, dest, 0,
             &recv_data, 1, MPI_INT, source, 0,
             comm_2d, MPI_STATUS_IGNORE);
```

![](img/ce9b698bbbb38a18fb353ecc10c0a794_26.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_28.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_30.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_32.png)

**重要提示**：在笛卡尔通信器中进行的通信操作（如 `MPI_Sendrecv`），必须指定新创建的通信器（如 `comm_2d`），而不是 `MPI_COMM_WORLD`。同时，启动的进程数必须与笛卡尔网格定义的总进程数（本例中为3x4=12）完全匹配，否则创建会失败。

## 结合非阻塞与笛卡尔通信

将非阻塞通信与笛卡尔拓扑结合，是构建高效并行模拟应用（如海洋中鱼群运动模拟）的常见模式。其核心思想是：每个进程同时与其所有邻居交换信息，并在通信进行时处理本地计算。

以下是一个概念性的代码框架，展示了如何在网格中与四个邻居进行非阻塞通信：

![](img/ce9b698bbbb38a18fb353ecc10c0a794_34.png)

```c
MPI_Comm comm_2d; // 假设已创建的4x4笛卡尔通信器
int neighbors[4]; // 存储上、下、左、右邻居的排名
int my_data, data_from_neighbors[4];
MPI_Request send_reqs[4], recv_reqs[4];

![](img/ce9b698bbbb38a18fb353ecc10c0a794_36.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_38.png)

// ... 通过 MPI_Cart_shift 获取四个方向的邻居排名，存入 neighbors 数组 ...

![](img/ce9b698bbbb38a18fb353ecc10c0a794_40.png)

// 第一阶段：发起所有非阻塞发送和接收
for (int i = 0; i < 4; i++) {
    MPI_Isend(&my_data, 1, MPI_INT, neighbors[i], 0, comm_2d, &send_reqs[i]);
    MPI_Irecv(&data_from_neighbors[i], 1, MPI_INT, neighbors[i], 0, comm_2d, &recv_reqs[i]);
}

![](img/ce9b698bbbb38a18fb353ecc10c0a794_42.png)

// 在等待通信完成的同时，可以进行不依赖于邻居数据的本地计算
// ... 执行本地计算 ...

![](img/ce9b698bbbb38a18fb353ecc10c0a794_44.png)

// 第二阶段：等待所有通信完成
MPI_Waitall(4, send_reqs, MPI_STATUSES_IGNORE);
MPI_Waitall(4, recv_reqs, MPI_STATUSES_IGNORE);

// 现在所有邻居数据都已就绪，可以进行下一步计算
// ... 基于 data_from_neighbors 更新 my_data ...
```

![](img/ce9b698bbbb38a18fb353ecc10c0a794_46.png)

这种模式可以放入一个时间步循环中，在每个时间步内交换数据并更新状态，从而模拟动态过程。

![](img/ce9b698bbbb38a18fb353ecc10c0a794_48.png)

## 总结

![](img/ce9b698bbbb38a18fb353ecc10c0a794_50.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_51.png)

![](img/ce9b698bbbb38a18fb353ecc10c0a794_53.png)

本节课中我们一起学习了MPI的两个高级特性：非阻塞通信和笛卡尔通信器。非阻塞通信通过允许计算与通信重叠来提升程序效率。笛卡尔通信器则为具有网格结构的应用提供了天然的进程拓扑，简化了邻居查找和通信模式。最后，我们看到了如何将两者结合，为构建复杂的并行模拟应用（如海洋生态或流体动力学模拟）奠定了基础。理解这些概念是编写高效、可扩展并行程序的关键一步。