# 【全集】范德堡大学 C++标准模板库 中英字幕 1080P p15 Lecture 15 - 迭代器适配器 part2 -BV1KWiCBWE7M_p15-

Hello and welcome to the next session in my webinar series on C++ Standard Template Library by example。

Today we're going to continue our discussion of iterator adapters we started yesterday and now we're going to focus on the so-called stream adapters that allow IO stream objects to be integrated seamlessly into various STLL algorithms making them work and then feel like they're iterators so without further ado let me go ahead and share my screen and we'll look at the place to get the code and then we'll jump right into the discussion of the examples。

So the day's source code can be found in my GitHub repository in the C++ STL S-066。5 subfolder。

 and you can see we have a number of different examples that we'll look at here。



![](img/6db8f2471826fc6bae54a3b911133c48_1.png)

Let's start by looking at the first example。

![](img/6db8f2471826fc6bae54a3b911133c48_3.png)

This example is going to demonstrate the use of I stream and O stream adapters。

 so the purpose of this is rather than having to explicitly extract and insert data in from IO streamams。

From the streams that are used directly， instead what we're going to use is we're going to use stream adapters or iterator adapters to make the streams appear as if they're STL containers。

And then we use the copy algorithm to manage the process of building the container。

 which in our example， just for kicks， we're going to sort。😡。

There are three types of stream adapters， I stream adapters。

 O stream adapters and stream buffer adapters this particular example is just going to focus on ice stream and O stream adapters。



![](img/6db8f2471826fc6bae54a3b911133c48_5.png)

So here's the example you can see we're going to make ourselves an empty list of strings called My list。

 and then we're going to apply the ISt iterator adapter to take the CN ISt and then go ahead and pull the data in as basically an iterator and input iterator as strings and we're going to keep going until we reach the end and every step along the way we're going to go ahead and insert the item that we read in the string that we got in from the standard input to an output iterator using the inserter adapter。

 the inserter iterator adapter that we talked about yesterday。

 and the way this is going to work is it's essentially a back inserter。

 we're just doing it this way for kicks， we're getting it the My list container which is the list and then we're telling it to put it at the end of that particular container。



![](img/6db8f2471826fc6bae54a3b911133c48_7.png)

Let's just take a quick look at the eyestream iterator。Stream adapter。

 you can see here that there's a couple of methods that matter here， one is this constructor。

 which is what we're using to initialize the first input iterator with and what we're doing is we're passing in an icestream object by reference and that's then being stashed away as a icestream pointer。



![](img/6db8f2471826fc6bae54a3b911133c48_9.png)

![](img/6db8f2471826fc6bae54a3b911133c48_10.png)

And then we go ahead and kind of kick things off and read some data in just to start things up you'll notice the second Istream iterator adapter that we're using is indicating end of file and so it just sets a value of zero or a null pointer here。



![](img/6db8f2471826fc6bae54a3b911133c48_12.png)

![](img/6db8f2471826fc6bae54a3b911133c48_13.png)

So that's the way we're going to know that we're done。

And then if you take a look at the various methods down here， you can see， for example。

 that we've got the the star method， which doesn't do anything we have the。



![](img/6db8f2471826fc6bae54a3b911133c48_15.png)

![](img/6db8f2471826fc6bae54a3b911133c48_16.png)

Other methods that don't really do anything but here's one that actually does something that plus plus operation goes ahead and will read in from the screen that we've encapsulated here into a value at returning this and the same thing for this post increment operation plus plus and so on and so forth so this is basically going to be used to pull the data in from the container that we've wrapped by the adapter。



![](img/6db8f2471826fc6bae54a3b911133c48_18.png)

![](img/6db8f2471826fc6bae54a3b911133c48_19.png)

![](img/6db8f2471826fc6bae54a3b911133c48_20.png)

So here's how it gets used of course we're going to read this thing in and remember we're just using the good old copy algorithm we've seen this at gazillion times now and it's just going to go ahead and read from the beginning of that sequence to the end and every step along the way it's going to go ahead and insert it using this inserter。

 which works like a back inserter。After we're done。

 we're going to go ahead and take the list and we're going to sort it。

 note that a list is actually a bidirectional iterator style container。

 and so as a result we can't use the sort algorithm that expects to work on random access iterators。

 but instead we're going to use the sort method which works on in this case the bidirectional iterator list is actually part of the class itself。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_22.png)

