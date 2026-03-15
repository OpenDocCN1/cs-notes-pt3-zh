# 【全集 秋季版】普林斯顿大学 C语言系统编程 中英字幕 p25 Lecture 25 - GDB与ARM -BV1u1feBoEsK_p25-.f30280

Welcome back to Co 217 lecture。 In the second part of this lecture。

 we're going to work through a simple example of using G D B with arm assembly language programs just to see some of the features and idioms that you will find useful in debugging your programs for assignments 5 and 6。

😊，Like in assignment 5， we're going to have a program that has a mixture ofC and dotS source files。

The C code is a simple little function driver program that reads in a size。

 allocates a string of that size， initializes every character in the string to the character A。

 except for the very last one， which is the nubite。And then it calls our Stlen function。

 which is custom written for us。 you'll see that it's capitalized differently than the center library。

 So our Stlin function not shown in this file。When it gets a result back from the return value from Stland。

 it prints that out， and then it's done。So let's take a look at that Sterlin implementation。

So our Sterlin implementation is written natively in assembly language code。

 so this is the text section。We have two semantically meaningful constants。

 We have min stack for the minimum possible amount of space we can allocate for a stack frame。

 and we have I， which is 8。 and so I here is going to be an offset from the stack pointer where we're storing the index variable for indexing into our array。

We announced that Stirlin is global。 That means it's visible in other files。 Again。

 it darn will better be because Maine lives in another file。And then we say， okay。

 now we're ready to begin Sterling。We set up our stack and the first thing we do after the prolo is we're going to store x0 R。

 so that is the zero register， we're going to store its value， which is naturally0 into SP comma I。

 so we're treating SP comma I that is SP plus I as a pointer and so this we're storing it 8 bytes from the top of the stack at the top of the stack we store x30。

 so this is the next variable down。We then load from the location of x0。Now x0 here。

Was passed in the string。So we've passed in the the address of the string into the function。

 that's in x 0。 And so we're going to load from that address， a single byte storing it into W 2。

 the lowest by of W2， the lowest bite of the the X 2 register。Then we're going to enter a loop。

 we announce the loop， we say compare W2 with the zero register if they're equal were done。

That is to say， if we looked into the string and saw the nobite。 we're done。

 We have finished counting all of the characters in the， in the string。Otherwise。

 we're going to load the value that we stored into I back into x1。

We're going to add one to that and then store it back into the variable I。

 So here we're fully using I， the memory location that I is stored in as the variable I。

 We're not using it in any temporary registers or anything like that。

 This isn't necessarily the most efficient。 We'll see that later。

 But this is a very thoroughly faithful。 perhaps too faithful。

 unidiomatic assembly language version of the string length algorithm that we we came to know in assignment。

2。At that point now we can go and say use this new value of x1， which we know is the index and x0。

 we will add the byte offset of the index to x0， which was the pointer to the beginning of the string。

And we will go to memory and fetch from that location in memory。

 the character there in the string and put it into W2。

And then we unconditionally branch back to the top of the loop to make our comparison again to see if we found the Nobite。

Once we eventually do find the Nobite， we come back down to the end and we will say。

 go get the value of I。 put it in x 0， because this is our result。

The index of the Nobite is the length of the string。We then do our epilogue。Destroy our stack。

 do our epilogue， which returns the return register to its original value， restores x30。

 and then we destroy our stack and we return。So let's walk through this programming in G。

 Here's our build command that we have built it from our previously compiled dot O of the driver。

 which was compiled with optimization turned on and then。Our STR dot S。

 the the source file and assembly。So we're going to launch G just as we have been。

 and at this point we're going to see a lot of the same commands that we have before。

 but with perhaps a new take in assembly， so let's get started。

So the first thing we'll do is we'll just break on Sterlin so that says we're going to go directly to the Sterlin function and stop there。

Now we'll run the program initially it looks like it's hanging here。

 but it's actually just waiting recall correct if you recall the main function actually prompts the user for input to say how big a string do you want。

 so it'll take a nice small one here and just say 10 and at this point now GB opens up and we see that we have two screens within our emAC window we have the GB interface and then we also have the code sitting there。

