# 【全集】范德堡大学 C++标准模板库 中英字幕 1080P p23 Lecture 23 - 非变异算法 part1 -BV1KWiCBWE7M_p23-

。Hello and welcome back to the next session in my webinar series on C++ Standard Template Library by example。

Today we're going to continue our coverage of so called non mutatingeststL algorithms。😡。

We're first going to take a look at some algorithms that will search for the max or min element in an iterator range。

Next， we'll take a look at the famous for each algorithm that accesses each element in a range and performs a function on it。

And lastly， today， we're going to take a look at the equal and mismatch algorithms。

 which as the name suggests， check ranges to see if they're equal and also check to see whether or not there's a mismatch and if there is a mismatch。

 it'll tell you where the mismatch started。So without any further ado。

 let's go ahead and take a look at what we're going to cover。I'll start by sharing my screen。

And you can see here that the source code will be in my GitHub repository as always。

 and it'll be in the C+ plus STl S10 folder and today we're going to examine the contents of the 10。

5 and 10。6 subfolds so let's switch over to the IDE we're going to start off by taking a look at two methods actually four methods because they're overloaded that will check for the min and max elements in an iterator range and max element will find the largest item in the range potentially using a binary predicate that you can pass in min element conversely finds the smallest element in a range and also may use a binary predicate like some of the other non-mutating algorithms we've looked at like find and find if these algorithms return in iterator pointing to the min or max element found which should always be found unless the iterator range is empty Here's the signatures for the first two methods we'll look at。



![](img/8014d5f1512346ad32cbe277c91c93a0_1.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_2.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_3.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_4.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_5.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_6.png)

Max element and mid element and these both take forward iterators because they have to save the iterators of the largest and smallest values found and input iterators don't let you do that so we use forward iterators here。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_8.png)

You'll also notice that Mac and Min element methods use operator less than to identify the biggest and the smallest elements or items in the range。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_10.png)

There's also a way you can pass a predicate in and that predicate's a binary predicate that takes you arguments and that one of the arguments will either be the current max and the current element or the current min and the current element and so you can control how those predicates work and they should only only return true when the element that you looking at in fact should replace the current min or max as we'll show in just a minute so these are the signatures for those other methods now note these methods are kind of funny unlike most of the methods that take predicates like find if or count if or remove copy if and so on。



![](img/8014d5f1512346ad32cbe277c91c93a0_12.png)

Which had the underscore if suffix， the max element and min element methods for some strange reason don't have the underscore if suffix and I've always thought that was confusing。

 I wish they would have fixed it at some point， but I suppose at this stage it's grandfathered into the namespace of C plus plus STL so we're just going to have to live with that confusion。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_14.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_15.png)

There's a little functer we're going to use in one of our examples below when we deal with the max element。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_17.png)

Algorithm that takes a binary predicate and you can see this is going to return the max odd number。

 so when it's called it's going to take a look at the current value。

 see if it's odd and if it is odd then it's going to check to see if it's greater than the current max and only if both those conditions are true will it be used as a replacement for the current max and we'll talk about that because the logic here is a little subtle。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_19.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_20.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_21.png)

Here is the。Main program where we're going to go ahead and use these S algorithms to check for in in maxes in these range ranges and the actual。



![](img/8014d5f1512346ad32cbe277c91c93a0_23.png)

Range we're going to have here is going to be a vector of ints。

 which just has a bunch of numbers in it， which I call stats。

 But I could call it whatever and call it， you know， vector of。That1 or V1 or what I usually call it。

So we'll start off by looking for the max number in that range。 And this is very simple。

 We simply say max element stats dot begin going up to， but not including stats do end。

 And what we get back， of course， will be an iterator to the result and assuming that we found a max。

 which we should。

![](img/8014d5f1512346ad32cbe277c91c93a0_25.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_26.png)

