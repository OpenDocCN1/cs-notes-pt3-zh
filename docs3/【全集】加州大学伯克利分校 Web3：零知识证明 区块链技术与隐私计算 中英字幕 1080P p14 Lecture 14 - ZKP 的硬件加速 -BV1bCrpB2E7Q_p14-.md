# 【全集】加州大学伯克利分校 Web3：零知识证明 区块链技术与隐私计算 中英字幕 1080P p14 Lecture 14 - ZKP 的硬件加速 -BV1bCrpB2E7Q_p14-

![](img/562634cb8ef1921784ac743c2a586325_0.png)

Hello everyone and welcome back to the course on Ze knowledgeledge proofs。

My name is Kelly Olen and I work at Supernational where we focus on hardware acceleration of cryptography in today's lecture we'll be discussing hardware acceleration of zero knowledge proofs。

 what does it mean， what's the current state of the industry and where is it heading in the future？

We'll begin today's lecture by discussing what is hardware acceleration and why is it important for zero knowledge proof generation。

After this， we'll move on to discuss some of the computationally expensive operations involved in proof generation operations such as multi scalar multiplication。

 number threeoretic transformation and arithmetic hashing。

We'll also include a brief discussion on the required hardware resources that are needed to perform these computations。

We'll then follow this up with a discussion on some of the limitations of hardware acceleration。

 and finally we'll conclude with a summary of the status of ZKP acceleration today。

 as well as a brief discussion of promising future directions for improving proof generation performance in the future。

To kick off today's topic， it's important to start with a quick overview of what we mean when we say hardware acceleration。

Hardware acceleration is the use of dedicated hardware to accelerate an operation so that it runs faster or more efficiently。

Hardware acceleration can involve optimizing functions and code to use existing hardware。

 which is often referred to as COTs hardware， which stands for commercial off the shelf。

Or it may involve the development of new hardware designed for a specific task。

Examples of COtTS hardware include CPUUs， GPUs， or graphics processors。

 and FPGAs or field programmable gateator arrays。Custom hardware is often referred to as an AsI or an application specific integrated circuit。

While both software optimization and hardware acceleration involve the design and implementation of efficient algorithms。

 hardware acceleration is unique in that it targets those algorithms at specific compute platforms or specific hardware resources。

The use of custom hardware to accelerate computationally expensive tasks has a well established history。

Prior to the advent of modern processors， many of the original computing systems actually had a separate copro for performing floating point operations。

However， some more modern co processors or hardware acceleration units that you may be familiar with include DSPs for processing audio and video。

 GPUs for gaming and video transcoding。TPUs for machine learning training and inference。

And NIC or NPUs for network can packet processing。While many of these mentioned hardware acceleration units have made their way into modern day cell phones and computers。

 perhaps more relevant to this audience is the use of hardware acceleration targeted at cryptographic operations。

On this slide， we'll take a deeper dive into some of the cryptographic primitives that have been hardware accelerated in the past。

Two of the most commonly accelerated cryptographic derivatives are those used for hashing in encryption。

Today， many modern Dame processors have custom areas of the silicon that are dedicated for both hashing and encryption operations。

These accelerators are leveraged through the use of hardware accelerated software libraries。

 which invoke specific cryptographic instructions such as Shaw andI for hashing and AESNI for encryptncion。

Through the introduction of these and other instructions。

 capabilities like disk encryption and secure web connections have become ubiquitous。Furthermore。

These capabilities occur with almost zero overhead or utilization of the processor due to the custom hardware accelerators。

As we move from client devices like mobile phones， laptops， and desktops to servers。

 we begin to see the need to handle even more cryptographic operations。As a simple example。

 a server may need to initiate thousands of TLS connections per second。

 orders of magnitude more than client devices。As a result， we've seen the design of custom silicon。

 as well as expansion cards and co processors to handle these operations。

While these accelerators have been around for many years and often operate behind the scenes。

 one of the largest and most well known cryptographic accelerators are Bitcoin mining machines。

Bitcoin mining rigs are focused on performing a very specific operation， a double Sha 256 hash。

 with a goal of providing throughput at the lowest cost possible。For the past several years。

 billions of dollars of Bitcoin mining rigs have been sold each year。