Initially， it comes top and bottom if you've grabbed my emax file。You'll see that we have。Transpo。

Split， there we go。 And so transpose split will make it instead top and bottom。

 itll make it side and side while keeping all of the same window contents。 All right。

 so I personally kind of prefer it side by side， but up to you。All right。 So we've dropped into here。

 And the first thing we want to say is， well， normally we want to look at our variables。

 but in assembly language。Well， what do we have？We do had。

 We did have variables in the context of Maine， but in our assembly language code， this portion。

We're going to use registers and we're going to use memory。 So let's see how we can do that。

We can use the command info registers that will show us each of the registers in the running process。

 So we see the value of x 0， x1， x 2， x 3， x4， and some of them have utterly garbage values。

 X 0 has this O X 4，3，0，0，1，0。 That looks like an address。 And indeed。

 it should be an address because that's what's passed in。 the address of the string。And you。

 lots of other registers， including the stack pointer and the program counter。

 So let's look at those quickly， the stack pointer。We need to print De sign SP。

 so when we're printing out registers， we always need to do the dollar sign before their name。

And when we print it， we get。That， and again， this looks like an address。

 but not particularly useful， but we can at least check and say， well。

 we know that given what that arrow says， we're about to change the sack pointer。 So let's do a step。

 We'll step  one instruction and print S P again。And indeed， it did change by 16 bytes from B0 to A0。

 it decremented。Great， so now that we've， we've done that， we should look and say， what's there。 Now。

 we haven't put anything there yet。 So we， we have no expectation that there's anything there。

 But let's just see what's there。We can examine what's in memory by using the X command X for exam。

So。A lot of this， you know the P for print， the X for examine it's just like we saw in the previous demo of using G。

 but here we're going to use it in the context of registers， so here we see that it has 00420018。

We have no context for what that should or shouldn't be， but let's step one more time。

 execute this store of the x30 and see what happens。At this point， it did change。 and we have 0，0，4。

0，0，5， F 0 as the hex address。 And we know it's an address because it's x 30。

 but we don't really see it that much here。 So let's see if we can find out a way to get get more information about this。

 So let's look at the the help for the X command。 And we can see that X can take as an option of format。

 And so the format can be。 it can be an octal or hex or decimal or unsigned or all kinds of things。

 including it can be an address， A or an instruction。 I。So we know this is an address。

 let's take a look at it that way so we can do x of a of still the stack pointer。

 and now this makes a little bit more sense， this says okay， the hex address 40，0。

5 F0 is at main plus 96， so it's 96 bytes beyond the start of the main function。

This seems vaguely believable in the sense that we've done some things in Maine。 and then。

After a while， after we set up our array， we invoke this。 we， we called this function。

 And so when we return from this function， we'll go back to a spot in main。 This makes sense。

We could actually look and see more closely。 We can actually look at that and say if we take that address。

 we can say examine as an instruction， What's at Hex。That。

And we can see that it's some sort of instruction that we're not personally familiar with。

 but it seems plausible。 We can actually do one better， if you will。 We can say， you know。

 let's see if this is really sort of what we're expecting。

We can give an argument that says count of how many。 So now I start to say， okay。

 I I have some weird S， X， T W that we don't know about。 And then in AD R， And then we're doing ads。

 we're working with X 0。 That's the type of thing that we would do when we come back from a function。

And then we have a BL to to print F， which we know we call immediately after getting back from this function。

 So this is looking good。 This seems like， in fact， we have stored X 30。

 and that value that we stored on the stack is， in fact。

 a location in Maine where we will return to after this function。

So that's where we're going to eventually， but where are we going immediately， well。

 that's what the program counters for。The program counter is the address of our next instruction。

 and so we see that that Stlin plus 8 kind of makes sense。 we've stepped a couple of times。

