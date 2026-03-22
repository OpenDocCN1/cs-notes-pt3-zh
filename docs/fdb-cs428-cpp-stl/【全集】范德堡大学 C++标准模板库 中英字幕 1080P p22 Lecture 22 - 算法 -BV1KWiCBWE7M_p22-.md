# 【全集】范德堡大学 C++标准模板库 中英字幕 1080P p22 Lecture 22 - 算法 -BV1KWiCBWE7M_p22-

Hello。And welcome to the next session in my webinar series on C plus plus Data Temp Library。

 by example。😊，Today we're going to be starting to talk about one of the most expressive aspects of STL which are its support for generic algorithms thus far we've talked about C++ template functions and template classes。

 we've talked about containers we've talked about iterators we've talked about functorters and various types of adapters and at long last it's time to get down to the algorithms。

 which is arguably why C++ STL is so popular because there's so many cool algorithms to do all kinds of things you used to have to do by hand。

😡，So without any further ado， let's go ahead and take a look at the code we're going to examine and then we'll just jump right into it。

So if you go to my GitHub repository and look in the C++ STL S 10 folder。

 you'll see there's a number of subfolders， 10。1 through 10。4。

 and that's what we're going to start focusing on today。



![](img/410434f87d02ca06ec6053e792193f6e_1.png)

So initially， I just want to give you an overview of the different types of STl algorithms they're typically clumped into。



![](img/410434f87d02ca06ec6053e792193f6e_3.png)

3 high level header files， algorithm， numeric and functional。 Obviously。

 the bulk of the algorithms are in the algorithm header file。 There's some numeric。

Functions that are in numeric and then those functionss we've talked about before。

 they aren't really strictly algorithms， but they do perform computation。



![](img/410434f87d02ca06ec6053e792193f6e_5.png)

The types of things you can do with the different methods and generic functions that are provided in these header files include traversing through containers。

 searching， sorting。😡。

![](img/410434f87d02ca06ec6053e792193f6e_7.png)

Doing various kinds of insertions， removing elements and so on and so forth And what's interesting about this is that these algorithms are all implemented in a way that work very well with the containers and the iterators that are built into STL in the form of various classes orstructs。

 but they also work nicely together with custom implementations you can make your own containers for example。

 you can make your own iterators and the other thing you can do of course。

 is you can use the native seastyle arrays and pointers that work on pointers to arrays with pointer arithmetic and all of these things work kind of in a plug play type manner with all the different algorithms。



![](img/410434f87d02ca06ec6053e792193f6e_9.png)

![](img/410434f87d02ca06ec6053e792193f6e_10.png)

![](img/410434f87d02ca06ec6053e792193f6e_11.png)

![](img/410434f87d02ca06ec6053e792193f6e_12.png)

One thing to be aware of is that containers are never passed directly to algorithms instead you get iterators to the containers and those iterator ranges are typically what's passed to the algorithms there are a few minor exceptions here and there。

 but by and large that's the general way things work。😡。



![](img/410434f87d02ca06ec6053e792193f6e_14.png)

And the algorithms can， of course， work with any type of calling iterator that's passed to them as long as they have the right form of iterator that's expected。

 such as a random access iterator or a bidirectional iterator and so on and so forth。



![](img/410434f87d02ca06ec6053e792193f6e_16.png)

![](img/410434f87d02ca06ec6053e792193f6e_17.png)

It's also possible to categorize the STL algorithms in four clumps the first clump which we're going to focus on today are the so-called non-mutating algorithms and these operate on ranges of iterators but actually don't change the values that they're going to access so good examples of this would be algorithms we've seen like find algorithms like count algorithms like equal which we haven't really looked at closely but it should be pretty clear what it does so those are all things that don't mutate they don't change the underlying contents in the container。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_19.png)

![](img/410434f87d02ca06ec6053e792193f6e_20.png)

![](img/410434f87d02ca06ec6053e792193f6e_21.png)

![](img/410434f87d02ca06ec6053e792193f6e_22.png)

![](img/410434f87d02ca06ec6053e792193f6e_23.png)