While hashing and Public key cryptography has been a longstanding target for acceleration。

 in recent years there's been a tremendous amount of focus on new cryptographic primatives that are beginning to come into the realm of practicality。

These include techniques such as fully homomorphic encryption， verifiable delay functions。

 as well as today's topic， which is zero knowledge proofs。

So why do we need to accelerate zero knowledge proofs？

The key reason is the high overhead of proof generation。

While proof verification is important and will increasingly become a focus as ZKPs are deployed at scale。

 the computations of generating the proof are currently the bottleneck to enabling novel and more complex use cases。

One estimate by Justin Thaller， one of the instructors of this course。

Is that ZK proof generation can be 1 million to 10 million or more times as expensive as performing the computation natively。

To put this in more concrete terms， let's take a look at two emerging use cases， ZK EVMs。

 which are designed to help improve the scalability of Ethereum and ZKVMs。

 which are designed to enable verifiable computation for a broader set of use cases。

On the ZKEVM side， a presentation earlier in this course series by Yy Zang。

 but the time to generate a proof for 1 million gas worth of Ethereum transactions at approximately 40 minutes on the CPU。

In comparison， the polygon blockchain runs at around 10 million gas per second using native computation。

This puts an estimated overhead of the proof generation at 25，000 or more。Similarly。

 ZKVMs like Rik Ze's risk5 based ZKVM is estimated to run at approximately 50 kilohertz。

In comparison to a modern day CPU which can run at 5 gigahertz or more。

 this implies an overhead of 100，000 or more。These examples are not meant to suggest a performance issue with either of these designs or projects。

 but merely to show the overhead that comes with proof generation。So with that background in mind。

 it's important to discuss the many potential goals of hardware acceleration。

Each which may require a different design or different hardware platform。

One of the most common goals of hardware acceleration is throughput。

 that is to perform as many operations per unit of time as possible。

A second possible goal for hardware acceleration is cost。When optimizing for cost。

 the goal is to reduce the capital and operational expenses associated with performing certain operations。

In the case of Bitcoin mining machines， this means maximizing the amount of hashes per dollar of purchase price。

 while minimizing the energy consumption and therefore operational costs of performing each hash。

Finally， a third goal for hardware acceleration is latency。

This is reducing the time to complete an individual operation。

Latency is an important consideration in domains such as high frequency trading and verifiable delay functions。

In the case of proof generation， low latency proof generation may facilitate better user experience or faster finality for use cases such as ZK bridges。

With that background out of the way， let's talk specifically about what core operations need to be accelerated to improve the performance of proof generation。

The first thing to note is that each proof system and its associated implementation is built leveraging different cryptographic primitives and different software libraries。

 what may be the most computationally expensive part of one proof system may be relatively minor or may not appear at all in a different proof system。

 implementation or use case。With that said， across a variety of different proof systems。

 there are three computationally expensive operations which are seen repeatedly。

Multi scar multiplication， number theoretic transformation， and arithbetic hashes。

In the coming slides， we'll discuss each of these in more detail。

 describing what they are and how they are commonly implemented。

The first primitive we willll tackle is multi scalar multiplication or MSM。

MSMSM is an algorithm for calculating the sum of multiple scalar multiplications。Alternatively。

 it can be thought of as a dot product of elliptic curve points and scrs。

One thing to note is that due to the nature of the problem， it is very easily parallelizable。

Each scalar multiplication or set of scalar multiplications can be split up and operated on by different hardware engines and then brought together and accumulated at the end。

There are a number of optimizations that can be applied to reduce the amount of computation in computing and MSM。

For a larger sized MSM， algorithms like Pipengers reduce the computational cost from linear in the amount of bases in scalrs to roughly ON over log n。

In addition to using improved algorithms。😡，There are also alternative point and sometimes curve representations that can be used to reduce the total number of field operations per curve operation。

Highly parallelizable operations like MSM are ripe for hardware acceleration。

By moving them off of a host device like a CPU onto a more parallel architecture like a GPU。However。

 one thing that must be kept in mind when moving operations off of a host device onto a peripheral is that data must also be moved to be computed on。

In the case of multiscalealar multiplication， the scalar。

 and sometimes the points as well must be moved off of the host and onto the accelerator。

The available communication bandwidth between these two devices will often limit the maximum possible performance of the accelerator。