And so after we've done two steps， the next thing we're going to do is 8 bys beyond。

 We haven't talked about it yet。 but each of the instructions in assembly is is 4 Bs。

 And so this is going to make perfect sense。 All right， So let's see what's actually there。

 Just like with what we were just doing before， we can do the exact same thing。

 we can say X slash I of the PC。 And we get that the next thing is going to be a a store from X E R into S plus 8。

 And we already knew that。 We can see that on the other side of the window。

 But this is a way that if you're not comfortable using emax， but you still want to use G。

 you can invoke G from the command line and get the exact same information just like this。All right。

So we did something else here。 We're going to step one more time。

 And now we have done a store into S plus 8。 So let's see what's there。

 Let's make sure that we actually stored zero there。

 And so we can do that when we looked up you can see it just at the top of the screen here。

 when we see in the X。 The size letters are B for byte， H for half word W for word and G for giant。

 which is 8 Btes。We stored。0 into S I。 And that was supposed to be an 8 Bte register。 We used X0 R。

 So this should have 0 in it if we go to S P plus 8。 So let's take a look。We're going to examine。

We want to examine 8 bitetes at a time。S， P plus 8。And in fact， we do get zero。All right。

So that was displaying at once。 One could imagine that this is something we're going to want to display over and over and over again。

 And so we can use the display command to to continually display memory or to continually display registers。

 So the types of things that we're looking at in this program。

 if you look at the line that we're on right now， where we're loading into W2 W2。

 clearly going to be an important variable for us or register for us。 So we can use display。W2。

And that looks great。And then we can say we want to， if we're looking at， okay。X 1， again。

 going to be an important thing。 So display X 1， we haven't actually used X1 yet。

 So it's not going to be very interesting right now。But actually， hey。

 it has some value that might be useful。 All right。

 And so now the the last thing we want to do is recreate that that X command where we're examining Unfortunately。

 their display doesn't take this idea of memory location。 There's no。

 from P prints at once to display prints at many times。 there's no equivalent for X。

 But we can treat the the arguments that we give to X。

 these effectively pointers that we're saying follow the arrow and go examine the memory。

 We can actually treat them that way and dereference them right there。

 then in there in in a display command。So let's try it out。

If we try to just do display star S plus 8， that's not going to actually let it let us do it because S is treated like a void star。

 so it showed it that。It's just not going to let us do it。 So we have to do a cast。

 just like if we want to work with a void star and dereence it in C， same thing here in G。

 so we can do display。Inly， we can undisplay three， that's， a little bit nicer so we can display。

Star， so that's our dereference unsigned long star。 So this is a pointer to an unsigned long。

Why unsign long？ Well， Because in the sea code， this was a size tea。On our system。

 a size T is an unsign long。 So here we have it。 and it's S P plus 8。 Now， if I。

 if I do it correctly， it will actually give me， hey， this is the location that you wanted。

 which is0。So we've done some displays。 We'll undiplay for， because that wasn't what we wanted。

So now let's wait， let's do one more step。So we have W2 is the value 97。X1 is the value 97。And。The。

 the value of I is 0。So W2， not equal to0。 so this comparison should not end up branching。

We step twice， and indeed， it doesn't。So now we can go back and load from X 1。We do the add。

 you'll see that the x1 value changes。We store back into the value I in memory。

 and you can see now that the value at the offset 8 from SP changes。

And now we're going to be ready to do our next time through the loop。

 So we we started with a priming read with。Getting from x0 into W2。

 Now we're going to get from x0 comm x1。 So now we're saying take the base location of the array and add our index to it。

 And that is the the location we want to get。We do that。 Hey， look， it's another 97。

 That's because we put A's into all of these。 Inly。

 we could have done something a little bit scker here instead of doing just display of W 2。

We could do display slash C， just like with the the print or the X command。

 the display command can take a format specifier。And now we'll actually see that， yeah。

 this is the ASI value of the character lowercase A， which is what we know we have in the string。

All right。If you want to do some some more work， we can certainly look and say， oh， we。

 we had this x 0 comma x1。 So this was the address of the current element of the array。

 We could certainly print that。And we get some address。

 perhaps it would be colloquially more common or more idiomatic to do。

Print as a hex as an address or a print hex。And we get a hex address。

 but it doesn't actually matter to us。 But if we wanted to know what's actually there。

 we could do the same trick we did with S P。 so we could do display as a character。The dereence of。

