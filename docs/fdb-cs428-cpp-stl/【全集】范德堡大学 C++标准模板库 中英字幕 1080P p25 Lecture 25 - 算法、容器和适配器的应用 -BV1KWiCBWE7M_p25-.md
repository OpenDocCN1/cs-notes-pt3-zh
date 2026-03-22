# 【全集】范德堡大学 C++标准模板库 中英字幕 1080P p25 Lecture 25 - 算法、容器和适配器的应用 -BV1KWiCBWE7M_p25-

Hello and welcome to the next session in my webinar series on C++ Standard Tempite Library by example。

😡，Today we're going to change gears a little bit， and instead of looking at specific C++ STL features or containers or algorithms and so on。

 we're going to show an example that illustrates how to apply various C++ STL algorithms and various features in the context of a program that will look for conflicts in meeting schedules。

 and it'll also go ahead and print out a schedule that's sorted by the date and time of the meetings。

😡，So without any further ado， let me share my screen and we'll start taking a look at the code。😡。

So as always， you can find the source code in my GitHub repository。😡。

And this is in the C++ meeting dash Schr subfolder and all the files we're about to look at can be found there。



![](img/d0a7ff755611e40bbce27dc51146699e_1.png)

So now let's go ahead and move over to my Sea lion IDdeE。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_3.png)

And you'll you'll see this is the main dot cppP file and we're going to spend a bunch of time in this in a second。

 but before we do anything looking at the code I actually want to show you how the program works and then we'll take a look at the code because I think it'll make more sense so let me go ahead and open up my shell here and。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_5.png)

![](img/d0a7ff755611e40bbce27dc51146699e_6.png)

I'm going to show you what's in the file so what's actually in the file。

 this is the file itself and you can see it has a list of classes。

 those are our meetings that we're gonna to schedule my classes I teach and we're going to have the class number like CS101 or CS251 we have the days of the week when they're taught which would be M for Monday and W for Wednesday and F for Friday and so on and then we're also going to have the times when they start and the times are going to be given in 24 hour time so for example CS101 is taught on Wednesdays from 1730 to 2030 which is 530 to 830 and likewise CS242 is taught a couple of different times and what we're going to do here is we're going to run a program that's going to check to see if there's any conflicts in the schedule and a conflict occurs if you have two classes that are taught on the same day at over。

So let's assume for whatever reason that we only have one classroom and so we have to be careful how we schedule things。

So let me go ahead and run the program I'm going to run this program which has all the various rows with each of the classes in their days and times and I'm going to go ahead and pipe it through the XArgs program and XAGs is a program that's going to take the argument here which is the program that we're going to run the meeting schedule program and it's going to convert the contents of the file into ArgV ArgC command line parameters and that's what the program is actually going to use in order to do its processing so let's go ahead and run it and you can see here that we've got a couple of conflicts CS251 and CS242 have overlapping times on Tuesdays and we also see CS242 and CS281 also have conflicting overlapping times also on Tuesday so these are examples of conflicts and then what happens down below is it goes ahead and it prints a schedule from Monday through。



![](img/d0a7ff755611e40bbce27dc51146699e_8.png)

![](img/d0a7ff755611e40bbce27dc51146699e_9.png)

C Thursday with all the times of each class starting and finishing。Okay。

 so that's what the program is going to do， so let's go ahead and return back to the code and talk about how it works。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_11.png)

So here's the main function， as it can see in the comments。

 it reads a list of meeting times and dates that are provided as AGC AGV command line parameters to the program as we just saw。

 and then it goes ahead and it detects and prints any conflicts situations where there's overlaps as we just saw and finally it's going to write the sorted schedule to the output。

😡，All right， so let's go ahead and see how we do this and I'll walk through the whole program at a high level first and then we'll dive down into each of the parts。

😡，We're going to store the actual meeting schedule in a vector so it's going to be a vector of meetings and we'll talk more about what a meeting is in a second。

 but for right now just to keep things moving a meeting is a struct that's going to keep track of the name of the meeting。

 the day of the meeting and the start time and finish time of the meeting and we'll come back and look at that in a second。