It will go ahead and print it out Max we're going go ahead and use min element and as you can see here min element works pretty much the same except it's looking for the lowest element or the minimum element in that range once again we start into an iterator and then assuming we have't fallen off the end we can print that too Now the next couple methods here are going to replace the use of the implicit operator less than which is used to compare for mixed max and min with an explicit predicate and we're going to do this a couple of ways the first way we're going to do it is we're actually going to pass in the max odd funcctor we defined earlier and if you recall the max odd funter which is up here it goes ahead and checks to see if the number is odd if the number is greater than the max if it's odd and then that returns true in that case to replace the current max otherwise it returns false。



![](img/8014d5f1512346ad32cbe277c91c93a0_28.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_29.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_30.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_31.png)

And so we're going to look through that range， and we're going to find the largest odd number。

 And then we're going to print that out。 And then the last thing we're going to do just for kicks is we're going to do the min element。

 And we're going to give a predicate for this as well。 except in this case。

 we're not going to use a functer。 We're going to use a good old C plus plus generic lambda。

 And in this case， I kind of hardcode it to be。

![](img/8014d5f1512346ad32cbe277c91c93a0_33.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_34.png)

And I should probably generalize that just to be on the safe side。

 so now it's a generic lambda or a more generic lambda。

And you can see here what we do is we check to see whether the value x is odd and whether it's less than the current min。

 and if so， we return true。

![](img/8014d5f1512346ad32cbe277c91c93a0_36.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_37.png)

So let's go ahead and run the program and then I'll talk about some of the kind of weird quirks about this。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_39.png)

So you can see here that what we get， let me give you the results and then we'll go look at the input to make sure that they make sense。

 which they should。

![](img/8014d5f1512346ad32cbe277c91c93a0_41.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_42.png)

You can see the max is 67 positive you can see the min is minus 40 and that's also correct you'll see that the max odd value is 67 and the min odd value is nine and that's all correct but what happens if we go up here and we change this to say10。

😡，Well， we're going to get a very strange result here and when we run it。

 we're going to see it comes back and it says Max odd 10。😡。

How the heck did that happen obviously 10 is not a an odd number it's not even a max odd number for that matter well if you go look at the code you get a hint as to why it has this somewhat strange results。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_44.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_45.png)

So let's go poke around and look at main element。😡。



![](img/8014d5f1512346ad32cbe277c91c93a0_47.png)

And。Here's min element and of course， min element。

![](img/8014d5f1512346ad32cbe277c91c93a0_49.png)

Has to be bornnerary and it has to call an internal mini element。

 but luckily there's just a handful of look at and here's the one that's actually doing the checking as you can see here it's past the first and last ford iterator and the comparison。



![](img/8014d5f1512346ad32cbe277c91c93a0_51.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_52.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_53.png)

Punter， the predicate。 and at first equals last。 it's like we're just done。 bailil out。 Otherwise。

 we go ahead and store the first。

![](img/8014d5f1512346ad32cbe277c91c93a0_55.png)

Iterator in the result。 so this is why we have to use a forward iterator because we're going to store this here and so that means if we go back and look at our example。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_57.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_58.png)

Probably shouldn't have。Made this so big if we go back here and look at the main program。

 you can see that we started out with the value 10 so that's going to be the first element so result。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_60.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_61.png)

Will be 10， no matter what happens， doesn't matter what its value is。

 And then we start marching through from plus plus first to up to， but not including last。

 So that means， of course， it's going to start the comparison with first at 25 and result starts at 10 And then if you see what happens here every time the comparison returns true Every time we tell it。

 hey， this thing is the min， then it'll replace the result with the current first and when we're all done。

 we return result Well， the consequence here is if it turns out that there are no。😡。



![](img/8014d5f1512346ad32cbe277c91c93a0_63.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_64.png)

嗯。😊。

![](img/8014d5f1512346ad32cbe277c91c93a0_66.png)

Min values that are odd， which is the case here， so if you take a look here。😡。

None of the values here are。😡，A odd and also less than Ted。😡，And so as a consequence。

 it's just going to return 10 so that's a little bit of a quirk you just have to get used to that but modo that if you keep yourself。

 if you limit yourself to binary predicates that don't do wacky things like look for odd numbers that may not exist。

 then you'll be perfectly fine。😡，Okay， so that explains how the。