Then they're also a bunch of so-called mutating algorithms and these are the ones that work on ranges of iterators too。

 but they can change the values of the data items in the containers or in the underlying arrays that they tend to be working on so examples here some of which we've seen would be copy remove。

 swap， generate and fill。😡，Yet another grouping or category of algorithms are the ones that work on sorting and set operations and these of course will also mutate so they're guess strictly part of the mutating category。

 but we tend to think about sorting and sets as their own subcategory so sorting of course is going to sort the contents in the underlying container in some order either ascending or descending and set operations will do common operations like set intersection。

 set union set difference and so on。😡，And then the fourth category is called the numeric operations。

 these provide numeric computations， things like accumulate， for example。

 or inner product and stuff like that。

![](img/410434f87d02ca06ec6053e792193f6e_25.png)

So in addition to these main types of algorithms within each algorithm category。

 there's also another subcategory of algorithms that end in the underscore if suffix and these are all known as predicate algorithms or the if algorithms。

 this would be things like find if or count if and what they do is they take predicates which are typically functors or adaptations of funcctors through negators or binders and so on and they manipulate the underlying operations in the container that they're going through to check and see whether or not they return true or false。

 so maybe manipulates the wrong word but they perform some kind of check to see whether or not something passes the predicate and then do the appropriate operation based on what algorithms being performed。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_27.png)

![](img/410434f87d02ca06ec6053e792193f6e_28.png)

![](img/410434f87d02ca06ec6053e792193f6e_29.png)

![](img/410434f87d02ca06ec6053e792193f6e_30.png)

![](img/410434f87d02ca06ec6053e792193f6e_31.png)

There's a number of reasons why you should use STL algorithms。

 first of all they're well designed and they're hard very well optimized and someone spent a lot of time debugging them and thinking through the asymptotic time complexity so they're just a good thing to have to take off the shelf to avoid having to reinvent the wheel。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_33.png)

![](img/410434f87d02ca06ec6053e792193f6e_34.png)

They're also nice because they're decoupled from the particular containers they operate on and instead of parameterized by。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_36.png)

By iterators so that means they're more flexible so for example。

 you don't have to write lots of different containers that work on different kinds of algorithms instead you can have a small number of containers and then the iterators to those containers can be used for the algorithms so it keeps the surface area of STL a lot smaller。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_38.png)

![](img/410434f87d02ca06ec6053e792193f6e_39.png)

Moreover， all containers with the same iterator type can use the same algorithms。

 so we'll see that you have these categories of iterators again like the forward iterators and bidirectional iterators and random access iterators and different types of algorithms have expectations on the types of iterators that they take a good example of this of course would be the sort algorithm which expects a random access iterator range if you give it up bidirectional iterator doesn't know what to do it'll throw a compile time error saying what are you doing in you're giving the wrong kind of iterator。

😡，So we're going to go talk about some of the nonmating algorithms next。

 but I wanted you to get the big picture view before we start diving into the specifics for each of these categories and look at some code。

😡，So armed with that knowledge， now let's go ahead and take a look at the next discussion which is also simply conceptual。

 we're not quite ready to go into the code yet， this is giving an overview of some of the key non-mutating algorithms that you'll find with STL and here's a list it's not an exhaustive list but it's a very representative list of the types of algorithms you'll find that are so-called non-mutating。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_41.png)

![](img/410434f87d02ca06ec6053e792193f6e_42.png)

![](img/410434f87d02ca06ec6053e792193f6e_43.png)

One of them is called adjacent find and this will go through a range and it'll look for two elements that are next to each other that compare equal and of course you can define what equal means so you can use this for all kinds of cool algorithms that look for things like conflicts or overlaps and ranges and so on and we'll actually take a look at an example in a not too distant future that uses adjacent find in a very cool way。

😡，There's a whole bunch of count algorithms like count and count if we've looked at those before。

 we're going to look at some of the examples again briefly and they do what you think they go through and they count the number of times the value appears or the number of times a predicate is matched。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_45.png)

