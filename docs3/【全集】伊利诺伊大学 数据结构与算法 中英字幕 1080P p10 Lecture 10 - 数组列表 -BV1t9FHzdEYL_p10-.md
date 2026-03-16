# 【全集】伊利诺伊大学 数据结构与算法 中英字幕 1080P p10 Lecture 10 - 数组列表 -BV1t9FHzdEYL_p10-

Hello， all。 Today， we're going to finish up with a linked list implementation of。U lists。

And then we're going to talk about a raise as an implementation of lists。



![](img/89a962d63a3fdcfdeb4ee44859045518_1.png)

So。We had been doing。Several functions。 And I want to talk now about what's probably the most confusing method that you have。

 which is remove。 So let's think about how we would do remove。



![](img/89a962d63a3fdcfdeb4ee44859045518_3.png)

Think about the fact that my pen has decided not to do pen。我。Yes， okay。Ru。Eth。

So we want to remove the ice element of our list。So let's try to code。First。

 by walking through the abstract implementation。Um， and then walking through the concrete。

 the best for contacting me is to email CS 225 admin。Because that way it'll go to me， Terry and。Brad。

 the grade book will be up this weekend。So let's walk through remove two。Okay。

 so the second element is。UWe have the zeroth， the first， the second。I apologize。

 I'll take a look at it。 I thought I fixed that， but I will take a look at it later today。

On the slides。The zeroth。The first and the second， so we want to remove the second。

How would we go about doing this。Any suggestions？A counter。Okay。So we've got a couple of things。

 so change the pointer to the first to go to the third element。 I agree we want that to happen。Okay。

But is that it？Isn't there something else we need to do， We need to delete the node。

 so we need to delete the node。Okay。Point1 to3 after deleting2。

I think we need to do something in the middle here。

I agree these are the two steps that functionally do what we want， right？

But let's see if we delete node， if we start with delete this， let's put the order on these steps。

 right？So。Yeah， we're going to first need a temp。And it's going to point there。 So we have one。Then。

 I think to。And then，3。Okay。Right。Right。So I think that's our process， we have three steps。嗯。

How are we going to write this， Let's see。 Let's try and write the actual code。



![](img/89a962d63a3fdcfdeb4ee44859045518_5.png)

First， we're going to use the index pointer。 Why do we need the temp。



![](img/89a962d63a3fdcfdeb4ee44859045518_7.png)

Is that what you're asking？How am I going to delete the node that is currently at two？😡，P。If。

 if I don't have temp。How do I delete that node and point to the next？

Because I have to these aren't an atomic step， right， yeah， okay？



![](img/89a962d63a3fdcfdeb4ee44859045518_9.png)

Okay， so the first thing we do actually， which we just skipped over was we need to get a pointer to node2 right because node2 is the node we want to delete and we had that wonderful helper function index。

😡。

![](img/89a962d63a3fdcfdeb4ee44859045518_11.png)

![](img/89a962d63a3fdcfdeb4ee44859045518_12.png)

Right， so we're going to use this again。And。Index。And that returned a list node。Pointer。Reference。

 and that's what we want again， right， because it's returning this thing。



![](img/89a962d63a3fdcfdeb4ee44859045518_14.png)

![](img/89a962d63a3fdcfdeb4ee44859045518_15.png)

This object here is。

![](img/89a962d63a3fdcfdeb4ee44859045518_17.png)

Being returned and and we want to modify that and we'll call it T。Or we'll call it in。

Seems like a fine for the node， okay。Then we need our temp pointer， right。

 and this is going to be a list node。Pointer。This one's not going to be a reference， is it？

This one is just a list node pointer。It'll be temp。And what are we going to initialize it to。



![](img/89a962d63a3fdcfdeb4ee44859045518_19.png)

![](img/89a962d63a3fdcfdeb4ee44859045518_20.png)

It's going to initialize to this value。Right in。It's the thing we're going to delete yep， I agree。

 and then we want to have n equals and next。And， finally。T。Okay。So。We have。Are four steps。

So the first thing we do is we get。Z。And to refer。To something that points。To the node。

 we want to move。Right。Okay。Then we make temp。Which is off on the stack。

And we initialize it to point to the same thing and does。We point in。The next。And finally， delete1。

So we have one。Qiu。3。F lines of code。And we're done。Yeah， the reason we needed to have a list node。

 we needed a reference is we needed it to be and to be a name of the node if it wasn't。

 if we had no reference there。And would be another pointer here。

And what we be doing is just changing that。Right。Why not address them？