Max and min methods work let me change this back to nine。

 so next time I can give you the example it won't blow up in my face。😡。



![](img/8014d5f1512346ad32cbe277c91c93a0_68.png)

We're now going to go ahead and take a look at another example and this one's going to illustrate a very famous STL algorithm。

 one of my favorites， the for each algorithm and we'll see that this is part of a number of algorithms that process or compare elements within an iterator range so for each is the one we're going to talk about first and that's going to go ahead and apply a function to every item that's in the range you'll see there's also an equal algorithm that checks to see whether every item in a range is equal to another range。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_70.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_71.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_72.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_73.png)

Possibly using a binary predicate， you can check equality various ways and then the final example we're going to look at here。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_75.png)

Not this example， but the next example will be mismatch and this looks through two parallel ranges and returns a position of the first one that is unequal that doesn't satisfy a binary predicate so it's kind of like diff if you will if you're familiar with the diF tool Well let's start out by looking at for each that's a real cool algorithm so here's a little print funter that records the number of times its operator function call method is invoked and it'll also print the value to the given o stream so you can see here that print is a unary funter it has a constructor that takes an ostream and it staes that ostream。



![](img/8014d5f1512346ad32cbe277c91c93a0_77.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_78.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_79.png)

In a local variable or rather a local data member。

![](img/8014d5f1512346ad32cbe277c91c93a0_81.png)

callled OS underscore and then it also initializes a counter to zero and every time operator subscript is called in that range。

 it increments the count by one and of course it also prints the results to the given out post stream。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_83.png)

Just for kicks we add a little helper method here which is an accessor method called count that returns that count so when we're all dumb you can see how many times that our our operator function call method was actually invoked so here is a little program to illustrate how this works for kicks I have it work on a built-in array it's easy enough to do it with a vector or a list or a deck or anything else。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_85.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_86.png)

So we have a built an array that has a bunch of numbers in it。

 and then we find the end of the array by taking the beginning of the array and then doing some pointer arithmetic to it to figure out how far down it goes。

 And then we call the for each algorithm， which we'll look at in a moment from the beginning of the range up to。

 but not including the end of the range。 And we're going to print in。

 We're going to go ahead and pass in。An anonymous instance of our print。😡，Funter。

Insttaniateated for int with C out as the output we want to write to Now we'll look at that code in a second you'll see what's going to happen is for each is going to return to us the updated fun so this fun is passed by value into the 4 each function it will then be updated by having the operator function call invoked in that range and that will increment the internal count by one and then when we're all done we're going to get back the final version of the fun it comes back as the return parameter and then what we do just to show how this works is we go ahead and print out the number of times that we call the operator function call or rather for each call。

 the operator function call。😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_88.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_89.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_90.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_91.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_92.png)

So let's go ahead and take a look at the for each algorithm as usual it's very simple。

 it's passed in。😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_94.png)

An input iterator to beginning and an input iterator to the one past the end and it's passed in a function and it's a unitary function and as you can see here it just marches down through that range one element at a time calling the function on each element so of course in our code that's going to end up calling back to。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_96.png)

This operator subscript sorry operator function call that's defined on print。😡。

And if you look over here， you can see that when we're all done we return back the value that we were passed in so this is passed in by value。

 the functions passed in by value， it's updated during the iteration through that range and then it's passed back by value to the color where we used it in order to print the number of times we were called So that's for each you might ask yourself why would I ever use for each versus using say a rangebased for loop。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_98.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_99.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_100.png)

Back in the day when we didn't have rangebased for loops for each was pretty useful in now that we have rangebased for loops it's sometimes overkilt to use for each another thing that gets tricky with for each is the fact you can't bail out unless you throw an exception so for my money I typically prefer these days to use for each I'm sorry I use the rangebased for loop and don't use for each that much unless I know I really want to iterate through every element in a range and there's something else I'm doing like applying an adapter or some other STL operation that really requires that type of a way of doing things All right so that's for each that's go ahead and take a look at our last example today。

 this example is going to illustrate a couple of other methods it's going to illustrate the equal method and the mismatch method which are two algorithms that are used to do various things to compare containers or ranges for equality and inequ。