There's also the equal algorithm that returns true if two ranges are equal。

 the values in two ranges are equal， there's a bunch of find algorithms like find find if there's find if not。

 there's find end which search backwards it find first of and just a bunch of find out operations and they keep adding new ones all the time。

 so those are basically linear searches， there's a for each algorithm that marches down through a range and invokes a function on every element to do something to it and then returns the result of all the computations performed on that function。

😡，To pick a functer of course， there's a mismatch algorithm that finds the first position where two ranges differ。

 it's kind of like diF if you've ever used the Uni utility diF。And then there's a couple of search。😡。

Algorithms that look for sub sequenceequences within a range。

 so you can look for do you have a vector of vectors。

 you can look for sub vectors that appear within those things。



![](img/410434f87d02ca06ec6053e792193f6e_47.png)

One of the things to note is a lot of these algorithms have some expectations about what's passed to them so a good example would be equal。

 the equal algorithm takes an iterator to the beginning of the first range and an iterator to the end of the first range and then it takes an iterator to the beginning of the second range and the expectation is that the second range is at least as big as the first range and of course if that's not true chaos and insanity will ensue so always make sure when you use some of these algorithms that you first do a little sanity check like check to see if the sizes are equal before you go ahead and actually call the algorithms on the iterator ranges and STL like much of C++ expects that you know what you're doing and if you do you get rewarded with good performance but if you don't you end up with a big mess so it's usually wise to think carefully and do a proper checks in your code before you start using some of these algorithms in production code。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_49.png)

![](img/410434f87d02ca06ec6053e792193f6e_50.png)

![](img/410434f87d02ca06ec6053e792193f6e_51.png)

![](img/410434f87d02ca06ec6053e792193f6e_52.png)

All right， so now let's go ahead and take a look at some of the examples of。😡。



![](img/410434f87d02ca06ec6053e792193f6e_54.png)

STL。Algorithms。And we're first going to。

![](img/410434f87d02ca06ec6053e792193f6e_56.png)

Start with one that's going to demonstrate some of the features that we've talked about before with respect to predicates and with respect to funcctors and some of the simple algorithms that work so as you can see here we're going to define ourselves a stateful functer just for kicks just to show a stateful functer because we haven't shown a whole lot of those and this stateful functer is going to be called is greater than and as you can see here it has a constructor that takes a constant T ref and stahees it away in a local。



![](img/410434f87d02ca06ec6053e792193f6e_58.png)

![](img/410434f87d02ca06ec6053e792193f6e_59.png)

![](img/410434f87d02ca06ec6053e792193f6e_60.png)

![](img/410434f87d02ca06ec6053e792193f6e_61.png)

Data member and then its function call operator will take the element pass to it。

 which is also passed as a constant ref and check to see whether or not that element is greater than the value that we stashed away so you can see it keeps the state in there so it can do the comparison each time。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_63.png)

![](img/410434f87d02ca06ec6053e792193f6e_64.png)

And so then we're going to show off a couple of examples here with the find if algorithms。

 so this is one of the family of find algorithms that you find in the non-mutating part of STL and you can see here that we're going to have a deck just for kicks we have a deck this time with a bunch of values some of which are positive some of which are negative and we're going to start by giving a value to search for that has the value of five so it's an auto with the value of five and that we do is we start out by using our is greater than perhaps two custom functer to check to see whether or not the value here is greater than the five which is what we pass in so you can see we create an anonymous instance of is greater than passing in the value and of course that then is used by find if and we've looked at find if many times before remember that's the one that's actually lurking in the algal base that。



![](img/410434f87d02ca06ec6053e792193f6e_66.png)

![](img/410434f87d02ca06ec6053e792193f6e_67.png)

![](img/410434f87d02ca06ec6053e792193f6e_68.png)

![](img/410434f87d02ca06ec6053e792193f6e_69.png)

![](img/410434f87d02ca06ec6053e792193f6e_70.png)

![](img/410434f87d02ca06ec6053e792193f6e_71.png)

Each file so we can't easily get to it without doing some prestging and what it'll do is it'll go through there and it'll make that predicate call each time until it finds a match and if it finds a match it'll return an iterator and if the iterator is not equal to the end then we know we found something that equaled that value and we get basically an iterator to it so can de referenceence it。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_73.png)