This is now a pointer to a char we're thinking of it as because there's actually characters there in the array of dollar signine x0 plus dollar signine x1。

And so there we get and say， hey， right here at this location is the character A。

 and it will continue to be for a while。So at this point， we can。

 continue stepping and things are looking great。 But we sort of realize that as we step through。

 what we're really interested in is when W2 ceases to be A and becomes the Nobite。

And so when we're sitting here， we could say， okay， I want to step more than one at a time。

So I can count and say， okay， what if I step 7。That's convenient。 I can step 7。

 And now you'll see that my， my index is incrementing each time。 So that's going pretty well the。呃。

That would be great， but maybe we don't want to do that calculation， maybe。If we。

 if we don't want to either count or it's， we're just not sure of exactly how that would work。

 we could always do set a new break point so we could set a break point on。 this is on。Line 18。And。

Here on line 18， we could set a break point and say， okay， now we know how to do it。

 We'll continue going through there。 Everything would be good。不。😡。

That would still say this only works if we know that it's always on exactly this line that we're going to do our access。

What if we wanted to check every time that we change the value of W2？Well。

 just like there's a break point for when you reach a linening code， there' are also watch points。

 So watch points say every time I change this variable and there are exact details for every time I read it every time I access it at all every time I write it。

 So for now， I'm just going to do the standard just watch。And I can do watch Dear sign W2。

And now I can just just like with a break point where I can just do continue。I continue through and。

It will go all the way until its value is changed。 Now， this is tricky because。

We changed it a whole bunch of times， but we overrote it with itself every time we。

 we didn't change the value。 We just did a write of the exact same value into it。

 so it won't actually trigger until it finally changes value， Not that it was written to。

 but it actually changes。In this case， that's great。 That's exactly what we wanted。

 We can see now we， we have stopped。 It shows us the old value and the new value of this。

 of this value that was being watched。😊，All right。There were a number of other things that we can do。

 So we could have instead of doing that， we could have done the the break point and said。

 show me the break point。 And we know it's a whole bunch of steps。 So you've seen continue。

 perhaps you didn't know that you can give an argument to continue。 You can say continue 10。

 And that says， skip a whole bunch of continue skip do it continue。 Oh， you hit a break point， S it。

 until you hit you reach that counter at which point it will start actually being a break point again。

 So this is convenient。 If we had a gigantic array。 And we were stepping through， you know。

 one time each loop and using the break point instead of the watch point for the change。

This would be super handy， we could say， okay， just， you know。Continue 99 times。

 Then I'm going to be at the interesting point that I care about。

But we can actually do this without knowing the number of executions。

So we can add some conditional to existing breakpoint or watch point。

 and so that's with the condition command。So that would just be condition。

The number of the existing breakpoint or watchpoint， so in this case we could do the Watchpoint2。

And we want to wait until W2 equal equals 0。 Now， in this case， not very useful。 It's already 0。

 And because it has the same value，97，97，97，97， a whole bunch of times and then eventually become 0。

 that wouldn't be that useful here。However， we can do this without a watch point at all。

 We can actually do this with a break point。 So let me reset。嗯。

So we can do info breakpoints and info watch pointss and it gives you information about what it is。

 is it conditional， so you can see there that it's a watchpoint， it's looking at W2。

 we stop only if it's equal to zero and we've hit it one time the break point is in just the Sterling function。

 we've hit it one time。All right， so we've turned off Watchpointint2。It's not there。

 so let's restart and see what happens。 we can do it even a little bit scker。So we can sue a run。

 And yes， we want to start from the beginning。 We'll start。 We'll get this same thing of。

 let's say a big number now。 And so now we stop here at the very beginning of the function。

 And so now I say， aha， I'm interested in。This line over here。

 this break on line 19 or 18 or 19 as the case may be。

And I want to break there as soon as W2 becomes 0。 So I can do break on line 19。If W2 equal equals 0。

So。Now， let's continue。We continue。 It ran for a while there。

 And now you can see that we have hit it where the the index。Our x1 value is 1000。