And then the final thing we're going to do we're going to start at the beginning of the list and we're going to iterate from beginning to end and we're going to copy it to the O streamam iterator and that's kind of the other end of this thing here's the OSt iterator you can see that in this case we gave it an O stream iterator that was an O stream and a con carestar delimiter。

 which in this case was the new line。😡。

![](img/6db8f2471826fc6bae54a3b911133c48_24.png)

![](img/6db8f2471826fc6bae54a3b911133c48_25.png)

And then this assignment operator that you see here。

 the assignment operator is the thing that triggers this because it's working as an o stream sorry it's working as an output iter so we want to write to it and what's happening is it takes the value that's coming through here from the list and it's going ahead and it's basically inserting that into the O stream that we tucked away in this constructor up here and if there was a delimiter that was given。

 we go ahead and write the delimiter out after we've we've basically inserted the value into the captured O stream。

So that's basically how the logic works here under the hood。

 you can see these are all value semantics， they're passing these things around and they're storing the reference or actually the pointer to the O stream as a pointer。

 but it comes in as a reference。

![](img/6db8f2471826fc6bae54a3b911133c48_27.png)

![](img/6db8f2471826fc6bae54a3b911133c48_28.png)

Okay， so going back over here， let's now run our program。😡。



![](img/6db8f2471826fc6bae54a3b911133c48_30.png)

And the program is going to say now is the time for all good people to come to the aid of their party and let's give that an exclamation point。

And now we go ahead and end that input， and you can see that I went ahead and sorted it after I got it。

 so it comes out in sorted order in as sendingending sorted order。

So that was the first example I wanted to show you。

 this is just showing the Istream and OSt stream adapters and how easy they are to integrate with STL algorithms like copy in conjunction with other things like Iner adapters or back Iner adapters and so on and so forth。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_32.png)

Let's now go ahead and take a look at the next example。



![](img/6db8f2471826fc6bae54a3b911133c48_34.png)

Six do。5。 B。So this example is going to further demonstrate some of the concepts we've been talking about and it's going to use the class template ISt iterator to create elements from an input stream using the operator that's the extraction operator and we're going to get the value of T and then we're going to store it when the iterator is constructed and each time operator plus plus is called。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_36.png)

The iterator here is equal to the end of stream iterator value if the end of file is reached and that's done by having this constructor with no arguments which is used to kind of be an indicator or a flag that we at the end of the stream the only value valid use of this no parameter version of the Istream iterator is to compare to other iterators when checking for end of file as usual dont don't attempt to dereference this thing you'll get gobbledy G the technical term meaning that it won't be a meaningful value this is just a problem or'm not a problem。

 this is the characteristic the behavior or the semantics of the end method for all iterators return from containers by the end method。



![](img/6db8f2471826fc6bae54a3b911133c48_38.png)

Since an icestream iterator is an input iterator， you can't assign to the value returned by dereencing it。

 it's a read only like model， and this means that I stream iterators can only be used for single pass algorithms as we can't assign to them。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_40.png)

![](img/6db8f2471826fc6bae54a3b911133c48_41.png)

Let's go ahead and take a look at this， we make ourselves a vector。And。Let's see， oops。

We make ourselves a vector here and this is going to then be empty initially we go ahead and make ourselves。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_43.png)

An I stream iterator adapter called I Iter and an O stream iterator adapter called OS Iter。



![](img/6db8f2471826fc6bae54a3b911133c48_45.png)

And we then define ourselves another vector V， and then we have a value type sum here。

 and I don't necessarily have to do it that way， I could also have said auto sum equals zero。

 that would also work if I gave it a different name than sum of course。

 but let's use this one just for kidss。😡。

![](img/6db8f2471826fc6bae54a3b911133c48_47.png)

So what we're going to do now is we're going to prompt to enter a sequence of integers with an end of file to quit。

 and you can see what we're going to do here is we're going to read from the input stream iterator adapter from CN to the end of this thing。



![](img/6db8f2471826fc6bae54a3b911133c48_49.png)