![](img/410434f87d02ca06ec6053e792193f6e_74.png)

![](img/410434f87d02ca06ec6053e792193f6e_75.png)

![](img/410434f87d02ca06ec6053e792193f6e_76.png)

The next thing we're going to do is just to show again how we can use find di， the find di algorithm。

 except this time， we're going to use a value that'll be equal to 20， not 5。

 And also just to kind of mix it up a little bit。 We're going to use the newer。



![](img/410434f87d02ca06ec6053e792193f6e_78.png)

C++ STL bind binder as opposed to bind second and what this is going to do is it's going to get rid of the need for the is greater than custom functer and instead use the predefined greater funter。

And this allows us to then go ahead and bind the second value here。

 the first value in this greater functer， which is a binary fun。

 is just a placeholder for whatever happens to come from the range from beginning to end of the vector and we're going to bind value as the thing we're comparing so in this case we're comparing against 20 so once again。

 if we get a hit， it'll give us back that the iterator where we found the value 20 and we of course we'll find the value 20 because it's in the values deck。



![](img/410434f87d02ca06ec6053e792193f6e_80.png)

![](img/410434f87d02ca06ec6053e792193f6e_81.png)

![](img/410434f87d02ca06ec6053e792193f6e_82.png)

And then the third example here is kind of a fun one。

 and this will illustrate some things we haven't talked a whole lot about up to this point。

 which is the use of the capture clause in a C++ generic lambmbda。😡。

So this is a generic lambmbda function this time we're going to go ahead and have the generic lambmbda function which is going to look for values greater than 40 in this case。

 and you'll notice that we set the value 40 outside of the lambmbda function。

 so it's set right before we call find if。😡，And then when we look inside here。

 we have to compare I which is our parameter that comes through each for each element in the range from first to end or begin to end。

 and we're going to use that to compare against value well the tricky part is that value is actually a local variable so how do we get access to it in the context or in the scope of the lambmbda function and the trick is we use this thing called the capture clause。

😡，And it's between the open close。Square brackets and if we omit the capture clause as I'm doing now by coming it out。

 you can see it doesn't know what this value is。😡，So it doesn't know how to access it。

 so there's two ways to make it accessible one is to type value and explicitly say I want this local variables value to be passed in here。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_84.png)

![](img/410434f87d02ca06ec6053e792193f6e_85.png)

And then we can refer to it just fine。 So it's kind of like it's kind of like an extra parameter。

 if you will， it's kind of providing a context for the lambmbda function。

 So that's one way to do it and that says just let value come in the other way to do it is a little bit more expansive we can just say the ampersand operator or the address of operator and what that says is let anything in the local scope be accessed inside of the Lambda function and it kind of depends on what you're doing is to which way is the right way to go I kind of like this approach because it makes it very clear where this is coming from and it's getting us the narrowest scope necessary in order to get the job done but be aware that if you have more complicated Lada you may not want to sit there and laboriously put all the variables they need to access in the capture clause that can get excessive Okay so that's basically what the code does。

 let's go ahead and run it。

![](img/410434f87d02ca06ec6053e792193f6e_87.png)

![](img/410434f87d02ca06ec6053e792193f6e_88.png)

![](img/410434f87d02ca06ec6053e792193f6e_89.png)

![](img/410434f87d02ca06ec6053e792193f6e_90.png)

![](img/410434f87d02ca06ec6053e792193f6e_91.png)

And hopefully it'll compile it run just fine， looks like it's doing well。

 so you can see we get the answers we expect we look for 10。



![](img/410434f87d02ca06ec6053e792193f6e_93.png)

![](img/410434f87d02ca06ec6053e792193f6e_94.png)

Os 10 is greater than five yes so 10 is greater than five I agree with that and 40 is greater than 20 and down here I should say is。

Greater than or equal to。

![](img/410434f87d02ca06ec6053e792193f6e_96.png)

40 so 40 is greater than equal to 40， notice how I did a little sleigh of hands here and changed the expression to be greater than or equal to rather than just greater。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_98.png)