Could we get back and still change N。 Well， address of N， if we did not return a。

Reference to a pointer would be an address on the stack。So there's a lot。

This is some pretty dense code。And this is one of the things that happens with pointers。That。

We get first， a reference to。The thing that we are going to change。Wei。

So that's this first line we get。A temporary pointer to save the thing that we are about to remove from the list。

Because if we did steps one and three without doing two and four， what would have happened？

Would our list be correct？One in three， but don't do two in four。Is our list correct？Yeah。

 the problem we have is a memory leak， but is our list correct， Our list is correct。

 so all of our tests on our list are going to pass。

 but we're leaking memory every time we remove something。This is what makes this hard。是。

Remove this bit。

![](img/89a962d63a3fdcfdeb4ee44859045518_22.png)

Wouldn't the node be pointing to two nodes， there would be two nodes pointing to the final location。

 right？

![](img/89a962d63a3fdcfdeb4ee44859045518_24.png)

There would be two nodes pointing to this node。To pointing。This。But that's fine。 The problem。

 The only problem。 If we do  one in three is that we're leaking memory。

 And if we never checked for memory leaks， we would have no idea there was a problem until suddenly there was no memory in our computer。

 right。And I say suddenly there was no memory in our computer because deep down in the operating system。

 it turns out is one of the most common places to see linked lists used。



![](img/89a962d63a3fdcfdeb4ee44859045518_26.png)

And if we did that wrong there， our operating system would actually use up all of our members。

So this is the code and every line has to be right。Yeah， remove， remove a node at a particular index。

 that's what it does。

![](img/89a962d63a3fdcfdeb4ee44859045518_28.png)

Right。Remove the I element。Let's go back to here。 It is。 N is the pointer that is in the S node。

 right， This is the zeroth node， the first node this。The second node。

It is the pointer in the S pointing at the two， right， We want to remove the two。

 So what we need is the pointer in our list that points at that two。😡。

So index returns a reference to a pointer that points at the I element。Okay。



![](img/89a962d63a3fdcfdeb4ee44859045518_30.png)

So that's all I've got to say about linked list implementation。😡。



![](img/89a962d63a3fdcfdeb4ee44859045518_32.png)

Well。If I delete without making a pointer， how do you get a pointer to what was the third element？😡。



![](img/89a962d63a3fdcfdeb4ee44859045518_34.png)

Well， if you delete temp without making a pointer。How did you make temp？Temp is the pointer you made。



![](img/89a962d63a3fdcfdeb4ee44859045518_36.png)

How does the work？

![](img/89a962d63a3fdcfdeb4ee44859045518_38.png)

Delete。Takes a pointer。

![](img/89a962d63a3fdcfdeb4ee44859045518_40.png)

As an argument and deletes the thing that that points to， That's what deletelete does。

 Delete does nothing to temp。

![](img/89a962d63a3fdcfdeb4ee44859045518_42.png)

Delete deletes what10 points at。Right？Delete， deletes what it points at。 Do It's really important。

 And one of the things that will bite you consistently。



![](img/89a962d63a3fdcfdeb4ee44859045518_44.png)

Is if you do not separate a pointer and what a pointer points to。If you do not include line 1，0，9。

Then。You don't have a linked list anymore。The index helper function is what we talked about almost all of Monday's lecture。

Yes。106 has list node， star and percentand N， and is a reference to a pointer to a list node。

If you don't include 109， what will happen， well the link at 3 won't exist。



![](img/89a962d63a3fdcfdeb4ee44859045518_46.png)

Um， what would it be like we would have if we did not have 109， we'd have this。This。Sorry， see this。

Yes。S points at。Memory。Deleted。I mean， your list would be up to end and then when you followed。

 did end next。Who knows what happens， You would go to the location in memory where the node was。Well。

 there's no way to get it the second one， right， nothing will point at this。They're just out there。

I mean。Leaked。A gone。Crash， if used。Ass will point to garbage。

Why do you have to point to a reference instead of the list node itself？

You don't point to a reference。What you have is a reference to a list node pointer。

One would be a pointer to a reference。 The would be a reference to a pointer。



![](img/89a962d63a3fdcfdeb4ee44859045518_48.png)

A pointer to a reference is basically nonsensical。 So the difference between a star and person and personan star is。



![](img/89a962d63a3fdcfdeb4ee44859045518_50.png)

![](img/89a962d63a3fdcfdeb4ee44859045518_51.png)

Star Ampersand is a very useful tool that lets you change what a pointer that exists points at。

 and Ampersand star is basically nu。

