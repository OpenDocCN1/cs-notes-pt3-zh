# 【2024-LLVM开发者大会-•-中英】-p16-P16-DynamicAPInt---Infinite-Precision-Arithmetic-for-LLVM--BV18eNfepENu_p16-

![](img/3fa05e5c955db3475cee2d64bc75d9d4_0.png)

Yeah， so I imagine and I'm going to talk about dynamic APIN。Wwhich is a class for infinite precision。

 arithmetic and aythium， of course it's not you literally infinite。

 but I just wanted to disarbiate between arbitrary position which is apN which we already have in aythium and this one where you can you don't have to fix the width beforehand。

 but you can just use as big values as fit in your memory。O。

So why do we even want this well we have a Presssperger library up in another upstream。

 we don't really need to know what exactly a Presssperger library is。

 but basically it's a set of solvers for some types of constraint systems and it happens to be used in a couple of different places like for computing bounds of SA values or for find loop fusion and I been told in circuit but there's a couple of pieces so its used。

You know， these spaces in the compiler， so we want it to be fast and we want it to be correct。

To avoid mis compels， So how do we do that？Well， what even as a proper library。

 don't need to go into the details of the algorithms。

 but basically what it looks like is you have these mat and you get integers from them and you do some numericalmeral computations。

And what we want is to do this fast and correct so theoretically in the worst case it could turn out that you know these don't fit in 64 bits you might need exponentially big integers。

 but what we found in that paper is that in practice that's not the case most of the time。

98% of the time actually is spent in test cases that can be solve with just 64 bit。

 so what we really want is an inteigger class that will be really fast in this case。

 but just to the sake of correctness to avoid miscompise。

 we just want to have a fallback path for the really rare case where this isn't enough。

So like one really simple thing we can do maybe as stupid is like。

We just haven't class dynamic APN in this case with just a 64 bit integer and you do a multiply with an off flow check like with the built and intrinsic irative if there's an off flow if there is you just exit and so the user at least knows that something went wrong without instead of silently miscompiling but most of the time you just told the value into x in this case because it into because it's the multiply equal to operator yeah and it just works and it's pretty fast。

But it's not really productionary。So what we actually want is something that works almost as fast as this IDly versus to the incorrect。

So that's what we want to do with dynamic APIient。What we' are doing is we have our credit position supported just for correctness but really what we want is for the 64 bit fast path to work with and how we do that is we basicallyK have a union of N64 and in APpN and what happens is we run all these operations on the 64 bit integer in the fast case and if there ever turns out to be anO so then we will fall back to increasingly the largerzure widths of ApN but that really shouldn't be happening most of the time and what we really want to focus on is optimizing the 64 bit path。

So how do we turn that silly thing we had earlier， which is basically just a performance roof line for us into like a more like you know。

 a rear solution？So。Now dynamic a is a union of 64 and 8， like we said。

 and we have a tag that tells us when which one it is。

And yeah so we just need to check the tag and then if it is in the fast case with the small 64 by integer stored then we do the multiflow with the overflow same as the fourth and yeah we have to check the overflow of that and if know there was no overflow then we actually stored the result and return and if the fast path doesn't work then there's some slow path that we don't really need to worry about because its not going to happen but we just need to make sure it's correct it uses aient。

Anyway， so how do we make the fast path fast？So we want some kind of benchmark。

 so here this is basically a micro benchmarkch where you just do a lot of my。And this。

 in this case is like the roof line because we just have a 64 bit ink and exit if doesn of them。So。

Of course， like the compiler could optimize the whole thing away。

 So we need to do a couple of things。 we need to use x and and we need actually take instead of having one because it knows and one times one is just one it gonna optimize the whole thing away。

 we can take it as input。 But let's see all all of that and assume that you know we can the compiler not to get rid of the whole thing。

😊，And yeah， so we have this as a sort of roof line and we compare this against the same thing in our class。

 so here yeah you set a dynamic a to x and then x to 1 and you keep multiplying it with1 and similarly assume that we took one as input and so on。

So when I started trying to optimize this thing， one interesting thing。

 I mean in the spirit of a student talk I'm going to tell you some lessons that I at least learned it thought very interesting。

 which is that when you started looking at this we realized that if depending on how the loop in the top function gets uned。

😊，The performance of our code could actually change even though we're completely different functions。

 but yeah as it turns out in Sky Lake interces， the location of your code actually matters。

 so depending on where your code ends up in if it ends up if your entire critical loop is in like one aligned segment aligned to something it's going to be slow and。

Yeah， we found this blog post basically， which mentioned this。And。

So I mean for now we just like switch to like an empty laptop that we had right around。And yeah。

 so now how do we continue making this faster？这个是。Okay， let me just get rid of this。顶。But yeah。

 So how do we now actually make this 64 bit in class faster。

 One thing is that like we've been saying the whole time about。

Basically that this six fast path is going to be taken like 98% of the time and so we should try the compile that so it knows to optimize that part but actually it turns out that in AMD also you have the same thing with the code layout and if you annotate some branches with。

Some annotations like this， then you might change the ordering of basic blockss and you might mess up the alignment。