As we had done with the functors and the binders earlier。Okay。

 so this is just kind of showing off some of the interesting examples of the find family of methods。

 I probably should show other ones too like we could use find not which would find the first thing。

 we could say find if not and then that would go ahead and invert this so it would find the first value that was not greater than or equal to 40。

😡，And it's just for kicks， let's say， is not greater than or equal to 40， so let's do that one。



![](img/410434f87d02ca06ec6053e792193f6e_100.png)

See what we get back as the result and that probably should be the very first thing which is 10 so I think we would agree that the value 10 is not greater than or equal to 40 so that's another example of where we're doing a different kind of find operation and there's other things we could do here as well there's other find operations we could use find as opposed to find if if we want to look for specific value as opposed to a predicate and so on and so forth。



![](img/410434f87d02ca06ec6053e792193f6e_102.png)

![](img/410434f87d02ca06ec6053e792193f6e_103.png)

![](img/410434f87d02ca06ec6053e792193f6e_104.png)

![](img/410434f87d02ca06ec6053e792193f6e_105.png)

Okay， there's one more example I want to take a look at。😡。



![](img/410434f87d02ca06ec6053e792193f6e_107.png)

In this session。And this is kind of a fun one， this is going to show us some other cool things。

 this is going to focus on the count family of algorithms so we've looked at the find family。

 some of the find some of the fine find family of algorithms now let's go ahead and count on the count family of algorithms so we're going to take a look at count and count if which are also to very very common non-mutating STL algorithms so to show this thing off we're going to define ourselves a little functer which is a generic fun called as value for absolute value and you can see here how it function coop takes a parameter F and returns the absolute value of F so if it's negative it'll come back positive if it's positive it'll stay positive。



![](img/410434f87d02ca06ec6053e792193f6e_109.png)

![](img/410434f87d02ca06ec6053e792193f6e_110.png)

![](img/410434f87d02ca06ec6053e792193f6e_111.png)

![](img/410434f87d02ca06ec6053e792193f6e_112.png)

![](img/410434f87d02ca06ec6053e792193f6e_113.png)

So here's our program， this program basically demonstrates the use of STL algorithms account。



![](img/410434f87d02ca06ec6053e792193f6e_115.png)

And。Cant。Yeah。诶。In conjunction with our。Value culture。



![](img/410434f87d02ca06ec6053e792193f6e_117.png)

And you'll see in a second why we're doing this this give us a good excuse to play around with things like nested binders。

 which are pretty cool and difficult to do with the earlier versions of binders in STL。

 but with the newer versions it's much easier。So here's our vector。

 we have a vector of a bunch of positive and negative ints。😡。



![](img/410434f87d02ca06ec6053e792193f6e_119.png)

And we start out by using find just to find the value10s， which we find right away。

 of course because it's right at the beginning and now what we're going to do is we're going to count the number of times that 10 occurs in the range。

 so you can see here we use count we pass in the value。

 which is the dereferenced iterator and it'll come back and tell us the number of times that count occurs and it should be two times because positive 10 occurs twice in that vector V。



![](img/410434f87d02ca06ec6053e792193f6e_121.png)

![](img/410434f87d02ca06ec6053e792193f6e_122.png)

Now let's go ahead and do something a little bit more adventurous。

 we're going to use the count if algorithm， we're going to go through the same vector from beginning to end except this time we're going to use nested binders and we're going to count the number of times that the absolute value of 10 occurs in this range and you'll also see another way to do this that isn't quite as convoluted but this is kind of cool it's kind of rare to see examples that demonstrate nested binders and I thought I should show that to you just because it's an interesting thing to know how to do。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_124.png)

![](img/410434f87d02ca06ec6053e792193f6e_125.png)

So here's what we're doing we're going to go ahead and first find the abs value I think I might be able to get rid of that so we can have we can find the abs value the abs value is going to get bound to the value。

😡，Of in this case， 10 and so we're。We're going to do is we're going to。

No i'm sorry what we're going to do here is we're going to go ahead and check to see if something's equal to the absolute value of 10 so the absolute value part here is bound to this placeholder as you can see here absolute value is a unary funter so we're binding it to this placeholder using bind which is smart enough know it's got a unary value here and so what it's doing is it's taking each of the values in the range from beginning to end and it's。