The next computationally expensive primitive found in snarks and Stars our number theoretic transformation。

Also referred to as NTT。NTT is an algorithm that is used to multiply two polynomials。

NTT is similar to other algorithms such as FFT or DFT。

 but is unique in that it operates over finite field elements。

One of the common algorithms used to implement NTT is the coolly2 key algorithm。

This algorithm reduces the complexity of polynomial multiplication from order n squared to order n log n。

Similar to MSM， when performing a NTT off of the host device。

 the scrs must also be moved over to the accelerator。Again。

 the communication bandwidth can limit the maximum possible performance of the accelerator。However。

 unique to NTT is that the problem is not easily parallelizable。

 each element must interact with a variety of other elements during the algorithms operations。😡。

This means that the problem cannot be easily divided。😡，Furthermore。

 because these elements interact with each other， they must be kept in memory and operated on。

 imposing high memory requirements。😡，The final cryptographic primitive that we'll discuss are arithmetic hashes。

In many zero knowledge proof use cases， it's required that the prover demonstrate knowledge of a hash pre image or utilize hashes。

 Merkel roots， and Merkle inclusion paths to represent data that exists outside of the circuit。

In zero knowledge proof systems， arithmetic hash functions like Poidon or rescue prime are often used over traditional hash functions like Shaw。

These hash functions are chosen because while they are more expensive to compute natively。

 they are more efficient when used inside of a circuit。When deploying these hash functions。

 there are many algorithmic parameters that can be chosen when instanttiating the hash。

This can impact the computational cost。Some of these parameters include the field size。

 the field prime， the number of rounds， the MDS matrix structure， and more。At the end of the day。

 however， efficient implementation of this primitive is predominantly driven by modular multiplication。

As mentioned before， the computationally expensive operations involved in improved generation can vary from system to system。

In general， however， these operations are dictated by the commitment scheme that is used when instantiating approved system。

Commitments such as KZG or CAate commitments lead to MSM operations during proof generation。

Conversely， when Fryes uses the commitment scheme， the proof generation process is often dominated by NTT。

As a rule of thumb， many snark systems such as Gss16 and Marlin are dominated by MSM。

 while Starks are often dominated by NTT。In aggregate， however。

 these three previously discussed cryptographic primitives take up two third or more of the time across all proof systems。

Prior to acceleration。While these three operations might seem wildly different。

 they actually share common foundational components。

Underlying each of these operations like MSM and NDT are field and curveb operations。

These operations at their core are predominantly driven by field arithmetic and in particular modular multiplication。

So while these algorithms are structured substantially different from one another。

 their underlying performance often derives from the ability of the hardware to perform modular multiplications。

One interesting thing to note， however， is the relationship between data size and computational cost for modular multiplication。

While data size grows linearly， the computational cost of modular multiplication is naively order n squared with respect to the size of the field。

This means that as the field size grows， accelerator performance may be dictated by the computational cost of the operation。

But for smaller field sizes， an accelerator may be bottlenecked by its available bandwidth to the host。

This dichotomy highlights the importance of understanding the specific parameters of the proof system when you begin designing hardware accelerated systems。

It also highlights the difficulty in designing hardware accelerated devices or implementations that could service a variety of proof systems and parameters。

The first step to improving proof generation performance is to understand the computational memory and bandwidth costs of the proof system and use case that you are working with。

By breaking down the higher level operations like MSM and NTT into the number of modular multiplications needed to compute them。

 it is often possible to estimate the performance of the proof system across a wide variety of hardware platforms prior to completing and implementation。

However， in order to ensure that the estimate is accurate。

 there are a number of parameters that should be known in advance。

The first most important parameter is the number of eachT operation in the proof system。For instance。

 some proof systems may require four or more MSMs per proof， while others may only require two。

A second critical factor is the size of the operations that need to be computed。Oftentimes。

 different use cases will result in different sizes for each operation。For instance。

 in some use cases， the MSM will only be of size 1000。

 while in another use case it may be 10 million or more。

The size of the operations can have a large impact on which algorithms are most efficient。

The next thing to determine are the size of the field and the size of the curve for the operations that you're performing。

This will help to inform the bandwidth and computational complexity of each modular arithmetic operation。

