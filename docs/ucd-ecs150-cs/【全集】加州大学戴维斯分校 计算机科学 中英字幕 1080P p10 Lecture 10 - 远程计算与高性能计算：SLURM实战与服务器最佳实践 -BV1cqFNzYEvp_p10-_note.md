# 高性能计算入门：第10讲：SLURM实战与服务器最佳实践 🚀

![](img/64aaedb754dc141d0d95feb35c40495c_0.png)

在本节课中，我们将学习如何在高性能计算（HPC）集群上实际运行计算任务。我们将从理解并行计算的基本概念开始，然后学习如何使用SLURM作业调度系统来提交和管理作业，包括交互式作业、批处理作业以及并行作业。

## 概述：并行计算与HPC集群

在开始之前，我们需要明确一些核心概念。到目前为止，您所进行的大多数计算可能都是**顺序计算**，即代码一行接一行地执行。然而，HPC的强大之处在于**并行计算**，即多个计算步骤可以同时运行。

并行计算主要有两种模式：
*   **多线程**：一个程序启动多个线程，这些线程共享同一块内存空间。这通常在一台计算机（一个节点）内进行。
*   **分布式计算**：多个独立的进程运行在不同的计算机（节点）上，它们通过文件或网络协议进行通信。这是更复杂但能处理更大规模问题的并行方式。

HPC集群由许多通过高速网络连接的计算机组成，每台计算机称为一个**节点**。我们登录的节点称为**头节点**，而实际执行计算任务的节点称为**计算节点**。为了公平、高效地管理所有用户对计算资源的使用，我们使用**作业调度器**。在本课程中，我们将使用名为**SLURM**的作业调度器。

## 1. 探索集群资源与SLURM基础

在提交作业之前，我们先了解一下如何查看集群的可用资源。

### 查看分区与账户信息

![](img/64aaedb754dc141d0d95feb35c40495c_2.png)

SLURM将计算资源组织成不同的**分区**，您可以将其理解为不同的任务队列。使用以下命令查看所有可用分区：

```bash
sinfo --summarize
```

该命令会显示分区的名称（如 `high`、`low`）、状态、时间限制和节点信息。

要查看您的账户具体可以访问哪些分区，请使用：

```bash
sacctmgr show associations user=$USER
```

### 查看作业状态

![](img/64aaedb754dc141d0d95feb35c40495c_4.png)

您可以使用 `squeue` 命令查看当前正在运行或排队的作业。添加 `--me` 参数可以只查看您自己的作业。

![](img/64aaedb754dc141d0d95feb35c40495c_6.png)

```bash
squeue --me
```

![](img/64aaedb754dc141d0d95feb35c40495c_8.png)

![](img/64aaedb754dc141d0d95feb35c40495c_10.png)

![](img/64aaedb754dc141d0d95feb35c40495c_12.png)

`squeue` 的输出包含了作业ID、分区、状态（`R`表示运行中，`PD`表示排队中）、运行时间、使用的节点和CPU数量等信息。

![](img/64aaedb754dc141d0d95feb35c40495c_14.png)

![](img/64aaedb754dc141d0d95feb35c40495c_16.png)

![](img/64aaedb754dc141d0d95feb35c40495c_18.png)

## 2. 运行交互式作业

交互式作业允许您像在头节点上一样，直接登录到一个计算节点并运行命令，非常适合调试和探索性工作。

### 提交交互式作业

使用 `srun` 命令并指定所需资源来启动一个交互式作业。以下是关键参数：
*   `--time`：请求的运行时间（例如 `20` 表示20分钟）。
*   `--partition`：指定分区（例如 `low`）。
*   `--mem`：请求的内存（例如 `1G` 表示1GB）。
*   `--job-name`：为作业命名（不能包含空格）。
*   `--pty`：指定启动一个伪终端，并运行一个shell（如 `/bin/bash`）。