Applying the absolute value funter on it so minus 10 and 10 are being treated as the same value。

 and then it's binding equal to to the absolute value of what's going through the range and then it's comparing that against the value 10。

 which is what we got with this iterator up here when we found 10。😡。



![](img/410434f87d02ca06ec6053e792193f6e_127.png)

So this should give us back a different number， in fact let's just go ahead and run the program and you can see what it gives back as a result。



![](img/410434f87d02ca06ec6053e792193f6e_129.png)

![](img/410434f87d02ca06ec6053e792193f6e_130.png)

So as I had mentioned before， when we do the regular old count operation。

 which is the first thing that we do up here， this is going to come back finding two occurrences because there's 10 and 10 it appears twice。

 but then when we come down here and we do the bind。😡。



![](img/410434f87d02ca06ec6053e792193f6e_132.png)

![](img/410434f87d02ca06ec6053e792193f6e_133.png)

![](img/410434f87d02ca06ec6053e792193f6e_134.png)

The nested binder version where we're using the absolute value functer to take the value and turn minus 10 into 10 or whatever or negative numbers into positive numbers。

 then of course we find three occurrences because there's 10。

 10 and minus 10 So this nested binder thing is pretty cool I had to spend a little while figuring out how to make that work because the descriptions in stack overflow and other places weren't very descriptive so here you go you can hopefully find this useful if you ever have to use nested binders。



![](img/410434f87d02ca06ec6053e792193f6e_136.png)

![](img/410434f87d02ca06ec6053e792193f6e_137.png)

![](img/410434f87d02ca06ec6053e792193f6e_138.png)

But honestly it's it's probably more trouble than it's worth and so here is a much more straightforward way in my opinion of doing this and is what we're doing here is we're just going to use a lambmbda function。

 a generic lambmbda function and here we just say you know for every element in the range from beginning to end。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_140.png)

![](img/410434f87d02ca06ec6053e792193f6e_141.png)

Call this code。 and we're just going to directly say is the absolute value of the parameter equal to whatever the iterator is that we're looking for and you'll notice again that。



![](img/410434f87d02ca06ec6053e792193f6e_143.png)

Ittter is coming from the outer scope right it's defined up here so we have to find a way to pass it into lambda because if we do it like this the compiler will complain and say hey you can't access this thing so we have a couple of options again we could just say ittter here and then that。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_145.png)

![](img/410434f87d02ca06ec6053e792193f6e_146.png)

![](img/410434f87d02ca06ec6053e792193f6e_147.png)

Gives that specific local variable to the as part of the capture clause to the lambmbda。

 or we can do what I had started out doing originally and just put the ampersand here saying anything in that outer scope that's a local variable can now be accessed by this lambda。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_149.png)

![](img/410434f87d02ca06ec6053e792193f6e_150.png)

So a bunch of different ways of doing sort of the same thing。

 hopefully you've learned something interesting and new about at the very least nested binders。

 which is pretty cool and hopefully you've also seen how you can simplify the use of convoluted nested binders with the more straightforward generic the lambda with the capture clause。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_152.png)

![](img/410434f87d02ca06ec6053e792193f6e_153.png)

![](img/410434f87d02ca06ec6053e792193f6e_154.png)

Okay， so。Those are the topics that I wanted to cover in this session we have lots lots more stuff to cover with algorithms we have some more things to talk about with respect to non-mutating algorithms。

 we have a bunch of things to talk about with respect to mutating algorithms and of course we're going to show examples that combine mutating and nonmutating algorithms in the same program which is not at all uncommon because sometimes you want to just look at stuff sometimes you want to change things and the great thing about STL is it makes it possible to to do a lot of this without you having to write the code yourself just reuse what's already there so if you enjoyed this content go ahead and like please feel free to subscribe to my channel if you'd like to learn more about these topics and also you can follow me on Twitter。

😡。

![](img/410434f87d02ca06ec6053e792193f6e_156.png)

Thanks very much。