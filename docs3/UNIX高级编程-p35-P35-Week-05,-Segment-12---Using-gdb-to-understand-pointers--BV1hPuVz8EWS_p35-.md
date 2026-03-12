# UNIX高级编程-p35-P35-Week-05,-Segment-12---Using-gdb-to-understand-pointers--BV1hPuVz8EWS_p35-

Hello and welcome back to C S 631 Advance programming in the Unix environment。 This is week 5。

 segment 12， and we'll break out our good friend， the debugger one more time。😊，This time。

 we'll use it to illustrate how we can expect memory locations in the running program。In the process。

 we'll also review a little bit how point doesn and arrays work in the C programming language。

 as this is fundamental to eliminating things like buffer overflows and other common causes of program failures and security issues。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_1.png)

So let's go back to our print puffs program。This time。

 we'll compile it with dash G3 to ensure additional debugging symbols。

 which we'll use in a moment to access to find macros。

 which otherwise would not be available to us in the debugger。Remember， in our previous video。

 we had handled the edge cases of providing a negative or a much too large number here。

 But we didn't discuss what happens when we provide a reasonable or normal number。

Let's give it a try and specify 8 as the size of the buffer used to process the data we feed the program。

We enter 8 characters。Hey， now， exclamation point。And the program prints this。Buff is he now。

 which seems right。 But Buff， too， is empty now。But3 looks right， though。 What's going on here。

Let's run it again。 This time， we enter 7 characters and get。Buff looks okay。Buff 2 starts out。 O。

 But what's going on here。 Why does it say it's buff 3。Time to break out the debugger， I'd say。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_3.png)

We'll break in print buffs。

![](img/447ca542b40911f5a1b7f5e5c13f51e9_5.png)

And run the program again。

![](img/447ca542b40911f5a1b7f5e5c13f51e9_7.png)

There。No。And is 8。So， we call malloc 8。Likewise， for the other two buffers。

 all three are now 8 by buffers。

![](img/447ca542b40911f5a1b7f5e5c13f51e9_9.png)

Let's make sure they are all valid。Okay， all three are valid pointers or empty at this point。So far。

 so good。Now we execute the next line where we copied data 2 into Buff 2。Yep， that broke as expected。

 everything normal here。On to the next night。Where we now copied data 3 into above 3。Yep。

 that looks right too。Next line， where we call getss。He now。P Buff。And that looks good， too。But Buff。

 too， looks wrong again here。 How did that happen。We didn't do anything to Buff2 after we called SDR copy。

 and we had confirmed the buff that Buff 2 contained the right data。And aboveuff 3 is still correct。

But it looks like what is in Buff 2 over here is actually the data we had meant to write to Buff 3。

So let's take a look at the memory locations of each of these arrays。1 is B0，10。And the others be 0。

18， while buffers be 0，0，8。What exactly is Buff。Buff is a cha star or what we call a string。

But a string really is nothing but an array of characters， right。

 and an array is nothing but a point to the beginning of the string。

 The first character with the assurance that the next element is another character until you find a no。

So if we inspect the location where a buff points to。We find a single character at B 0，0，8。

 the H from Hano。That's the same as saying bath 0， right。The next character， then。Mis Buff what。Okay。

 so far， this makes sense。Now， in GB， we can do more than just print a given variable。

 We can also examine any memory address for that， we use the X command， which then takes a modifier。

 which tells GB how to present the data at the given address。Here， if we say x slash C。

Of this address。Then we are saying， print the value at this address as a character。

And so we get the same age ASI character here。What we find at B 0，0，9。 That's just1 B further。 So。

 yep， that's where the E of he now is。But B 0，0，8 is the address of Buff。We can also say。

 print the address of Buff plus one， and we'll again find the same E there。That is。

 an array subscript notation is the same as referencing the beginning memory address and adding the offset。

So pointers in the arrays are just about the same thing。Now。

 remember that the address given here is in hex。 So what is the last element of the string hey now。

