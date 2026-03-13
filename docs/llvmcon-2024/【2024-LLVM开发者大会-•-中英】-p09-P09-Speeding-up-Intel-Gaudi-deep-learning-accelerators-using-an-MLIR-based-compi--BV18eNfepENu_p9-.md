# 【2024-LLVM开发者大会-•-中英】-p09-P09-Speeding-up-Intel-Gaudi-deep-learning-accelerators-using-an-MLIR-based-compi--BV18eNfepENu_p9-

![](img/c060bf1b397abcae9f8988b9877dfecb_0.png)

Good afternoon。 today I be presenting an MLR based compiler。

That is being used in production to compile workloads on Intel Gaudy accelerators。

This is work done by many engineers， including the ones listed here。

So Intel Gaudi is a third generation air accelerator for inference and training。

And it provides up to around two petflps of matrix multiplication computation。

And it has inbuilt high bandwidth memories and inbuilt ethernet controllers for scale art。あ。

The compute acceleration primarily comes from these two engines。

 we have a matrix multiplication engine that is a systolic 2 by 256 by 256 systolic， right？

And we have eight of these on the chip。And we also have 64 tensor processing core。

 Each core is a VLIW processor with support for 256 byte wide single computations。

And to enable workloads to run on this accelerator， we provide a suite of software compilers。

 libraries and frameworks。We have support for popular deep learning frameworks like Pytoch。

And we also have some proprietary graph compilers， and in this talk I'll be talking about the Fuser。

 which is used to program the PPCs。This picture shows the high level compilation flow in Gaudi and it shows where the fuser gets invoked and the components it interacts with。

So on the left， you see a Pytoch code that is getting traced and it will be converted into a data flow graph。

Which is then handed off to the graph compiler。The graph compiler does a bunch of optimizations。

And while it knows how to deal with metrics multiplications and how to configure the MMmeEs。

It doesn't really bother generating code for the TPCs。

 these TPCs are programmable and to keep an open operator set。

 it hands it off for other compilers to reason about these operations。

So we get a subgraph of operations from the graph compiler and the fuser then fuses these things and creates LLVM IR。

 and this IR is then handed off to a LLVM backend which generates the final fused kernel。

This is then given back to the graph compiler。And for operations that the userr cannot handle or cases and cases where the user has written their own custom kernel。

These are provided by the performance library and they get picked up from there。

The graphraph compiler then schedules all of this work on the chip and they all run nicely。

So now I'll get a bit deeper into the fuser compilation flow。And like I said。

 the graph compiler gives us an input IR which is not an MLIR format。

 and so the first step we do is an importer that creates ML MLIR IR that looks something like what you see on the top right。

It's not visible， but just to give you an idea of the scale of things。

 typically we have like thousands of operations in this computation here。

And this is represented using a custom dialect that we call the TPC kernel dialect。

 and it's designed mostly to interoperate with other components in the system。

So if we don't handle something， this can fall back to a different performance library or another compiler。

We then go through a series of clustering passes and these passes group these ops into clusters。

Each cluster will typically end up running as a single kernel。

 and they're roughly around like tens of ops in these clusters。And after clustering。

 we then lower this into another custom dialect that we call the S dialect。

And the S dialect is basically primitive operations， it has some element wise operations。

 broadcasts and reductions。More complex operations like normalization， softms。

 they all get broken down into these primtive ops。We then do a series of high level optimizations that are easy to do at this level。

 given that the data flow is very apparent。And then we are ready for our fusion。

The fusion pass takes these multidimensional operations and values of tensors。

And it breaks them up into scalar operations that work with scalar values。

And these operations are nested in loop like structures。And with these values。

 we can then pass them around in registers and avoid memory reads and write。Now。

 as we do this incremental fusion， we have different choices in how we fuse and op with its predecessor or successor。

And instead of just doing a greedy fusion， we create or enumerate a list of possibilities。

And we scored them using a cost model。One interesting learning we had during the development of this optimization was that we needed to pay attention to the beam diversity here as we prune these options。

If we only go for the lowest cost， then we tend to get stuck in local minima。

 so we had to put in some optimizations or considerations into the cost model for diversity of the Ps。

So after fusion， we get this loop like IR that you can see on the left。

 it is mostly consisting of upstream dialects here， like they are fine dialects。

 the memory of dialects， are written than math。We can do further loop fusion if needed。

 and then we do more optimizations on these loops。And we end up with paralyzed and vectorized IR that can run on these 64 tensor processing cores。

We then do a bunch more backend optimizations and finally generate the optimized LLVMIR。

Which is then handed off to the LLBM backend to generate the final boundary。

For the loop optimizations， we leverage a lot of upstream and fine optimizations。

 so you can see that there we use the loop fusion algorithms in a fine dialect。

We use the super vectorizer for vectorization， and we also use a lot of the polyhedral utilities to reason about loops and discover parallel loops。

And that's what helps us paralyze and distribute these。Computations over the different TPcs。

We have upstream enhancements wherever feasible to these different parts of the malar dialects。

And in addition to generating code， we also use MLIR to extract metadata。

And provide that to the graph compiler。One important piece of information we are able to extract is if you think of a point in the iteration space of the kernel。

The graph compiler wants to know what part of the tensor or what region of the tensor is this kernel going to access when it's trying to execute this iteration。

And this comes to us through a fine analysis and we hand it off to the graph compiler。

Graph compiler does some very interesting optimizations here with this where it first slices the kernel。

And it can schedule a slice of execution on the TPC。

And this slice can then write all its outputs to local cache or SRA。

And its consumer on a different engine， like a matrix multiplication engine can start right away as soon as this slice is done。

Meanwhile， the graph compiler can schedule the next slice of execution on the TPCs so we get very nice MMmeE and TPC overlap。

On this。We also get to use these high bandwidth caches and asras and some flash attention like schedules that are very efficient。

And this slide shows the overall performance improvements we get by using Fuser。

 the graph on the left is showing different pytoch workloads that are shown on the X axis。

And Y axis shows the speed up we get by running the fuser。

And you can see that we get up to 50% speed ups， on an average， we get about 30% speed up on Gudy2。

On the right， I'm showing the performance improvement just focusing on the accelerator execution。

 so we collect a whole bunch of traces from these models， run them with them without the fusor。

And on average， we see about a 50% speed up。So to conclude。

 I've presented an MLlayar based fuser that is deployed as part of the Gaudi stack。

 it delivers significant performance improvements and works in tandem with a graph compiler to optimize execution or the entire accelerator。

We have leveraged upstream dialects like a fine SEFth and math along with in house dialects。

 and we would like to thank the MLR community for all the great work that made this compiler possible。

Thank you。研究上ね。