The index in memory at S plus 8，1000。W2 is now zero。

 and the thing that we're actually looking at the the actual memory location in the string is the nubite。

So I think that's a super useful tool of as you're starting to look especially at this next assignment where you will potentially want to run it for many。

 many iterations， there are a couple of examples of how you can either with continuing with an argument or setting a watchpoint or setting a break point that's conditional go through and get the behavior you want to trigger and stop and allow you to look at the state of the program when some particular condition hits。

All right， so that was our brief tour of GDP The last thing I'd like to talk about in this portion of the lecture is just some more discussion of optimizations because that's really what's at the core of the part two of assignments of assignment 5。

So we're going to quit out of that。And now。We， we have our our handy little stir dot S。

 Let's copy it over into stir up dot S。And let's think about what optimizations could we make Before we do that。

 Let's go ahead and just see。 how long does this take。 Oh I'm going to echo a large number。

Into St lens， that's going to， it's going to ask me， how many times do you want it， and let's do it。

So we'd run it， this was compiled with optimization turned on of the Sterland。

 but not of that assembly because we just wrote it， and that's a big number and it took four seconds。

So the question is， can we do better， You might naturally think， well。

 you could have compiled with optimization there。 Okay， so let's come back up。嗯。

We'll talk more about optimization in the next lecture， but you know just for now。

 we'll try it again。And you can see that， you know。

-03 not getting us anything when it's already compiled the Sterling dot O and our hand coated assembly。

No big benefit。The compiler compiler optimization isn't going to help when we aren't running the compiler on our assembly。

 we're just assembling it and then linking it。All right。

 So let's look at our code and see if we have some， some natural。Things that we might want to do。So。

The thing we talked about last time was。Memory very slow。 We should use registers here。

 there's we certainly could use call saved registers。

 but I'm going to just use some of the registers that are call or save for simplicity。

 So I don't have to save them away， store them away and restore them。 And also because as it ends up。

 I'm not calling any functions here。 So I have no worries about having to have them be destroyed by some function call。

 So instead of memory， we're going to use registers。 And the other thing is。

Each time here I I'm adding an index， and then I have to recompute the location in the array。

 so I have to do another ad。If I was using this as more of like the equivalent of S RRP instead of SRA A from assignment2 using pointers。

 I think that we could potentially save an operation or two。 Will it make a huge difference。

 Who knows， But at least it would be a little bit cleaner rather than having the all of this stuff going on with the index to just think of this as a pointer operation as we walk down the array。

So let's first concentrate on getting rid of all of these memory addresses。

So we have store0 into the memory。 Nope， that's not going to be a thing anymore。 Instead。

 we're going to say， okay， X1 is going to be our。Our pointer。 So let's do move。Intex 1 from x0。

 x0 is the base pointer of the array， so let's move in T 1。For consistency in our array。

 we're going to be loading from wherever x1 points， so that's fine。

 we'll change it here even though they're in fact the same value。All right， in our loop。

 we still do a comparison at this point， though， when we are not going to do a load from S P come I。

We're going to。Just add one to the to the X1， which is serving as our index。 So that's fine。

 We still do need to do a load， though， because we need to load the actual value。 But here。

 instead of being x 0 plus x1， x 1 is the pointer to the current character in the array。

So we can just do load from X1 into W2。All right， so then we branch after after the entire loop goes around。

 instead of going out to memory and grabbing from I， we're just going to subtract the two pointers。

 we're going to say， where are we now， minus the base。

 and that's the number of characters that we're in between？

So we're going to do a sub from stored into x0 because that's going to be the return address from x1 x0。

 so we're saying x1 minus x0， the current location minus the original location。We restore。

 and everything looks good。 So let's see what happens at this point。So， we're going to look for。

Stir up。And let's run it。Already a significant difference。

I should be running these multiple times so I can tell you that the Sterland has consistently been between 4。

40 and 4。45 seconds and Stirlin opt here consistently is right at 2。91。

 give or take literally hundreds。Or even thousands。 So， so we've done that。 This seems great so far。

 Can we do more。So the idea in assignment 5 is really about being creative。

 looking at all of the things that you could imagine doing。