![](img/89a962d63a3fdcfdeb4ee44859045518_53.png)

Not a thing。Yes， because temp and end do point to the same thing。Up until you delete it， but。

Equivalent line of code absolutely would be n equals temp。

And that would be fine in this particular order。They would be exactly the same thing。Okay。So。😡。

That's implementation of。A list。

![](img/89a962d63a3fdcfdeb4ee44859045518_55.png)

As a linked list in C++。What is so with our linked list， we had a list node pointer。

What's the other implementation？If we wanted to do an array implementation of a list， how。

 what would we have， We would have exactly the same public interface， right。

 Our list should behave the same。 Our implementation detail should not change。

 What do I need to put in the private section。To manage my list。

Let's try and think about everything we needed， right， with。

Our linked list implementation in our private section， we had a list node。And such。 Okay。

 there are a couple of things we got a length is interesting And a T star。 So let's。

 let's start with T star。 right？ I like this。 What is this doing。And I'm going to call this data。

Right， so that's the array。So we have people saying max size and length。

Let's think about this for a moment。Because。Do we want to constantly have to reallocate T？Data。

So we're going to allocate some space for our list and as we put things in， we'll use that space。

 but at some point we'll have used up all that space and we'll need to reallocate it。😡。

So I want to separate two ideas， so here's data。😡，It's some。Right。

And there are a couple of places that matter in this array。I'm going to say we care about this。

 which and we care about this。So this is， we've allocated  one，2，3，4，5，6，7，8，9，10 spaces。

 so when we constructed our list， we made it10 long。And that's how much memory is allocated， right？

So。What do we want to call these two pointers， what do we want to call the first one？Is that length？

Where is that max size？Cur size。Okay， that's one possibility mid， mid。Used space。Till。

Interesting idea。 that sort of thinking about it from a so max in length。So。

Our suggestion is max in length。

![](img/89a962d63a3fdcfdeb4ee44859045518_57.png)

Head， if it existed， which it doesn't really the same sort of way， would be a pointer here， right？



![](img/89a962d63a3fdcfdeb4ee44859045518_59.png)

Ed。And we've already called that data。

![](img/89a962d63a3fdcfdeb4ee44859045518_61.png)

Size and capacity。So there are a lot of different options here。



![](img/89a962d63a3fdcfdeb4ee44859045518_63.png)

I happen to like size and capacity， and I like size and capacity because that kind of follows the STL version。

So we're going to call this size。And we'll use an underscore。嗯。And we will call capacity。

And I'm going to be shortened， I'm going to have cap。So what are these。

 these are probably and here is where it gets tricky， there's a couple of options。

 so I'm going to have size。And I'm going to have capacity。Current。Size of list。And capacity。

Available。4 list。Okay。It is dynamic in the sense of that we can allocate whatever sides we want using new。

 but we have to keep track of it。If we wanted a rip， we are implementing right now， in a sense。

Vectctor。And there's different choices。 So one suggestion is， these could be。Type T could be T stars。

 and that's actually a very legitimate choice。 We could choose to call them T stars。

But that feels kind of tricky。In general， I tend to advocate at this point in our programming that only using pointers when we have to will simplify our life。

 And if instead of these being pointers， what if I think of them as。



![](img/89a962d63a3fdcfdeb4ee44859045518_65.png)

This is size。And。This is capacity。So therere links， right？And either one of these choices will work。

I'm going to choose because I'm going to want to return， right？The the size， probably so unsigned。

 sounds good。Okay。We could use size T or use size T。But yeah。

 though that would also be a reasonable choice。I'm going to use unsigned。

 it's a little bit easier to make sense of right now， but formally a size T。

 let me briefly talk about what a size T is。Is an int。Large enough。To index。Any memory。

well to say anything。Okay。That's what a size T is。We could argue that size C is probably the right thing。

 but I'm going to use unsigned for now。

![](img/89a962d63a3fdcfdeb4ee44859045518_67.png)

Okay。So how does this work？Well， why on signed， can they ever be negative？

They could be integers or doubles。But this is clearly a value that makes no sense to be negative。

 What does a negative long list mean？Is size T good for saving memory。

 Why would use use it instead of an unsigned int， sizeize T is defined to always work。

Whereas conceivably， my unsigned int might be 4 Bs。 And if I'm on a 64 B machine。

 so I have 8 B of memory， I could have an array that was more than 4 Bs of elements long。Right。

 I could have an array that was more than two to the 30 seconds。

 had more than two to the 30 second things in it。 and on most of our machines。