😡，So then what we're going to do is we're going to take the contents we get as Arg C。

 AV parameters to main， and we're going to use a really cool custom iterator adapter that I wrote called an ArgV iterator and what ArgV iterator does it' going to treat Arg C ArgV。

😡，Input to be converted into an iterator format and by doing this we're going to be able to read the command line parameters that are passed in as Argvrgc and then use them in the standard copy algorithm so we're going be able to use the Argv iterator adapter much like we've used stuff like Istream iterator adapter in previous examples and we're going to be able to read from the command lines and then take the contents that come in in the Argv parameters convert them into meeting objects and then insert them at the end of the schedule so you can see here we're going to use back inserter as the output iterator to adapt the schedule vector into something that could be treated as an output iterator so we'll take a look take a closer look at Argv iterator adapter in just a second but this is kind of at a high level we're reading from the command line parameters and sticking things at the end of the vector and notice the cool use of STL adapters to make all this very seamless。

And allow us to reuse code like the copy algorithm。After we've done this。

 we go ahead and we sort the contents of the vector from beginning to end。

 that's just the good old sort algorithm， I perhaps could have stored the meeting contents into a set and then I wouldn't have had to have sorted it。

 but this works just as well。😡，The next thing I do and this is really the fun part of the program when we get to this a little bit later。

 I call a helper method called check for conflicts and I give it the beginning of the schedule and the end of the schedule now keep in mind the schedule is now sorted。

😡，And it's sorted in such a way where it'll be sorted so that each day will be sorted by Monday。

 Tuesday， Wednesday， Thursday， Friday and so on， and then within each day it'll be sorted using the less than operation on a meeting object。

 which is used to make sure that things show up in the right order when you sort them。😡。

We'll talk more about that in a second so then I go ahead and call check for conflicts on the sorted schedule and it will go through and use a couple of different techniques to find out where there are conflicts and you'll see we're going to use two different approaches one is based on the C+ plus adjacent find algorithm and the other is based on the C+ plus STL transform algorithm and we'll compare the pros and cons of each approach shortly。

😡，When we're all done， we will have printed out any conflicts if they exist and then we're just going to dump the schedule from beginning to end in sorted order and we'll use the C begin and CN method on schedule。

 which return constant iterators because we're just reading the elements and then we're going to go ahead and use the O stream iterator adapter to write the output to the standard output。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_13.png)

![](img/d0a7ff755611e40bbce27dc51146699e_14.png)

All right so that's a high level view of what's going on now let's kind of dive down into each of the piece parts we'll start by taking a look at the ArgV iterator and I'm particularly proud of this clever little class because it's a great example of how you can use adapters to great effect with STL algorithms so we take something that wasn't meant to be used with the copy algorithm namely ArgV ArgC and we convert it into something that works quite nicely that way。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_16.png)

So ArgV iterator is a template class that's parameterized by type T in our case we're going to be creating meeting objects out of the contents of A V and A C and it inhers from iterator and in fact is a forward iterator。

 so that's the forward iterator tag it only go in one direction from left to right。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_18.png)

We have a default constructor that gives everybody either zeros or nulls。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_20.png)

And I guess if I was really being smart， I would use null pointer。

 I can see the compiler is yelling at me to use null pointer because that's the c+ plus 11 in way of doing things。

 so I will respect c+ plus 11 in ways of doing things in this regard。



![](img/d0a7ff755611e40bbce27dc51146699e_22.png)

Down here， I have the constructor that we're actually using along with a copy algorithm and we give it Argc and Argv。

 Now if you go take a look at the way it's called here。

 we pass Argc minus1 Argc is the count of the number of parameters that are passed on the command line and we do this because of course we want to skip over the first parameter which is the name of the program itself so we don't need to include that so we're going to be Argc minus1 and likewise we're going to be Argv plus one where Argv is going to be the pointer to an array of strings。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_24.png)

And we're going skip over the first element because that's the name of the program so we start out by incrementing ArgV and decrementing ArgC and that's what we're passing into this constructor here and then what we do is we stash those values away in local data members so ArgC underscore gets set to AGC Argv underscore gets set to ArgV base ArgV gets set to Argv and stays there whereas we'll see that the AV underscore gets incremented and it's going to get incremented by the count that's passed in here。

😡，And if you look at the main program， you can see the count is four。

 and that's because if you go look at the input file。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_26.png)