Finally， there are a variety of other smaller factors that may contribute to the performance of the proof system。

 these may include the representation of the curve points。

 does the modulus have a unique structure that enables faster reduction and many more。😡。

Once all of these parameters are determined， the number of modular multiplications required to perform。

A proof or the proof generation process can easily be calculated。And with this number in hand。

 it can then be compared to the mod performance of a given hardware platform in order to derive a performance estimate or calculation time。

With knowledge of the calculations that need to be performed。

 the next step of hardware acceleration is selecting the right hardware for the job。

Given that these workloads are driven predominantly by modular multiplication。

 we should be looking for hardware platforms that can perform a large number of multiplications quickly and cheaply。

The estimated performance of a given hardware platform can be evaluated by looking at the number of hardware multipliers on the platform。

 the size of the hardware multiplier， and the speed and frequency with which each multiplier can be executed。

In order to illustrate this concept more concretely。

 on this side we show a table with four hardware platforms， a desktop CPU， a server CPU， an FPGA。

 and a GPU。The first platform， the desktop CPU， contains eight cores each with a 64 by 64 bit multiplier and operating at 5 gigahertz。

The multiplication power of this platform is estimated at approximately 164。

 and this number is calculated by multiplying the number of multipliers， the multiplier size。

 and the frequency and then dividing by 1000。The next platform， a server CPU， contains 96 cores。

 each with a multiplier， but running at a lower frequency。

This platform has a multiplication power of around 900， five times out of the desktop processor。

The following platform is an FPGA in this case， the FPG is substantially more multipliers over 6。

000 in comparison to the 96 present on the server。However。

 while that is approximately 60 times the number of multipliers。

 the multiplication powers less than twice out of the server CPU。

This is due to the reduced multiplier size and frequencying。Finally。

 we have a GPU with approximately 5，000 multipliers， each 32 by 32 bit and operating at 1。

7 gigahertz。This yields a multiplication power of approximately 9。

000 or roughly 5x improvement in performance due to the larger multiplier size and increased operating frequency over the FPGA。

For those interested in learning more about these underlying hardware of architectures and their impact on model performance。

 I highly recommend my colleague Simon Pffer's presentation from the Stanford Blockchain Conference several years ago。

 which can be found on YouTube。So with all that said， given these examples。

 if one was optimizing for either Mole throughput or Momo capital costs。

 the GPU would likely be an attractive platform to target。However。

 it is important to know that these analyses only highlight the underlying capabilities of the hardware platform。

In order to achieve the improved performance and meet the goals of hardware acceleration。

 other factors must often be taken into account。These can include the ability to realize the theoretical performance。

 the ease of deployment， the operating costs， the ease of programming， and many other factors。

Finally， with a firm understanding of the computational requirements of your proof system and a target hardware platform identified。

 there are two key areas to focus on for successful hardware acceleration。

The first is the selection of a hardware friendly algorithm that fits the target platform。

Target platforms like GPUs and FPGAs have fountain of core and work best with algorithms that are highly parallelzable。

Furthermore， when selecting an algorithm， you should choose an algorithm that aims to reduce the total computational cost by reducing the number of required operations。

Next， once an algorithm is selected， the final step is creating an efficient implementation。

Oftentimes， algorithms may need to be restructured to better match the hardware capabilities and design of your target platform。

In addition to restructuring the algorithm， oftentimes low level assembly primitives must be employed to more fully utilize the hardware resources and achieve the maximum performance。

Another thing to keep in mind when pursuing hardware acceleration is that multiplication is not the only resource required。

While these higher level primitives are dominated by modular multiplication。

 other compute resources in arithmetic units are often required。Furthermore。

 depending on the size and type of operations you are accelerating。

 non computational resources can become the bottleneck。For example。

 operations like NTT can sometimes be bottlenecked by the speed of memory access。Alternatively。

 for use cases with large problem sizes， sometimes all of the required data cannot fit in memory on your target platform。

 resulting in reduced performance。For accelerators connected to a host system。

 communication bandwidth can also become a bottleneck。Currently。

 many hardware accelerated NTT implementations， both GPU and FPGA。

Are limited not by their computational resources， but by their ability to move data between the host and the accelerator。