It might actually become slower， which is what happened in one particular example。

 even though we aertated it。A branch that was always taken in the benchmark。

 but yeah again from the blog post it turns out that you can pass some arguments Steium to align everything appropriately and that kind of works and this makes it like work 1。

2 x faster like putting annotations like this everywhere。And the other thing is to inline that again。

 has like a notable。Effect。And yeah， now that we added at these like basic things。

 we can come back to the micro benchmarkch。And。We looked at this thing like we looked at the assembly that came out and we played with it for a while and what we found out is basically if you look at the micro benchmarkch after inlining there's these three branches。

 it's like a really tight loop and there are three branches。

 the if for the flag the if for the overflow check and then there's a continue to continue the loop and。

Yeah so like I say we switch to this AMD thing and if you again go for Zen for microarchit you find this crazy diagram but then if you zoom in you find out okay there's only two branch ports so in this really tight loop it's hard for it to do three branches and that actually makes a difference。

And we did think of some ideas like okay， maybe you can combine these two branches into one and at the cost or some other arithmetic compute。

 but actually the conclusion is that the micro benchmarkch uses its usefulness at this point。

 like you kind of like exaggerated its utility because there's no like clear word code which is literally just。

Jump store you know， one might add like a bunch more branch things in the actual end to end benchmark。

Any further optimizations you do in this micro thing you don't have。So。

What did we end up achieving on the ML pressper thing with all these optimizations？

So the APpient just bare APient without even having any also checks or is actually kind of slow。

If we are ortho checks， it could be even so， but even if you just have these， its。1。

5 x lower than our dynamic APIN， which is fully correct。

 also checked is actually obvious works and the roof line that we had of the checked in 64 is about twice as fast。

That looks kind of bad， but actually there is some hope like although I won't go into the details of that。

In this talk， because it's not really a topic， but the main thing that we found out is that。

There are actually still a lot of tight loops。Where there are a lot of these flag checks occurring of。

 is this in the 64 bit time？And。You can sort of pull all these things out。

And then the critical code will work much better and one of the things that maybe we talk about in the future work part。

 but basically we want to provide like a function where you can give it just give it a lambda and it will do all the checks upfront。

And。Then do your actual computation。What I want to say is that。

If you do things like that then you can get really close， I mean pretty close to the roof line。

 so this is like 30%。So within the roof thing， so。And yeah。

 kind of another thing is when you in everything， you know。

 maybe it mess up the branch prediction because even though these branches are supposed to be always taken or always not taken like in the fast path。

 maybe you might think，Because they get actually put into different ways in the core when youre branch prediction might get confused。

 but actually if you compare the checked in 64 with the dynamic thing。

Although the number of branches increases by a significant amount， like 25， 30%。

The number of transmission misses does not increase actually that much。So that means okay。

 is able to kind of cope with。嗯。A extra branching。And then so the question is like what is something that actually might be causing the worst performance and one thing where you can see it is in the L1 data cache flows。

So they become basically double when you go from in 64 to dynamic AP。If you look at the misses。

 then they also basically double so basically it means that we are not able to preserve performance at all compared to the roofside and that's why one of the interesting ideas that might be worth doing later。

Is to use instead of a 64 bit， if you just had a 32 bit and some other flag。Then。

The two combined can be a pointer in the showcasecase and。In the fast case。

 you just use 32 bit smaller than each， and maybe that's still enough to cover most cases。

So that could be something worth trying。And the other one is the lambra that I spoke about earlier。

So。Yeah that's the end of my talk thanks for coming happy to take any questions。



![](img/3fa05e5c955db3475cee2d64bc75d9d4_2.png)

Thank you， Yeah， any questions， What's the size of the type if it's 64 bits and a tag， how does that？

Yeah， so that's kind of。So initially it was the 64 bit and the union with the APN and the APN is 128。

And then if you have a tag on top of that， it's actually you know three times 64 but so right now it's in a state where there is already a tag inside the APpN and that's being reused。

But。Eventually， then so then it's 128， but eventually we would want to。嗯。

Keep all the target business inside a and not have to look at it at all from where we are。

That's not how it is right now， but it's 128 to answer a question。Hi。

 just curious has have benchmark benchmarking against other libraries like GM or boost multi precision？

No， in this， so right now we didn't， but actually in the paper that I showed you in the beginning we did benchmark this kind of approach against GMP and GMP is really good when you have big numbers。

 but here we really almost always have smaller numbers and intents are being slow。Yeah。All right。

 I have a final question， so your benchmarking loop。Actually。

 one thing that's kind of common is if you have。The trip count of the loop， if。

 if that's like fixed and there is a relationship between this trip count and the the。

 the induction variable， right， then like scaf can actually infer and hoist the check。

 So you will see largely different coach and。Depending on a naive micro benchmarkch and what you will see in the in the real world。

Yeah， so actually， I did also try it with by taking the trip counter as input。

I should probably have put it on the side， but yeah， I mean。

 the resultss kind of old with but that is input。Yeah。Okay， thank you so much and then。😊。

To conclude the student advance。Do we have the last speaker？All right， great。