The largest we can have in an unsigned。 So it's guaranteed to be big enough to index any E。

 That's what it is。 Yeah， it's more resistant overflow。

 It's more portable so that if we go from one machine to another， we know it's going to work。

That's the way to think about it。Now， it's not infinite。

 but it is guaranteed to be big enough that any array that you can fit in the memory on any machine。

Will fit within a size T。

![](img/89a962d63a3fdcfdeb4ee44859045518_69.png)

Yep， okay， so。Let's see。 let's think about what's going on here。So here is our array。In this case。

 what do we have， Let's see， we have size。Equals。5， right？Capacity。Equals。5。

And what do we need to do if we want to。Add something to this。Let's do。And we have data。

Right so we want to do， let's think about the simple one first， push back。Maybe double capacity。

 We have to change the capacity， right。Pushback is also a function on vector， yeah。

You' will note that what we're doing here models a lot of what vector can do。

So we have to make a larger array， right， So we have to do a couple of things。

 We have to make a larger array， and we're going to make it some amount larger。s。

 let's just do the plus1 for now。So we now have a larger array。And then we have to copy， right？

So we got a copy。Okay。Then what do we do？Finally， we're going to insert at size。Right。

So make new array。Copy。Old。Qunu。Deelete old。De车。Qunu。And finally。

 we can do our actual work of insert。Okay。So。If we did pushback。Okay。So first。

 we have to make a new array。😡，Then we have to copy from the old array to the new array。

Delete the old。Why do we have to do size plus plus。What is size plus plus doing。

Size plus plus inserts at size and then increases size by one， right？Size is size。Well， I mean。

 this is a real question here。What should size be of this array？

So we're going to insert it size and then increase。 So this has size。Equals0， and。Cap。Equals4。Yes。

 it would。 I need to insert at size。 So in this case。

 I am using post increment explicitly for its value。I am inserting its size and then increasing size。

 right？Insert at。Insert it because sizes 5。 I insert at 5。At 5。Ven。Size 2，6。

We don't need a reference， but in general， we would have a constant reference。Yeah。

 doing plus plus size would make size six and then insert there， which actually。

 if we only expanded the array by one would crash。Okay。So push back， man， if we have to expand。

 it gets ugly。

![](img/89a962d63a3fdcfdeb4ee44859045518_71.png)

But。It's not that bad。How about insert it front？Insertted front was the easy function in our linked list。

 What do we have to do if insert it front。 and this time let's assume that we have that 10。

So we have size。Equals5 capacity equals 10 and data。Insert at front。Yeah， so we're going to have。

Insert at front if we have， say， X。We are now going to have to。Do。X。Were actually。

 we're going to have to。 we're not creating any new memory。 We have to do。5，2，2， S。Xi。X。Man。

 that seems really problematic， right， it's a pain。Yeah， start at size， move everything one forward。

 stick a new value in。But yeah， to insert it front。We had to copy everything。



![](img/89a962d63a3fdcfdeb4ee44859045518_73.png)

Could we start at the end of the array and move forward absolutely doesn't really matter？



![](img/89a962d63a3fdcfdeb4ee44859045518_75.png)

![](img/89a962d63a3fdcfdeb4ee44859045518_76.png)

嗯。You could write this loop in a forward order with a temp or a backward order without a temp。

 Honestly doesn't matter。 What is going to matter is that we have to copy every element， right。

 Insert at front。 What is the running time of insert at front， assuming we don't have to add memory。



![](img/89a962d63a3fdcfdeb4ee44859045518_78.png)

So running time。Time。If。No memory allocation。Yeah order in。Or order size。

 those are going to be the same we can assume。Order N。That's really kind of terrible， isn't it？

We don't really like that。What was the running time on our linked list implementation？😡，Constant。

 yeah。So。There was a question about that since。If we had a beginning of the list in the middle of the array。

 we could do stuff， so we'll talk about that， that's some good thinking can we do things better？

The answer is。You can make。Insert it front。Insert it back。Or if you really， really mess with it。

 insert at front and insert it back， run in constant time。How， well， if I store my list starting。

If instead of storing my list the way I drew it here， what if I stored my list？This way。

Now I have five three spaces。In the front。And so then， Constantine here。And as they said。

 I could store it in the middle。And we'll come back to this。But clearly。You can either do。

ItIt's simple to see that you could do insert front in constant time。Or insert back in constant time。

It's a little bit trickier， but you can do insert F and insert back in constant time。