And we're going to do a back insert of each element。

And then what we're going to do is we're going to take this and we're going to go from beginning to almost the very end。

 and we're going to go ahead and write the results to the output stream iterator。😡。

And notice the main difference between this and the previous example as we defined explicit instances of ISt iterator and OSt iterator。

 we made these as basically local variables as opposed to doing it implicitly by having anonymous objects created。



![](img/6db8f2471826fc6bae54a3b911133c48_51.png)

![](img/6db8f2471826fc6bae54a3b911133c48_52.png)

![](img/6db8f2471826fc6bae54a3b911133c48_53.png)

Works pretty much the same， this arguably is a little bit more concise maybe depending on your point of view。



![](img/6db8f2471826fc6bae54a3b911133c48_55.png)

And then what we're going to do here is since we stopped before we got to the very last element in our copy。

 then what we're going to do is， you know assuming that we're not at the end。

 what we're going to do is we're going to go ahead and print the last element。😡。

And then we're going to say what the accumulated sum is of that value。

 and you can see here the sum is defined up there。😡。



![](img/6db8f2471826fc6bae54a3b911133c48_57.png)

Iues if I was really being conscientious， I would probably move this。Closer to where it's being used。

And I go ahead and I write out the results here， and this will go ahead and accumulate the elements in the vector from beginning to end and print out the sum。

😡，So let's go ahead and run this。😡，And it prompts us for some input， so let's say 10， 20， 30， 40， 50。

 60。And then let's give it the end of file character and you can see what it does is it prints 10。

 20， 30， 40， 50。And then it goes ahead， as you can see here and it。Printnce the last element。

 v dot back， that's the last element in the vector。

 and then it goes ahead and calls accumulate which totals up the contents that's in that particular vector and prints the results。

😡，So this is also giving us a chance to kind of showcase the accumulate method that of course is a standard STL algorithm and you can see all it's doing here is it gets an initial value here and this of course is a template that's parameterized by an input iterator and。



![](img/6db8f2471826fc6bae54a3b911133c48_59.png)

![](img/6db8f2471826fc6bae54a3b911133c48_60.png)

Class which is going to be the thing that's used to total it and we go through the range from first to last as we always do and every step along the way we basically increment the count of ait which as we saw here would start out as zero and we add to it what was ever in the container at that point and we just keep a running score of that or running some of that and then when we're all done we can just return that as the result of accumulate so that's illustrating how accumulate works you'll notice that accumulate comes out of the numeric header file。

So that's the second example I wanted to show you this kind of illustrates a couple cool things it illustrates how you can make explicit instances of ISt iterators and OSt iterators and how you can then do copy where you don't go the whole way and then how you can go ahead and use the operations here to accumulate the information and print the results out。



![](img/6db8f2471826fc6bae54a3b911133c48_62.png)

![](img/6db8f2471826fc6bae54a3b911133c48_63.png)

![](img/6db8f2471826fc6bae54a3b911133c48_64.png)

Okay， and oh， I can see that Cang is telling us let's use empty， not size equals zero。

 so I think that's probably a good suggestion to make the code a bit more understandable。😊。



![](img/6db8f2471826fc6bae54a3b911133c48_66.png)

All right， next thing， let's go ahead and take a look at。Six。5 C。



![](img/6db8f2471826fc6bae54a3b911133c48_68.png)

So as we've seen before there's I stream iterator adapters， there's OSt iterator adapters。

 and the I stream iterator adapters as you saw are used to basically read the values where the O stream are used to write the values so they're used as output iterators with the ISt iterator adapters are used as input iterators。

And as you can see here， they changed the assignment of a new value to be an output operation by using the insertion operation。

 the less than less than operation。

![](img/6db8f2471826fc6bae54a3b911133c48_70.png)

As you can see here， when you we create an O stream iterator。

 you have to provide it with an output stream like C out or C error。

 an optional that you can also provide it with a character string that can be used to separate the values being passed when you write them to the output stream。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_72.png)

So here's what we're going to do， we're going to go ahead and make ourselves a an ostream iterator we call Oi。

OI， and then we go ahead and we assign six to this and 88 to this。

