# # 任务级并行性

+   - 将不同的任务（进程或者线程）分布到不同的处理单元上执行，可分为进程级或者线程级并行性

+   - 常见于商业应用领域（如大规模数据库的事务处理）、多道程序工作负载（Multiprogramming workload）等

```
```if(processor_ID="a") {
	task A;
} else if (processor_ID="b"){
	Task B;
}
```
```

例子：任务并行的代码示意图