# 【2024-LLVM开发者大会-•-中英】-p70-P70-A-data-driven-approach-to-debug-info-quality--BV18eNfepENu_p70-

![](img/2c3f6d113344300d14857baa942f3df3_0.png)

So hello everyone， today I'm going to talk about a data driven approach to Dbug In quality。

 so I'll be talking about the work I did on the Swift compiler earlier this year。

So first a morning introduction， my name is Emil Peterson， I'm a student at APpTch in Paris。

I interned at A earlier this year and this presentation is based on work I did while interning there。

Where my task was to improve the quality of Dbug info for optimized code that I am speaking personally as a student and I'm not representing art in this talk。

So first， why debug optimize code， there are three reasons I can think of。

 the first is embedded programming， we want to stop using unsafe languages like C in those areas。

But un optimized code is often too big for optimized targets。

So we have to use optimized builds even when they bargain。

The second is crash logs when we receive those， we still want to be able to debug what's happened on a production build。

And the third one is complex programs。Dbugging in an optimizeimd compiler gets really slow。

 so I would often prefer debugging the optimized bill to go faster。

The problem is that debuing optimized code is unreliable， stepping is not perfect。

 variable often unavail， and in Swift， sometimes the variable just don't exist。

When de being C plus plus， I often have to go up or down a few frames before I see the value of my variables。

 So the information is there somewhere in the compiler， but。Why can't we keep track of it？🤧嗯。

I believe that ver being unavailable is preventable in many cases， and we can fix those cases。

🤧So why does it happen？First let's take a look at the Swt compiler pipeline。

Swift code goes through the AST， where macros will modify it and can change。Dbug info。

 then it will go through the Sw intermediatemedia language or S。

Where optimization passes modify it and then through L IR with its passes and。

Foo machine I with its passes before getting to the object file。

And the debug info representation is different in for each stage， so when lowering to the next stage。

 we can lose Dbug information and at each transformation within stages like optimization passes。

 we can lose debug information。So variables can be lost while translating from one stage to the next。

 but most of the time they are dropped because optimization passes are written to optimize code and undeigned with debug information in mind。

In Swif passes often completely remove debug variables， so they don't even show us unavail in LD。

 they just completely disappear。And today we'll focus on how we can improve optimization par。🤧嗯。

A first simple approach is to read the code and try to understand what happens。

 but good luck with that。A better approach is to use a known example of variables being dropped by the compiler and then byecting to find why it's lost like at which pass。

A way to do that is to use textile， it can help bisecting LLVM passes。

 but it requires a code sample with a long debugging problem because we have to tell it what to expect。

And so that only works for LLVM and not C。It also runs the whole pipeline， which can be slow。嗯。

So the solution I'm presenting today is variable drop statistics， so what is it？

Those statistics happen within the optimization pipeline。

 so within one stage today I'll take the still stage as an example。

 but it would be the same for any of the stages that have optimization passes。

Within the CL optimizer， there is a lot of passes that will each modify the S code variable drop statistics work by running statistics between each pass。

When statistics are gathered， we will get a list of variables defined within each function。

 then for each pass， we compare the before and after。And if there is a difference。

 that means a variable was dropped by thepa and we report it。If variable was added by a pass。

 which happens when inlining code， that's normal， but。

Once a variable was added and another later pass shouldn't we move it again。What。

Constitutes available。Two variables are considered the same。 So in the before and after。

 if they have the same name， the same scope within the function。

 which includes what which function it was in line from。And the same source location。

So two identical variables can appear within the same function at the same time。诶。

That happens when a variable got split into different different allocations by SOOA or when a value was modified。

And we don't track those fragments。 We just track if the virus still exist。And for Swifts。

 we can run the compiler with those statistics enabled on any code base。

 we can run them on the Swt standard library because it has an impact on all the Sw codes that we write。

But the problem is that it's a bit special and it's not really a representative of code that can be written by developers using Swifts。