![](img/64aaedb754dc141d0d95feb35c40495c_20.png)

![](img/64aaedb754dc141d0d95feb35c40495c_21.png)

运行以下命令示例：

![](img/64aaedb754dc141d0d95feb35c40495c_23.png)

![](img/64aaedb754dc141d0d95feb35c40495c_25.png)

```bash
srun --time=20 --partition=low --mem=1G --job-name=my_first_job --pty /bin/bash -l
```

命令执行后，如果资源可用，您的终端提示符会从 `@login` 变为 `@hivecXXX`（某个计算节点）。现在您可以在这个计算节点上运行任何命令了。

### 结束交互式作业

要结束交互式会话并返回头节点，只需输入 `exit`。

在交互式作业内部，您可以通过环境变量 `$SLURM_JOB_ID` 获取当前作业的ID。

## 3. 运行非交互式（批处理）作业

![](img/64aaedb754dc141d0d95feb35c40495c_27.png)

![](img/64aaedb754dc141d0d95feb35c40495c_29.png)

对于需要长时间运行且无需人工干预的任务，我们使用非交互式作业。我们将创建一个包含SLURM指令和实际运行命令的**批处理脚本**，然后提交它。

### 创建批处理脚本

使用文本编辑器（如 `nano`）创建一个脚本文件，例如 `hello.sh`：

```bash
#!/bin/bash
#SBATCH --time=20
#SBATCH --partition=high
#SBATCH --mem=1G
#SBATCH --job-name=myjob
#SBATCH --mail-user=your-email@ucdavis.edu
#SBATCH --mail-type=ALL
#SBATCH --output=myjob_%j.out

srun hostname
```

**脚本解析：**
1.  `#!/bin/bash`：指定脚本由Bash shell执行。
2.  `#SBATCH` 开头的行：这些是给SLURM的指令，定义了作业的资源需求和其他设置。
    *   `--output`：指定标准输出日志的文件名，`%j` 会被替换为作业ID。
    *   `--mail-*`：设置作业完成或失败时接收邮件通知。
3.  `srun hostname`：这是作业要执行的实际命令。使用 `srun` 来运行命令可以让SLURM更好地记录和管理作业步骤。

### 提交与监控批处理作业

使用 `sbatch` 命令提交脚本：

```bash
sbatch hello.sh
```

![](img/64aaedb754dc141d0d95feb35c40495c_31.png)

![](img/64aaedb754dc141d0d95feb35c40495c_32.png)

![](img/64aaedb754dc141d0d95feb35c40495c_33.png)

![](img/64aaedb754dc141d0d95feb35c40495c_35.png)

![](img/64aaedb754dc141d0d95feb35c40495c_36.png)

提交后，您会看到类似 `Submitted batch job 1234567` 的信息。您可以使用 `squeue --me` 查看作业状态。

![](img/64aaedb754dc141d0d95feb35c40495c_38.png)

![](img/64aaedb754dc141d0d95feb35c40495c_40.png)

![](img/64aaedb754dc141d0d95feb35c40495c_42.png)

![](img/64aaedb754dc141d0d95feb35c40495c_44.png)

![](img/64aaedb754dc141d0d95feb35c40495c_46.png)

作业完成后，输出日志会保存在您指定的文件（如 `myjob_1234567.out`）中。如果作业出错或您想提前终止它，可以使用 `scancel` 命令：

```bash
scancel 1234567
```

### 在作业中使用软件环境（如Pixi）

如果您的任务需要特定的软件环境（例如通过Pixi管理），只需在 `srun` 命令前加上 `pixi run` 即可。例如，要运行一个Python脚本：

```bash
#!/bin/bash
#SBATCH ...
srun pixi run python my_script.py
```

## 4. 运行并行作业

上一节我们介绍了如何运行单个任务，本节中我们来看看如何利用SLURM运行并行任务。SLURM主要支持两种并行模式：**并行步骤**和**数组作业**。