Which whoops we had shown earlier here the input file that we had had four columns for each row and these four columns of course are going to correspond to the state that we want to use to initialize our meeting object so that's why we're gonna skip over for every time we do an increment so let's go ahead and see how the actual iterator works I only implement a few of the iterator methods just the ones I need to get the job done I implement the not equal iterator and that's used to see if we've reached the end and we know we've reached the end when the arg V underscore pointer is going to be equal to base arg v plus arg C so that means we've gone through all the elements that we're iterating over。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_28.png)

![](img/d0a7ff755611e40bbce27dc51146699e_29.png)

![](img/d0a7ff755611e40bbce27dc51146699e_30.png)

![](img/d0a7ff755611e40bbce27dc51146699e_31.png)

The dereference operation， which is what you use when you want to read the contents that is going to simply take whatever ArgV points to。

 which remember that's a carestar star or it's an array of characters and it goes ahead and it will convert that into an instance of whatever whatever parameterized type has been given to the ArgV iterator template now in our particular case that's going to be the meeting and in fact if you go back here you'll see that we expect there's a constructor for meeting that takes a carestar star and in fact if we go over here and look at the constructor we will see that there is indeed a constructor for meeting that takes a carestar star and we'll take a look at how that works in a second。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_33.png)

![](img/d0a7ff755611e40bbce27dc51146699e_34.png)

![](img/d0a7ff755611e40bbce27dc51146699e_35.png)

![](img/d0a7ff755611e40bbce27dc51146699e_36.png)

All right， so then down here we have the overloaded operator plus plus this is the pre。😡。

Increment version and it will skip over the ArgV parameters by the increment designated in the constructor in our case it's four and that's because there's four columns per row that are used to initialize each meeting object。

 namely the title the day of the week as a character and then the start time and the finish time。😡。

All right， so that's basically what we got here you can see just down there we have arg C and underscore and argv underscore and base argv underscore and increment so that's our very very clever Argv iterator and I think that gets used a nice effect here to kind of make everything hold together in the context of。

😡，STL and its algorithms。

![](img/d0a7ff755611e40bbce27dc51146699e_38.png)

Let's now go ahead and take a look at the meeting。😡。

Class orstruct in this case and this is basically the data structure we're going to use to store information about each meeting。

 including its title， its day of the week and its start time and finish time。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_40.png)

So to make this easy， we're going to have an enumerated type called day of week with a bunch of enumerated literals corresponding to each day。

 we have a little factory method that takes a character and returns the corresponding enumerated type。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_42.png)

We have that constructor I just showed you that takes a Carestar star and we' convert that into a meeting object and we've got relational operators。

 the less than operators used by the sort algorithm and then the equality operator is used in a very。

 very clever way by the check for conflicts method and we'll see how that gets used in a second。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_44.png)

![](img/d0a7ff755611e40bbce27dc51146699e_45.png)

And then the other elements are just what you'd expect there。The title， in other words。

 the name of the meeting， the day of the week and the start time and the end time。

And we're using the syntax here that says initialize this to its default value。

 so we don't have to remember to do it in the constructor。



![](img/d0a7ff755611e40bbce27dc51146699e_47.png)

Let's now go ahead and take a look at the implementation of the meeting class。

 you can see here's the one that takes the carestar star so that's what gets called by the。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_49.png)

Ag the iterator， if you recall right here， operator， the reference will go ahead and create this。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_51.png)

Object using this constructor and what it does is really quite cool it takes Argv and says Argv sub0ro is the string that corresponds to the name of the meeting which for example would be something like CS101 in our case and then it takes in Argv sub1 and takes the character there which is going of course to be the day of the week and you can see here that that could be W or T or R for Thursday and W for Wednesday and so on and then then we go into the body of the constructor and here we're going convert the string parameters that come in from Argv ArgC which namely are things like 1730 and 1130 and 1430 and so on we're going convert those into the corresponding numbers and the way we do that is by using a string string so we create a string stream a1 which is Argv sub2 and then we make a。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_53.png)

![](img/d0a7ff755611e40bbce27dc51146699e_54.png)

![](img/d0a7ff755611e40bbce27dc51146699e_55.png)