Sometimes these bottlenecks can be alleviated or eliminated by keeping data resident on the accelerator。

 thereby reducing the bandwidth requirements。This trend of data movement being the bottleneck rather than data computation is seen not just in NTT and ZKP systems。

 but has been a broader trend prevalent throughout big data and high performance computing environments。

For highly parallel algorithms， computation is often faster than the data movement itself。

 and therefore hardware accelerated designs should seek to minimize data movement。

Another consideration when using off host accelerators is the time it takes to move data to the accelerator and back。

For small problems， sometimes it can be more efficient to perform computations directly on the host rather than on the accelerator。

A final pitfall of hardware acceleration is the widely known Ammdelll's law。

Omdll's law states that the overall performance improvement gained by optimizing a single part or single parts of a system is limited by the fraction of time that the improved part is actually used。

😡，More simply in the case of ZKP systems， if MSM， NTT and arithmetic hashes make up approximately 65% of the time。

 then even if these operations are eliminated， the best speed up that can be gained is 3X。

In light of the 100，000 to1 million time overhead of proof generation versus native computation。

 it's clear that optimization doesn't end here。To wrap up today's introduction to hardware acceleration for CKP。

 I'd like to share a real life example of how hardware acceleration is being used today。

For the past several years， FCoin has been one of， if not the biggest EKP system in production。

 with between one and5 million proofs being generated per day on average。

FileCoin uses EKPs for proof of replication or Pro repP。

 which is a cryptographic way to prove that you have created a unique copy of a data set。

The proof of replication used in file coinin requires approximately 470 gigabytes of Poidon hashing。

If this hashing were performed on a many core CPU system， it would take around 100 minutes。

In comparison， the FCoin GPU implementation takes only approximately one minute on a modern GPU。

A roughly 100x performance improvement。For the cryptographic proof component of fileCo。

 they leverage the G 16 protocol。For each P rep performed on the FCoin network。

 a storage provider produces 10 proofs， each with approximately 130 million constraints for a total of over 1 billion constraints。

The MSMs alone required to create these proofs total approximately 4。5 billion point scalar pairs。

If these proofs were to be computed on a many core CPU， they would take around an hour to complete。

However， in comparison， they can be completed in around three minutes on a GPU。

 which is an approximately 20x improvement。This example highlights the ability for hardware acceleration to make ambitious ZKP use cases practical。

If you're interested in learning more about hardware acceleration。

 there are a number of great resources available online。

 including open source GPU and FPGA implementations for many of the cryptographic primitives discussed today。

One particularly great resource to visit is Zeprize。o。

 a community initiative focused on improving the performance of ZKP systems。

For those interested in the current performance estimates of the primitives discussed today。

 the table on the slide provides a brief overview of the performance that can be achieved for these primitives using a GPU and open source libraries。

For larger multi scalar multiplications， a single GPU can perform at a rate of over 100 million bases per second。

In terms of NTT， an NTT of size 2 to the 28 can be computed in under 250 milliseconds。

And for Poidon hashing， a GPU can hash approximately 350 gigabytes per second。

While there has been a tremendous amount of progress with ZKP hardware acceleration over the past several years。

 there is still plenty of room for improvement。On this slide are a few areas that could help make proof generation even faster。

The first area is improved algorithms for core primitives like MSM and NTT or other optimizations to existing algorithms。

A second area would be entirely new core primitives such as new hash functions with lower computational requirements。

A third area， while obviously an active area of research are new proof systems。And in particular。

 with respect to hardware acceleration， simplified proof systems。

Simplified proof systems can create more opportunities for hardware acceleration。

Examples of a more simplified proof system would be one that has fewer distinct operations。

 reduced communication and memory requirements， or even elimination of some of the computationally expensive operations that are present today。

Finally， there's also always room for improved implementations， both of complete proof systems。

 as well as the hardware accelerated prims。This includes targeting both commercial off the shelf hardware like GPUs and FBGAs。

 as well as custom silicon such as an AsI。In conclusion。

 I want to say thank you and provide a shout out to all the great folks who have been producing content about ZKPs and hardware acceleration for the past several years。

I'd also like to thank the incredible instructors who put this course series together and also those who are watching this video。

If you have any comments or questions about the content of this presentation or would just like to chat more about hardware acceleration。

 feel free to reach out to me at Kellyatsupernational。net。Thanks。



![](img/562634cb8ef1921784ac743c2a586325_2.png)