![](img/89a962d63a3fdcfdeb4ee44859045518_80.png)

How would the vector implementation look like in this class。

 very similar to what we're talking about？

![](img/89a962d63a3fdcfdeb4ee44859045518_82.png)

But let's start thinking。Just like how many spaces do you reserve at the back。

 you reserve some amount and you keep track of them。No。

 you're just keeping track of where the start is， where the end is and the total size。

 and you can do that with three values。😡，In a lot of ways， we'll get back to the details。



![](img/89a962d63a3fdcfdeb4ee44859045518_84.png)

But for now， lets， let's assume right here， if we didn't have to allocate memory。

 it was clear that we could insert it back in constant time。



![](img/89a962d63a3fdcfdeb4ee44859045518_86.png)

![](img/89a962d63a3fdcfdeb4ee44859045518_87.png)

Here， insert front was expensive， but I claimed that we could do insert front in Constantine。

 Why are we using arrays instead of vectors because。Where somebody had to write vector。Right。

Here's the thing。In this class， we are that somebody most of the time。Vectctors great。

 It's absolutely。 It's exactly what we are talking about today is how do I make vector。

Somebody wrote that code and today we're looking at that。It's super cool。

But somebody had to write it。So。I'm not going to tell you today about the details of how to get insert front and insert back in constant time。

 But I want to ask now， when we talked about expanding。We had some choices， right？

We have the choice of。Maybe adding some number of elements。Or doubling。

 So let's try and figure this out。I don't think I like the plus one element。

 So here is going to be my strategy。 Let's try and figure out how much it costs。

If we are doing every time we run out of space。We add two elements， right。So right。

 we we have one element， we put in that， that's constant， we put in this， that's constant。

 and then we have to do copy， copy。Copy， copy， copy， copy。Right。Et ceter， right。

 so as we go through this。As we keep putting things onto our list。How much time does this cost？So。

Here's what I want to do。 I want to ask。If we have inserted。嗯。This is。

 I'm going to call this a round。Okay。So we have one round， two rounds， three rounds， four rounds。

 five rounds。Okay。Why is it adding to because we want to look at this， right？

We want to figure out what's going on。So。How much does this cost。

 We have people that are proposing that it's n squared。So how are we going to do this。

 so we do two copies in the first round。Four copies。Then here we are doing six copies。eight。10。

 right？So how many copies are we doing per round？On the case round， we do。

How many copies I'm getting all sorts of。I want number of copies in round two copies。In round。Or。

2 K for the k Thrs。 Okay， so we'll do it as K。2 k。Okay。Right， everybody's happy that it's 2 k。

So then the total number of copies we do is the sum。From one to R， right， of 2 k。Right？

And if we think back， we get what？R squared plus R。You， in fact， are out the two and so get through。

I just did this whole simplification through。There's a lot of steps in the math。

 but that's not our focus here。You should be able to think back to 173 and figure this out。

 maybe try it on your own because we might ask you some stuff like that at times。But if I told you。

 well， the running time is on the order of r squared plus R， or if I said this is big O of r squared。

 you go， what are you talking about， Professor？what the heck。What is R， as the user of this list？

You have no freaking R， right， What is this R thing you made up？So what do we really want this。

 We want this。In terms。Of and。Right？And we could say that n is equal to what？To O or。

So we get n over two， we get through， we plug this in。Or R equals n over  two。

 so plugging that in we get。And over two squared plus。And over to and we get。Squared plus2 n。Over 4。

So our final running time， in terms of。And。Well， what does that mean？Running time。So。Well。Copy， but。

This is copies。Coopies total。Right。This is the number of total copies we get。

What we want is copies per insert into list。Right？How do we get this copies per total。

 so we get n squared plus2 and over4。Divided by。We've done any inserts。Let's get rid of this， but。

Any inserts， we get this， we simplify this。We get。Ohm sorry。And。

So the running time of our array list， if we choose a resize strategy of adding two every time it fills up。

😡，Takes and time to insert。An thing。And squared time to insert end things。

 Every insert is taking end time。We had the total number of copies over and inserts， right？

This was the total copies done。4。And inserts。But we want。Yeah。

 I I was sloppy with the way I did this because I was also trying to run out of time。

 So that this strategy isn't very good。 but vector is a tremendously used tool。

So maybe there's a better strategy and on Monday。We'll revisit this topic and see if we can come up with a better strategy。

For now， enjoy your weekend。Good luck finishing。

![](img/89a962d63a3fdcfdeb4ee44859045518_89.png)

MP stickers。