So remember the star and the plus plus here are just syntactic sugar。

 what really matters is this assignment operator。😡。



![](img/6db8f2471826fc6bae54a3b911133c48_74.png)

And here we go， this is the assignment operator for the O stream iterator adapter as you can see it's going to take the value and it's going to basically insert it to the output stream which was stashed away when we created the instance of that O using this constructor here and then if there's a delimmerer we go ahead and write that out as well so that's what happens with the assignments here。



![](img/6db8f2471826fc6bae54a3b911133c48_76.png)

![](img/6db8f2471826fc6bae54a3b911133c48_77.png)

Then what we're going to do is we're going to go ahead and create a deck that has the values three。

 four， seven， and eight。And much like we did before。

 just kind of illustrating we can use decks as opposed to lists or vectors。

 we're going to go ahead and copy the contents。Of this deck。

From beginning to up to but not quite including the last one we stop one before the end and that's going to get written to the the O stream iterator adapter in this case we're going to put a plus between each of these things and then when we get to the end the last one we're going to go ahead and say。

😡，D dot n minus one， so we're going to go ahead and go back one and we're going to print the result there so that's going to be the last element there and we could probably just have said you know D dot back in fact that's a good question let's see if we can say。

😡，D dot back。Yeah。Oops be helpful if I didn't give it a syntax error here。

 so we could also say D dot back that's the last element。

 but if we want to be even more obscure we can say D dot n minus one which is the last element and then dereence it and then again we go ahead and use the accumulate algorithm we did before except now we're working on a deck as opposed to the other data types we worked on before。



![](img/6db8f2471826fc6bae54a3b911133c48_79.png)

Okay， so let's go ahead and run this and see what we get as output so you can see that the first thing we do and I probably should put a new line here just because it's kind of a different。

Output， let's go ahead and do that and then rerun it。



![](img/6db8f2471826fc6bae54a3b911133c48_81.png)

So now you can see that we start out by making an O stream iterator that's going to write the standard output with a space between each of the elements and then we write six and eight to that so we go ahead and。

P those things out into the O stream as if we're doing pointer arithmetic which is kind of cool and then we go ahead and we write out the contents of the accumulated deck and we add up the results of the value。



![](img/6db8f2471826fc6bae54a3b911133c48_83.png)

So that's illustrating yet more features， this is kind of focusing on the O stream part as well as of course also using the icestream part。

So now let's go ahead and take a look at our。Final example here I。



![](img/6db8f2471826fc6bae54a3b911133c48_85.png)

Get the thing to open。Let's say 65 D， that's the one we want。



![](img/6db8f2471826fc6bae54a3b911133c48_87.png)

And this is a really interesting one， this one this is yet another kind of stream iterator adapter。

 remember we've already talked about the I stream iterator adapter。

 we've talked about the O stream iterator adapter now we're going to talk about the stream buffer iterator adapter。

😡，And you'll see that there's a couple of variants of that， there's ice cream Buff iterator。

for reading an O stream Buff iterator for writing to streams and these template class objects can be used to read or write individual characters from our two basic streambuff objects。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_89.png)

And so this is just a really， really fun example， I think I'm going to to show it to you and then we'll kind of talk about it because it's pretty crazy。



![](img/6db8f2471826fc6bae54a3b911133c48_91.png)

In fact， let me tell you what， let me go ahead and run it first and then I'll show it to you。

So here's what we get is the output it says here is a sample sentence for output I hope you like this sentence out there perhaps not the most profound。

Bit of prose in the English language ever written， but it gets the point across I should probably put some Shakespeare in here to make it better。

So here's what we're going to do first thing we're going to do is we're going to open up a temp file name using the muchbl temp name method which has been deprecated I just haven't had a chance to rewrite this to use make S tempemp but this is just a simple example so don't write code like this in production code I'm just trying to make a temporary file name for the purposes of getting this program to run then what I do is I take that temporary file name and I go ahead and create myself an O stream which I call out and I'm going to open it for reading and writing and also truncate which means it's going to start being empty even if there's something already in it。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_93.png)