Hey now is seven characters， but we know that all strings are all terminated。

 so we can look at the eighth by from the beginning address。B 0，0，8 plus 8 is B 0，0， F。And yep。

 that's where we find the nullbite。Now， what's buff to again。Buff 2 is at address B 0，10。

 which is exactly 1 B after B 0，0 F。 And we had written the string。 Hello。

 I am Buff 2 to that location。Yeah， let's verify that the data we thought we had written here was indeed that。

For that， we use info macro。Which shows the right data。But how large is that data。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_11.png)

That's 17 B。But up here， we had allocated only8 bytes of data for above 2。So Maoc went out and said。

 oh， you want 8 B of dynamically allocated memory。 Sure， no problem。

 I can squeeze it in my ear and handed us back a pointer to a chunk of memory that was exactly 8 B in size。

 starting at B 0，10。😊，Then we asked Meloc to get us another pointer to a chunk of memory。

8 by in size for above 3。And Malo said， sure thing。

 Here you go and returned the pointer at location B 0，18。That was reasonable。

 Malick knew that the space from B 0 to B 0，17 was reserved， but anything after that was fair game。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_13.png)

But that location is directly after the previous pointer。

 And so if we look at what is at the address of Buff 2， B 0，10 plus 8。Then we get， of course， B 0，18。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_15.png)

The address of path C。In other words， when we ran SDR copy of data 2。

 we wrote 17 B of data starting at B 0，10， but then called SR copy with data 3。

 writing 17 B of data at B 0，18。That is， this over here is actually 3。When we say print buff 2。

We are effectively telling GDP B， begin at the edges of Buff 2 and then print as a string。

 the contents。 The string is defined as going on until the null character is encountered。

 But our SDR copy of data 3 overwrote the null at the end of Buff 2 so that print Buff 2 continues to print data until it finds the null at the end of Buff 3。

Let's try something else。We break in line，25。And I guess we don't need the first breakpoint any longer。

 so we delete that。

![](img/447ca542b40911f5a1b7f5e5c13f51e9_17.png)

We run the program again and stop right before we call getstz。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_19.png)

Here are all buffers once again， just like before。Now， we run getss。But we enter 8 characters， not 7。

Buff is no。Hey， now， exclamation point。Which has8 characters。And Buff 2 is。Nothing。Why is that。

Buff begins at 4，0，0，8， and contains7 characters。So，4，0，0，8 plus 7。Contains the last character。

The explanation point。But strings are not terminated。 So 4，0，0，8 plus 8。Is。Yep， no。

But that address 4，0，1，0 is the address of Buff 2。So by allocating an 8 B buffer， but entering 9 B。

The eighth character of our exclam in our exclamation point， plus the drillinging null。

We overflowed Bth 1 and rode null into the first bite of Bth 2。Now， if that is correct。

 then we should still find the remainder of the data we copied into Buff 2 at the memory locations beyond 40。

10， right。And yep， at 4，0，1，0 plus 1 or 4，0，0，11， there's the E。1 by more。

 And we find L and so on and so on。So here we observe something important。

 Riding beyond the boundaries of a buffer does not necessarily lead to a segmentation fault。

It just means that you're writing data into the given memory location。

If that happens to be the address of another pointer， then you' simply overriding that data。Here。

 let's see if we can illustrate this by example。Let's delete all break points and just run the program。

We enter8 characters string。Meaning the trailing null will cause the first bite of Buff 2 to be null。

 which is why null Buff 2 looks empty to us， even though there are other characters after the null。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_21.png)

But3 remains， as expected。Now， if we run it again and enter a longer string。

 what do you think will happen。Here， we enter 16 characters。And get。Buff  one。

 containing the full 16。With a second aid overflowing into Buff 2 and the null at the end of this string flowing over into Buff 3。

And so we know how to overflow and place content we'd like to be above three into that location。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_23.png)