![](img/d0a7ff755611e40bbce27dc51146699e_56.png)

![](img/d0a7ff755611e40bbce27dc51146699e_57.png)

![](img/d0a7ff755611e40bbce27dc51146699e_58.png)

![](img/d0a7ff755611e40bbce27dc51146699e_59.png)

Stream stream A2， which is RV sub3 and then we go ahead and use the extraction operator to go ahead and put the contents of the stream into the start time into the finish time so that's a little cleaner than using something like A to I which is all full of weird problems if you give it the wrong kind of input。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_61.png)

Okay， so that's the constructor that takes a Carestar star and converts that into a meeting。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_63.png)

Down here we have the method that takes a character and converts it into the appropriate enumerated literal。

 does exactly what you think it does， it does a switch statement and then returns the right literal。

Here is the operator equality and this is used by the adjacent find algorithm and also by transform depending on which version you use in order to be able to detect overlaps in meeting times and here's how it works let's give an example of a conflict that I showed you before here's CS242 and CS281 they both appear on Tuesday and CS242 starts at 1230 and goes to 1430 CS281 starts at 1300 and goes to 1430 and you can see here they both have the same day the start time for CS242 is indeed less than the start time for CS281 however the start time for CS281 is less than the finish time for CS242 so that's an indication that there's an overlap and a conflict and so that will return true even though they don't actually have exactly the same value they have the overlap and that's。

😡，It makes them equal。

![](img/d0a7ff755611e40bbce27dc51146699e_65.png)

And then there's some other checks we could do for other cases that are also indiia of overlaps。



![](img/d0a7ff755611e40bbce27dc51146699e_67.png)

Down here is the lesson operator， this of course， is what's going to be used by the sort algorithm in order to be able to order the meetings in the correct order by day and by time within the day。

 so that goes ahead and does this。😡。

![](img/d0a7ff755611e40bbce27dc51146699e_69.png)

and then the last thing we have here is the insertion operation that takes the output of a meeting and writes it into the given O string and again it just formats it in a nice way。

😡，Okay， so that's the meeting class， let's now go back to the main class。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_71.png)

the main method and we'll find the last thing to talk about and this is really the fun part because this is what's going to show off some of these other cool STI algorithms that we've been talking about and some that we will talk further about in later parts of the course。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_73.png)

![](img/d0a7ff755611e40bbce27dc51146699e_74.png)

So the method is called check for conflicts， just for generality I made it be a generic method。

 so it's parameterized by the input iterator and in this case the input iterator is going to be the beginning of the schedule vector and the end of the schedule vector so we're going to check for conflicts in our schedule。

😡，Now I've got two versions here。 The first one， which I've got enabled at the moment。

 is going to check for conflicts using the adjacent find algorithm。

 And we've talked about adjacent find。 the way it works is you give it a range from beginning to end of iterators and it will return an iterator to the first element in that range where two adjacent elements have the same value。

 So of course， in this case， we're going to be using the。😡。



![](img/d0a7ff755611e40bbce27dc51146699e_76.png)

qual equalal operation on meeting to find out if there's conflicts so we're basically doing this to check for conflicts and here's how it works we start out by making a kind of a temp iterator called iter and we start at the beginning we keep going while we haven't reached the end and every time through this loop we use adjacent find starting at the current value of the iterator which initially is at the beginning and then going to the end and we'll get back an updated iterator and if that iterator equals end it means there were no values in that range that were equal when they were adjacent but if we do get a hit and it's not the end we know we found a conflict so we print out conflict in big capital letters and we say iter sub0ro and it sub1 and those are the two values that are adjacent to each other from the point of view of the iterator。

😡，And then in this case， we increment the iterator by one so we can skip over the one we just found the match on and then start comparing at the next element to see if there's a match there。

😡，So this will could potentially iterate and find multiple matches and that's why we use a loop so that's one way to do things another way to do things is to use the transform algorithm now we've talked a bit about transform before adjacent find is a non mutating algorithm so it doesn't make any changes to the the underlying container that it's going to be。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_78.png)