![](img/8014d5f1512346ad32cbe277c91c93a0_102.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_103.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_104.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_105.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_106.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_107.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_108.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_109.png)

Quality and then if it's for inequality to find out where where they differ and we're also going to show the STL distance algorithm as well。

 which is basically just a generalization of the concept of pointer arithmetic and we'll see how that gets used in our example here So take a look down here you can see we've got vector V1 and vector V2 V1 starts out with just a bunch of values 102030 4050。

 and then we make v2 a copy of v1。 So the first thing we're going to do is we're going to call this helper method called find mismatches with the V1 range and the V2 range And I think you would not be surprised to realize that that's going to compare equal because they're the same values So let's go ahead and take a look at find mismatches。



![](img/8014d5f1512346ad32cbe277c91c93a0_111.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_112.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_113.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_114.png)

I should really say find potential mismatches because we may not find any mismatches so here we're going to go ahead and take in。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_116.png)

An iterator range from first to last for the first pair of iterators。😡。



![](img/8014d5f1512346ad32cbe277c91c93a0_118.png)

And then we're also going to take another iterator range from first to last for our second pair of iterators and the reason that we do this the way I do it is because we may have different types for the first iterator range than the second iterator range in the example we're looking at initially they're the same types they're both vectors of ins but down below we're going to generalize that a bit so we need to define different types。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_120.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_121.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_122.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_123.png)

So the first thing we do is we go and we say。😡，Is the size of the first range equal to the size of the second range。

 And if they're not equal， then we probably need to be very careful how we do the rest of the computation。

 because if you're not careful， you can have some problems with other calls。

 But we'll worry about that in a second。 But if they are equal length。

 then we're gonna to go ahead and call the equal algorithm。 And you can see what equal does。

 is equal just goes ahead and I can get it to show up， which it's。

Being ordery at the moment sometimes the sea lion gets confused and doesn't know where it is and how to get access to the code so let's see maybe I can get there another way let's try go to。



![](img/8014d5f1512346ad32cbe277c91c93a0_125.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_126.png)

Definitions there we go all right， so you can see that down here we're going to call equal odds I'm not sure if that's going to work either。



![](img/8014d5f1512346ad32cbe277c91c93a0_128.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_129.png)

C lion again is being。

![](img/8014d5f1512346ad32cbe277c91c93a0_131.png)

Bnerary。Let's see if we can。Force it to go there。 All right， let's try this。 When almost fails。eququ。



![](img/8014d5f1512346ad32cbe277c91c93a0_133.png)

Alls。And we'll see if we can find the one that is doing what we want。



![](img/8014d5f1512346ad32cbe277c91c93a0_135.png)

Oh， one reason why it's doing all these things is it's got all kinds of really cool specialization code in here that's optimized for various use cases and so on。



![](img/8014d5f1512346ad32cbe277c91c93a0_137.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_138.png)

Well， it doesn't look like we're gonna to find it quickly。

 but I think I can assure you that what equal does is it goes through the range from the beginning of the first range and then in parallel goes to the range of the second range and it compares each element one at a time either in a loop or by some kind of magic comparison method that's built into lower level parts of the runtime system and if they're equal in that range refined otherwise it returns false Now the reason why I check the distance first is you can see that equal only takes three parameters it takes the full range for the first element for the first iterator range but only the first iterator for the second range and therefore it darn well better be the same size or the second range needs to be larger than the first range otherwise chaos and insanity will ensue so that's why I go ahead and check the distance up here so let's assume for argument that they're equal because they are equal for the first example。



![](img/8014d5f1512346ad32cbe277c91c93a0_140.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_141.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_142.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_143.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_144.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_145.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_146.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_147.png)

So obviously this will come back and say the ranges are equal。



![](img/8014d5f1512346ad32cbe277c91c93a0_149.png)

