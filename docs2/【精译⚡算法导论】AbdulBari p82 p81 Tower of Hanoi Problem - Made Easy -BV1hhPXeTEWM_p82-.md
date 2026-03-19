# 【精译⚡算法导论】AbdulBari p82 p81 Tower of Hanoi Problem - Made Easy -BV1hhPXeTEWM_p82-

Hello friends。 This video is about Tower of Hani problem。

I am going to show you how to write an algorithm for of Hanai。By taking a small example。

 as well as large example with3 disc。那个。The problem is there are three towers given。

And one of the tower is having a stack of disc in the decreasing order of the sizes from bottom towards top。

We have to move all this disk from tower A to tower C。And at any moment of time。

 a larger disc should not be kept over a smaller disk。

So this will not be easy to transfer all this disc， so for help。

 one more auxiliary tower is given which we can use for transferring this disk。

There can be any number of disk given in this tower。

So let us see how to solve this problem by taking a small example。

I am taking an example with a single disc。 Suppose there is only a single disc given in the tower。

Then the solution is very easy。 Mo what is from tower A to tower C。哪ic。If there are two disc given。

 disc 1 and is 2。Then。The first move will be move what is from Tower A to tower B。

As we are not moving into destination tower， we are moving into an auxiliary tower that is intermediate tower B。

 so I have written the statement like this move what is from tower A to B using C absent。

This is done。Nouned。Second movers， mover is from。A 2， C。So as it is a destination tower。

 so directly move what is from A to C。And this is done。Another third step is move a disk from。B2 C。

Using a。So here I am not starting from source or the beginning tower， I am starting from B。

 so I am again using the term using here。So B to C using a B to C using a。

So this is how the statements are free。And finally， this is moved。 So these steps were very simple。

 If there are two discard given then the problem is very small， it's very trivial。

 And these are the three steps。Now let us move to the next problem。If there are three this given。Now。

 we can call this problem as large。 This is a little bit complex。NowIf there are three disc。😔。

I am going to give the moves like this。Move two discs from A to B。Using C。Actually。

 we have to move one disk at a time， but here I am saying move two disk。

How to move to disk from one tower to another tower already we have seen it so you can apply that procedure。

So it means this statement is a recursive statement。So it is not talking about one discarded time。

 heres talking two discarded time， so how to move to two this we have already seen the procedure。

So let us see this and these two discard move here， this is done。

Second step is move what is from a to C。 Mo1 is from a to C。 That's set。It's done。

The third step is move to disc from B to C， these two discs。

 we have to move from B to C using a again， this is a recursive step。

 how to move these two disc to from this cover to this st all the day we have seen。

So this is recursive system。And finally， this is done。Now。

 these three steps are very important for devising a recursive procedure for Tower of Hanai problem。

来了。If there are n disk。Then those three steps can be written like this。When there were。

Three disc we wrote here too。So it means if it is four disk， then we' will write 3。 so similarly。

 if there are n disk， we write n minus1。So those three steps are repeated here。

 move n minus1 disk from a to B using C， move what is from a to C and move n minus1 disk from B to C using a。

So this forms our a recursive algorithm， for of Hani。Now here is an algorithm。

Here you can compare it with these three steps with de。And -1 is from A to B， using C。

And move what is from A to C。N minus-1 is from B to C， using a。Algorith is。If there are an disc。

And three towers are given， ABC。And if there are more than zero disk。

Then first step and minus-1 disc。Here B is the middle tower， which we are using。

 so I can call it as using。So now in this step。C becomes using， so C comes in the middle。

Source destination。This is middle1。 So source destination。 This is the middle one。

And next step is print of Mo is from A to C。 That's it。And third， n-1 disk。 This is sources。

 This is a destination。 This is middle tower。 So source's destination， and this is middle tower。

So this is how the algorithm is devised based on the three steps we have seen。

Here I am going to trace this algorithm for3 disc。So this algorithm or function is called by passing 3 disk。

And tower numbers are given1，2，3。Now， inside the algorithm， there are three steps。

First is a recursive call， then printf， then again a recursive call。

So I am not going to show this tracing in the calling sequence。But I am just going to expand this。

Now here you can see。When three disc pass with  one，2，3， then there are three steps。N -1， A， B。

 So n -1 is from 3。 is 2。AB。So，1，3，2。The next is print A。Print a face。1，3。Then again。

 a function call recursive call n minus1 BAC。So， two。This is B。 This is A， and this is C。Then again。

 these two recursive call has to be expanded。So they are expanded like this。😔。

Right now we call this as A and this as B and this as a， based on that， these calls are written。

Again， these will expand so this is how it looks like。As after one disc。

 the next call will be for zero disk。And nothing going to happen when there are zero disk。

 So that's why I put a mark here。To show that it terminates here。Now finally。

 and this completed tracing。These are the printers。I have collected all of them here at the bottom。

One，2， three， one，2，2， three，2，2， one，2， three， so on。Now。

 these are the moves that we have to take for transferring。Or moving3 is from tower A to tower C。

So let us see whether these moves will really help us in moving trades from Tower A to Tower C。

Here are the steps or moves。 The first move is 1 to 3。

 so we'll move one disc from tower 1 to tower 3。This is done。Then second move tower 1，2。The two。

This is done。Third move， Tower 3 to tower 2。你的试试。1， to 3。To do完。2，2，3。Then 1，2，3。

That's all we have followed all these。Moves， and we have transferred all these three is from tower  A to tower C or tower 1 to tower 3。

So that all is the tracing for3 disc now similarly， this algorithm can work for n number of disk。

Hope you have understood the working of of an eye。😔，Thank you for watching。Please， leave a comment。