Itterating over transform in contrast is a mutating algorithm except we're going to use it in such a way here where we don't actually mutate it。

 we just update it in place and the reason I use transform is because I didn't actually have to write a loop so you'll notice here I had to write a loop and call adjacent find multiple times but transform doesn't require calling a loop you can do this in a single in a single call it's not they're both single pass because the other one is going to keep jumping the adjacent find we keep jumping by the iterator returned and you skip over everything else and start at the next iterator but transform is cool because you can do it in one fell swoop without having to have a loop。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_80.png)

![](img/d0a7ff755611e40bbce27dc51146699e_81.png)

So here's what we're going to do， we're going to start with the beginning of the iterator range going up to one less than the end。

 so let's say that there's I don't know 16 elements。

 so we're going to start with zero up to up to 15， not the 15th lo not you know sub15 but the 15th element we won't go to the very last one。

😡，And then we're going start the second range for transform one past the beginning and that of course will go up to the end。

 so we're basically going to have two ranges that are going to be offset by one and they're just going march through here and this binary function is going to be called at every step along the way in order to transform and so let's go ahead and see what transform will do。

 but before I show you what we're going to be transforming by this binary function let me show you what we're transforming into we're actually transforming back into ourse so we're doing this transform but we're actually not changing anything we're just writing the value back to where it had started from and transform works perfectly fine like that。

😡，So here is the lambmbda function that we define， which is going to be using a decal type mechanism to。

😡，Deduce the actual type in this case it's the meeting type and I probably could have put meeting in here because it's pretty clear that this is looking for meeting conflicts。

 but just for kicks just because I like using decal type I use decal type on star begin and that will figure out the type of that and that'll make that the parameter that's passed here for the lambmbda and so I pass by reference to avoid having to do copies and so what I've got here is basically a meeting lefthand side meeting righthand side and of course what they're really going to be is they're going actually be adjacent elements in the underlying container as I march from begin to begin plus one I march down through them in a pairwise fashion。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_83.png)

So if it turns out that the lefthand side equals the righthand side， in other words。

 if our quality operation on the meeting returns true。

 that means there was an overlap in the time and of course that'll come out as a conflict so we'll print the conflict and then the last thing we do is we return the lefthand side so it'll get updated in place。

😡，So two different ways of doing this checking， one of them uses adjacent find which is honestly probably the right way to do it because transform as we'll see in a second is a bit overkill。

 but adjacent find requires us to use an explicit loop conversely transform does not require an explicit loop。

 it does the looping internally and we pass in a binary function。

 the downside is that it's probably doing more work than we really need because it's doing this right back to the vector and we don't really need to do that。

😡，But the point is that STL gives us all kinds of opportunities to do cool things。

 and then we can decide what makes the most sense given our requirements and what we're trying to achieve。

😡。

![](img/d0a7ff755611e40bbce27dc51146699e_85.png)

Okay so that is the program that I wanted to show you today I think it's really fun and it's just a great example of all the interesting things you can do with STL and how very little code we actually had to write and especially very little custom code we had to write let's assume that the ArgV iterator is something we could reuse for other classes so that that was well investedted time to make ourselves the generic ArgV iterator and that worked seamlessly with the copy algorithm we used the backiner which is also another STL iterator adapter we used the sort algorithm to sort the vector we were able to use the adjacent find and or transform methods to do our thing and so really the only thing that we wrote that was kind of custom for this application was the meeting struck that we had which makes sense because we have to do some domaincentric programming and that's what it was but almost everything else just kind of came along for。



![](img/d0a7ff755611e40bbce27dc51146699e_87.png)

ide we wrote insertion and extraction operations so we can use those things that we used the string stream in order to be able to convert strings to numbers。

 so the real take home point of all this is that STL makes it really easy to write reusable code it makes it really easy to reuse existing STL code and it makes it really easy to adapt your code that you write that's reusable with the reusable code that's an STL So this is a very simple example but it's also a good example of the power of STL and the whole theory of you know write less do more and it also it demonstrates the concept of zero overhead abstraction because there's not a virtual method to be found in here lots of inlining the compiler can optimize the heck out of this and it's just going to work really well and is very clean and easy to understand once you understand the patterns of STL。

Okay well thank you guys for coming if you enjoyed this content please don't forget to like and if you're new to the channel please go ahead and hit the subscribe button so thanks very much and I will look forward to talking with you again soon。

😡。