Now let's go ahead and take a look at an example where they're deliberately not equal and that'll be more interesting perhaps so in this case we're going to go ahead and define ourselves a native built in array which has values that are clearly different from what's in vector v1 and now we're going to call find mismatches passing in V1 begin to V1 end as the first range which is our vector and that'll have iterators and then we're going to pass in。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_151.png)

A begin to an which are of course the built in types that come as part of the underlying then C type system so those are two different ranges and that's why find mismatches has to be defined with two different sets of templates for the different ranges so now we're going to come in here and it's going to be pretty clear that even though the ranges have the same size they're not equal so let's go ahead and take a look and see where they differ and to do this we're going to use the mismatch algorithm and you can see mismatch maybe we'll get lucky。



![](img/8014d5f1512346ad32cbe277c91c93a0_153.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_154.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_155.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_156.png)

And。You go find mismatch。

![](img/8014d5f1512346ad32cbe277c91c93a0_158.png)

So mismatch also seems to be something that's going to take a lot of find so we'll skip over。

 but basically what it's going to do is it's going to go through those ranges seeing where things stop matching and then it's going to record where they don't match and to to keep track of this stuff what we're going to return here from mismatch is a pair so if I was to go ahead and。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_160.png)

Actually put the real type here instead of using auto you'd see it would be a pair that would be the input iterator for the first range and an input iterator for the second range and that's what comes back from mismatch and so what it'll do is it'll tell you where the first mismatched elements were and in this case you can see it's coming back and saying this is where it mismatched and there is where it mismatched。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_162.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_163.png)

So we already know they're not equal because we compare them for equality up here。

 so we know it's going to find things that don't match。😡。



![](img/8014d5f1512346ad32cbe277c91c93a0_165.png)

Down here just for kicks， we're going to use a predicate comparison instead of just letting it use the builtin equal operator and in this case you can do a sort of arbitrary things I'm going to go ahead and call mismatch again and in this case I'm going to pass in the predicate now my particular predicate is going to be done。

😡。

![](img/8014d5f1512346ad32cbe277c91c93a0_167.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_168.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_169.png)

F a generic。Land function。

![](img/8014d5f1512346ad32cbe277c91c93a0_171.png)

And all it does is just check for quality so I don't have to do anything super special I'm just showing you that you can use predants in this case and that'll go ahead and show us the next place that things mismatch and let me show you what I did by the way what I did was kind of clever here I looked for the first mismatch and I get back a pair that tells me where the matches the mismatches occurred and then notice I pass that pair of iterators into mismatch for the second time so that'll go then and find the next place in that range that they don't match and I evoke that behavior by incrementing this by one in fact I probably could have done this and it might have been a little bit more clear what was going on so there I'm starting by passing in I'm skipping over the place where it didn't match and we'll start looking again at the next location。



![](img/8014d5f1512346ad32cbe277c91c93a0_173.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_174.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_175.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_176.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_177.png)

So let's run this code and we'll see what the results are。😡。



![](img/8014d5f1512346ad32cbe277c91c93a0_179.png)

And you can see here that here's the original input just for comparison。

 you can see that the ranges were equal when we compared the vectors to each other。

 no real surprise because they were a copy and then when we had two different ranges with different values。

 10，20， 30， 40， 50 and 10， 40， 60， 80， 100， you can see that in that case it tells you where the first mismatch occurred which here is at the second element 20 and 40 and then we went ahead and looked again and it came back and said aha。

 there's some other things missing at elements 30 and 60。😡。



![](img/8014d5f1512346ad32cbe277c91c93a0_181.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_182.png)

![](img/8014d5f1512346ad32cbe277c91c93a0_183.png)

So these are the examples that I wanted to show you today there's a couple other very interesting non-mutating algorithms that we still have to look at including search and search end and then we're also going to compare search end against adjacent find which is yet another way of doing a find that looks for elements that are consecutively next to each other in a range and if I get particularly ambitious when we may also get a chance to take a look at a binary search example as well so that'll round out our our non-mutating algorithms we're going to wrap that up tomorrow and then after that we'll start looking at the various mutating algorithms of which of course there are quite a lot so thanks very much for joining if you enjoyed the content please like and subscribe and I look forward to seeing you again soon。

😡。