And so I mentioned earlier that we're not actually making any function calls。

If we're not making any function calls。We don't actually need a stack and we don't actually need to restore X 30 because we've never changed X 30。

 We've taken away all of the memory accesses。 So I isn't on the stack。

 We aren't making a function call。 So X 30 doesn't need to be on the stack。

 We can actually take those away altogether。Would we expect that this is going to make a huge difference。

 Frankly， no， because it's a single thing at the top and at the bottom。 Furthermore。

 this function is only called once。 If this function were being called over and over and over and over again。

 this would potentially be a big win。 But right now， yes， sure。

 it might have helped us on the very margins， but probably not a huge win。That being said。

We want to think about it creatively。 and we can say， O， we're comparing with 0。

 So every time we do this comparison with 0 and then a branch for equality。

But we know from a previous lecture that there is this compare with the value 0。

 And so I don't know if it's faster or not， Let's try。

 I could imagine it might be only because we don't have to do with two separate instructions。

 It's all wrapped into one。 But again， it's experimental。 We really don't know until we try it。

 We can think about it， we can pontificate。 We can read all of manuals in the world。

 but when it comes down to it when we're trying to optimize， especially in assignment 5。Try it out。

 See if it helps or not。 If it helps in your code， keep it there。 If it doesn't， don't。

So let's try it out， instead of this comparison with W2 and WZR。

 we are going to just do compare branch。To zero， the location we're going to is SLN and the register we're comparing to see whether its zero or not is W2。

We'll rebuild it。We'll try it again。And it， again， made a pretty decent difference again。

 So didn't really know whether it would be beneficial or not。 But as it ends up， yes， very much so。

You'll see in the Pit who get a book that they discuss a little bit about the loop structures and you'll talk a little bit about this in precept as well。

 so we can try that too， so when we look at our loop structure we see that we do a conditional branch at the top of the loop every time and then at the bottom we do an unconditional branch。

The problem with this is that each time through the loop。

 we're going to do a branch and then immediately do another check。

It would be nice if we could minimize that if we could get that down to one check and potential jump per iteration through the loop。

So the way we can do that is basically guard the loop。 instead of just having a。

 this is effectively a while loop， we could have an if statement outside and then a do while loop。

 So that way， we could have the only check come at the very end of the loop。

 And we wouldn't need this jump back to the top。 Let's see what that would look like。

So before the loop， we can check。If we're already at 0。

 if the very first bite that we read in was was 0。 That's the empty string。

 immediately go to the end， otherwise。Well， now we're going to go in and we know that the precondition of this loop is satisfied so we can come all the way down here。

And we'll just invert the condition here at the end。And say， if we are not at zero at this point。

Go back up to the top of the loop。If we are at 0 at this point， fall off the bottom。

 That's the equivalent of jumping to the end。 We just go to the next instruction。

 So will this help or not， I don't know。 Again， it's saving a little bit of logic maybe increases pipelining a little bit。

 but really hard to judge。 Let's be empirical about it and see。When we try it out。Maybe that's。

 you know， within the margin error as it were。 But if we try it again。

 and if we get the exact same time again or very close， Yeah， it seems like again， that made some。

Very small， very incremental difference， but enough small incremental differences with a couple of those big leaps。

 and suddenly you have a really efficient program that you certainly couldn't have done by just by compiling。

TheThe entire premise of this is that yes， while it is true that the compilers are awesome。

 as I said in the first part of this video， we can in fact。

 do much better than the compiler for certain tasks where either we know more about the characteristics of the program。

 the characteristics of the workload， we're able to make use of instructions that the compiler might not know about or know that they apply。

 and so it's really worthwhile to try and be creative when we try to optimize so that's the takeaway for the end of this again I encourage you to work hard on assignment 5 get started。

 you probably won't be to the part 2 F that I'm sort of implying with this section for a while now。

 but the sooner that you get there， the better it's certainly if you're having fun with it can take infinite amount of time and if you're not having fun with it。

 you know it's still a small bit of a slug to get as many of the optimizations as we suggest。

So good luck with that。