This is Buff3。

![](img/447ca542b40911f5a1b7f5e5c13f51e9_25.png)

So how do we avoid this problem。Well， instead of really nearlyly writing data into buffers。

We should use SR N copy and be careful to never write more data than the size of the allocated buffer。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_27.png)

Which is not the length of the data。But rather， the size of the buffer。

But it took at the manual page， anyway。Note that S N copy does not nu terminate the data。Meaning。

 we have to do this ourselves。

![](img/447ca542b40911f5a1b7f5e5c13f51e9_29.png)

So we do this here explicitly。Then we repeat this before above3。Let's give it a try。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_31.png)

We again， enter a longer string。

![](img/447ca542b40911f5a1b7f5e5c13f51e9_33.png)

And。

![](img/447ca542b40911f5a1b7f5e5c13f51e9_35.png)

Wait， we observed the same situation。 Why is that， I thought we had fixed this。Again， to the debuder。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_37.png)

Here， let's take a look at the different buffers again before we call getstz。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_39.png)

![](img/447ca542b40911f5a1b7f5e5c13f51e9_40.png)

![](img/447ca542b40911f5a1b7f5e5c13f51e9_41.png)

Aha， Buff 2 and Buff 3。Are correct。We only rode 8 ps into these buffers， as we shall have。But now。

 when we call getss。We once again， overflowed Buff。And thereby， buff 2 and buff 3，2。This is because。

Here we are well beyond the Stu N copy， which was only used to initialize the buffers。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_43.png)

And remember， when we compiled the code， a compiler gave us a warning。And very explicitly。

 it told us to not use Gs exactly because it does not do any boundary checking。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_45.png)

The manual page is equally unambiguous。 Programs should never use this function。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_47.png)

So let's replace our call to getss with a call to F getss。

We instruct Fgos to not read any more than the size of the buffer we allocated。So， no。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_49.png)

We no longer overflow any buffers。

![](img/447ca542b40911f5a1b7f5e5c13f51e9_51.png)

All right。 I think this will have to suffice as far as G is concerned。 Like so many other un toolss。

 it's something that you just have to use a bit to get the hang of。 But once you do。

 you can't really live without。In this video， we built on top of the lessons from the previous videos and showed that we can inspect arbitrary memory locations using the X command。

 When doing so， we define the format of the memory location and can thus print， for example。

 characters or strings。😊，We also saw that we can use the debugger to really understand code execution。

 And from there， better rock pointers in the arrays in general。

We saw that a string is really nothing but an array of characters。

 The rays are nothing but sequential memory locations， which can access by a simple point arithmetic。

By incrementing the address of a pointer， we can iterate through the array。

 and so star pointer plus 1 is the same as pointer Subscript 1。

While we knew that strings are null terminated， we are also able to illustrate what happens when there is no null or the null is placed earlier in the array。

In our code， we then showed that overflowing a buffer that is writing beyond the memory address that was allocated for a given buffer does not necessarily lead to a sec fault。

 In fact， the sack fault is actually the best case scenario。 since at least here。

 your programme fails。A much more risky scenario was the one we observed。

 whereby overflowing one buffer lets you control the content of memory addresses and use elsewhere。

Now， most of this is not something that's strictly speaking part of debugging。

 but I hope that I was able to show you that you can use the debugger to deepen your understanding of the program youre analyzing。

In this series of videos， I' try to give you an idea of what a Dubugger is capable of。

 As I mentioned before， if you learn nothing else， but that you could use G to pinpoint your sack faults。

 then that alone is a win。But I still recommend that you consider finding a good tutorial for your preferred to burgerger and follow it。

 There's so much more to learn。For now though， we'll stop our coverage of the debugger here and move on to other development tools in our next video。

Thanks for watching and see you next time， cheerus。



![](img/447ca542b40911f5a1b7f5e5c13f51e9_53.png)