So we can run those statistics on the whole source capability test suite。

 which is comprised of over 200 open source Sw projects。

 so that should be representative of what developers usually do。

So if we run our statistics on the source compibility test suite， we get those big numbers， about 2。

7 million variables are dropped in total by different passes。

The passes is dropping most Ti variables are those passes that have a lot of different heuristics。

 like Spl CFfG or S combined。And。So that makes sense。But we can also see SOA up there。

Which is a pretty simple password that really shouldn't drop deeper info。🤧嗯。Some drivers are。O。

 to drop。When a function is reachable， such as with that function elimination or。

And that code elimination。It's okay to remove the variable。

Same thing when a scope within a function becomes unreachable。

 which means that the scope would be visible on none of the instructions on which I could set the breakpoint。

 then dropping the variable is fine。Also， the standard library defines transparent functions。

 which means we don't allow stepping into them so those variables can be deleted too。

So the ver will not appear in the debugger in this case。

Some variable values should be dropped when a variable is unused or when its computation is moved。

Into a new scope， then it can be unvailed in the original scope。

 so if we can can't keep track of the variable。It must not be removed。

 it must be marked as unavailable at that location。But this is often not done well by s passes。

 which is why variabless disappear so often， simplyify say F G is one of those cases。

If a value is folded and can be calculated by2 expressions from available values。

 then we should also show them as unavail while keeping is available there。

But some passes should definitely not drop feedback value for variables when a variable is split into multiple allocations。

Like with SOA or when it is moved from an allocation to a register with mid to W。

 or when it is moved from the heap to the stack with a log box to stack。And。

The deb value should follow。When a constant is folded and can be represented as a constant in a12 expression。

 and we should do so。In all of those passes， we are losing debug information at the s。

The problem is that these passes here in orange are mandatory passes in the C optimizer。

 and they are also run when compelling at 00。Thank you。🤧So， that's not good。

If we run the compiler in debug mode with variable drop statistics on。

 we can see that regular variables are dropped when compiling for debugging。

Because of some logic errors， some variables were showing up in the wrong scope。

 and they would be unavailable in the original scopes。

 and sometimes they would be dropped because they weren't handled。After fixing those issues。

 that's what it looks like now most passes are completely fixed and two thirds of cases with loadable by address are fixed。

The ones in the blue were from transparent function。 So that's fine。No。

 how did I find the real issues？ Like， I only have numbers here and not examples that can find me。

As I can help me find mistakes。The statistics report has more information that just the total number of dropped variables for each pass。

 It also includes the name of the function in which a variable was dropped and the pass number。

We can then recompile the part where the mistake occurs with flags to look at the seal on a small function before and after faulty pass。

 and it is actually pretty easy to understand what happens once we have that example。

So if you remember， that's what the report looked like for optimized code after investigating issues and fixing them。

 that's what it looks like now。Simplify CFG is now dropping 12% more variables because they aren't dropped by earlier passes。

 but overall we're dropping 35% less variables from 2。7 million in total to on 1。8 millions。

Passes such as SOA and fee expansion that should never dropped variabless are now fixed。

Now the current eight passes dropping most debug variables are those。

 and we should focus on those passes to have the most impact on debugging optimized Sw code。

So if you're interested， the pull requests for the verrop statistics can be found here。

 there is one PR for Swt and it has recently been reporteded to LLVM IR so we can also fix issues in LLVM IR optimization passes。

So there is still a lot to do， the LM IR patch was merged recently。And。

We could also add similar approaches to different stages such as machinech IR。

But we could also add them between stages like from C to LLVM IR or from LLV IR to machine IR。

And we have a few par that do a lot of different things， such as in combining LM and s combined in s。

And it can be hard to know what subpart is responsible for very being dropped。

 So it would be nice to have more fan queen statistics。

And we would also like to ultimately determine if fibers are being dropped for a good reason or for no valid reason and have separate numbers in the report。

Thank you for listening。

![](img/2c3f6d113344300d14857baa942f3df3_2.png)