And then what I do is I go ahead and I output to the OF stream I'm writing to that file right so this isnt a file stream an output file stream I write to the file。

 here's a sample sentence for output， I hope you like the sentence out there。😡，Again。

 not the most profound thing ever written。What I do now is I go ahead and take so keep in mind that's been written to a file right so what I do now is I go ahead and I seek put the seek pointer to the beginning of the file at the moment it's at the end of the file because I just kept done writing to it now I move it back to the beginning。

😡，And then what I'm going to do is this is really cool I'm going to construct myself an eye stream buff iterator and I'm going to give it the read buffer to that file。

 so remember I wrote to the file I moved the seek pointer to the beginning of the file and now I'm going to get a read buffer to that particular。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_95.png)

Content here is a sample sentence for output that that string that's in the file。

 and I'm going to connect it to an eyestream buff iterator so this is going to read this from a buffer that's associated with the file。

😡。

![](img/6db8f2471826fc6bae54a3b911133c48_97.png)

And then I'm going to go ahead and create an icestream Buff iterator which will represent the end of the file。

 and then while I'm reading from the beginning to the end。

 it's going to read the contents out basically a character at a time。

 the file will be read a character at a time and every step along the way。

 I go ahead and write the contents and then I increment it by one。😡。

And so this is going to basically iterate through that file one element at a time and let's see if we can make this work or not。



![](img/6db8f2471826fc6bae54a3b911133c48_99.png)

So you can see here what we're doing and it's it's pretty low level。

 but these are the construct these are the constructor that we use to create this we stashed the。



![](img/6db8f2471826fc6bae54a3b911133c48_101.png)

![](img/6db8f2471826fc6bae54a3b911133c48_102.png)

The read buffer in here， we give it the buffer and then here's the plus plus operation that we're using here。

 which is going ahead and basically advancing it by one。



![](img/6db8f2471826fc6bae54a3b911133c48_104.png)

Another way to do this， which I think is arguably even better is to use the copy algorithm。😡。

And write the code like this， so here's the copy algorithm。This is a little bit。Foratted。

 but we can fix that。So you can see here that we're going to start with an anonymous instance of the ISt Buff iterator。

 that's the input iterator， the first input iterator， as usual go to the last。

 which is just this No op constructor for ISt Buff iterator。

 and then we're going to write this thing to an O stream iterator， not an OSt Buff iterator。

 but to an OSt iterator， so it's going to write the standard standard output。😡。



![](img/6db8f2471826fc6bae54a3b911133c48_106.png)

And when we run this thing， as you can see， when we ran it。

 it went ahead and took the contents of the file， which is what we gave it here。

 and then it wrote the contents of the file character by character to the standard output。😡。

And again， I think if we run it this way， we should probably get this thing appearing twice。



![](img/6db8f2471826fc6bae54a3b911133c48_108.png)

I think it back just shows up once although that I know why because we didn't reance this thing。

 so we got everything that was underneath it let's go ahead and do this let's say。



![](img/6db8f2471826fc6bae54a3b911133c48_110.png)

啊。If zero。And we'll get rid of this guy。Actually if。And then let's go ahead and try to run this。

And as you can see it gives us the same result as before。

 which is what we want so either of those approaches are work fine this approach is arguably more concise this approach is to showing you the elements one at a time and then when we're all done we go ahead and remove the temp file because we don't need it anymore and that will clean everything up since it's a temp file。



![](img/6db8f2471826fc6bae54a3b911133c48_112.png)

So that was the last example that I wanted to show today this particular。



![](img/6db8f2471826fc6bae54a3b911133c48_114.png)

Set of examples here was just illustrating the stream adapters。

 Istream OSt and stream buffer adapters and you can see that they're actually very useful I've been using them quite a bit kind of as a debugging tool when I want to print the contents of containers out and I don't want to have to write special print functions and so on I just use copy and then I use the OSt adapter to write to the output usually to see out so very useful little tools showing once again the orthogonal concepts of STL where you can kind of mix and match things and you can adapt stuff and even though we've looked at these examples earlier in other context I wanted to kind of walk through it systematically to show you how the Istream adapter I stream iterator adapter。

 OSt iterator adapter and Istream buff iterator adapter and OSt Buff iterator adapter can be used。

So if you like this video， please go ahead and give it a like and subscribe and feel free to follow me on Twitter。