### 并行步骤

这种方法适用于需要同时运行多个**不同**命令或步骤的场景。我们在一个批处理脚本中编写多个 `srun` 命令，并让它们同时启动。

![](img/64aaedb754dc141d0d95feb35c40495c_48.png)

以下是关键技巧：
1.  在每个 `srun` 命令末尾添加 `&` 符号，表示不等待该命令结束就继续执行脚本。
2.  使用 `wait` 命令确保所有后台任务完成后，脚本才结束。
3.  通过 `#SBATCH --nodes` 指定需要的节点总数，并在每个 `srun` 命令中用 `--nodes=1` 指定该步骤需要的节点数。

**示例脚本 `parallel_steps.sh`：**

![](img/64aaedb754dc141d0d95feb35c40495c_50.png)

```bash
#!/bin/bash
#SBATCH --time=10
#SBATCH --partition=high
#SBATCH --mem=1G
#SBATCH --job-name=parallel_demo
#SBATCH --nodes=2

srun --nodes=1 hostname &
srun --nodes=1 hostname &

wait
```

提交此脚本后，两个 `hostname` 命令会并行执行，可能在不同的计算节点上。

### 数组作业

数组作业非常适合**令人尴尬的并行**问题，即需要将**相同**的任务运行很多次，且每次运行之间不需要通信。例如，用不同的参数处理100个数据文件。

您只需编写处理**单个任务**的脚本，SLURM会自动为您创建多个副本（一个数组）来运行。

**关键参数：**
*   `#SBATCH --array`：定义数组索引范围，例如 `1-3` 会创建3个独立的作业任务。

**示例脚本 `array_job.sh`：**

```bash
#!/bin/bash
#SBATCH --time=10
#SBATCH --partition=high
#SBATCH --mem=1G
#SBATCH --job-name=array_demo
#SBATCH --array=1-3

srun echo "Hello from array job $SLURM_ARRAY_TASK_ID"
```

**脚本解析：**
*   `$SLURM_ARRAY_TASK_ID` 是一个环境变量，在每个数组任务中会自动被赋予不同的值（1，2或3）。
*   提交后，SLURM会生成3个独立的作业任务，每个任务输出不同的信息。
*   输出日志文件也会被分开，通常命名为 `slurm-作业ID_数组任务ID.out`。

您可以在您的任务脚本（Python、R等）中利用 `$SLURM_ARRAY_TASK_ID` 来读取不同的输入文件或设置不同的参数。

**在Python中获取任务ID示例：**

```python
#!/usr/bin/env python3
import sys
job_id = int(sys.argv[1]) # 从命令行参数获取
print(f"This is array task {job_id}")
```

![](img/64aaedb754dc141d0d95feb35c40495c_52.png)

![](img/64aaedb754dc141d0d95feb35c40495c_54.png)

对应的批处理脚本中这样调用：

```bash
srun python my_script.py $SLURM_ARRAY_TASK_ID
```

## 总结

本节课中我们一起学习了在高性能计算集群上使用SLURM进行计算的完整流程。我们从并行计算的概念和HPC集群架构讲起，然后逐步深入：

1.  学会了使用 `sinfo`、`squeue` 等命令查看集群资源和作业状态。
2.  掌握了通过 `srun` 启动**交互式作业**进行调试和探索。
3.  掌握了通过编写包含 `#SBATCH` 指令的脚本，并使用 `sbatch` 提交**非交互式批处理作业**。
4.  最后，我们探索了两种实现并行的强大工具：**并行步骤**用于运行多个不同任务，**数组作业**用于高效运行大量相同任务。

![](img/64aaedb754dc141d0d95feb35c40495c_56.png)

请记住，在共享的HPC环境中，合理请求资源（不超额请求）并及时取消不需要的作业是一种良好的实践。现在，您可以开始将您的计算任务部署到HPC集群上，充分利用其强大的并行计算能力了！