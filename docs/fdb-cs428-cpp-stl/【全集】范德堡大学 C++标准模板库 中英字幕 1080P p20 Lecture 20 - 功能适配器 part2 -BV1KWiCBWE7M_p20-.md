# 【全集】范德堡大学 C++标准模板库 中英字幕 1080P p20 Lecture 20 - 功能适配器 part2 -BV1KWiCBWE7M_p20-

Hello and welcome to the next webinar in my series on C++ Standard Tt Library by example。Today。

 we're going to continue our coverage of function adapters。

 picking up where we left off yesterday where we covered binders。😡。

Now that we've covered binders we're going to talk about another example of a function adapter which is called a negator and we'll see that there's a number of different negators in addition to talking about the negators and showing some examples。

 we'll also have a chance to revisit some of the binder functionss and take a look at how they've evolved over time with different versions of the C++ standard。

So without any further ado， let me go ahead and share my screen。😡。

And you can see where you can find the code， you can find the code in my Gitthub repository in the C++ STL S09 folder。

 and the code we'll look at today is in the 9。3 subfold。



![](img/841b7f0aa929ea6656b076d5a9def536_1.png)

![](img/841b7f0aa929ea6656b076d5a9def536_2.png)

![](img/841b7f0aa929ea6656b076d5a9def536_3.png)

So let's go ahead and take a look at the code we're going to start off by quickly defining what a negator adapter is and a negator adapter is basically a functer that can be used to store the opposite result of another funter that it encapsulates and you can see that there's several different negators that have been defined over time some of them came around in the early 2000 time frame including not one and not two and not one basically is expected to work on a unary func or uninary operation whereas not two works on a binary fun or a binary operation and then there's a newer funcctor that's come in more recent versions of C++ called not function or not FN I'm going to call that not function just to make it easier to pronounce and not function is a very special template that can work with either。



![](img/841b7f0aa929ea6656b076d5a9def536_5.png)

![](img/841b7f0aa929ea6656b076d5a9def536_6.png)

![](img/841b7f0aa929ea6656b076d5a9def536_7.png)

![](img/841b7f0aa929ea6656b076d5a9def536_8.png)

![](img/841b7f0aa929ea6656b076d5a9def536_9.png)

![](img/841b7f0aa929ea6656b076d5a9def536_10.png)

![](img/841b7f0aa929ea6656b076d5a9def536_11.png)

Uary or binary funs， and you don't actually have to distinguish it lexically by having it be called not one or not two。

 which has always been a little bit confusing。😡。

![](img/841b7f0aa929ea6656b076d5a9def536_13.png)

![](img/841b7f0aa929ea6656b076d5a9def536_14.png)

To see how these different neators work， we're going to create our own template for a simple boolean func that'll check to see if a value it's past is either odd or even if you pass it an odd number it'll return true if you pass it an even number it'll return false and this template only takes one argument so it's basically a unitary function。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_16.png)

![](img/841b7f0aa929ea6656b076d5a9def536_17.png)

Here you can see the definition of this generic functer is odd， which is in fact a urary function。

 and you can see that it' function call method， which is of course what defines a functer takes type T parameter called number and the body of that function mods the number by two and if we get a remainder that means it's odd if we don't get a remainder that means it's even so of course it's returning a boolean value that's true or false。



![](img/841b7f0aa929ea6656b076d5a9def536_19.png)

![](img/841b7f0aa929ea6656b076d5a9def536_20.png)

![](img/841b7f0aa929ea6656b076d5a9def536_21.png)

We're also going to have a little helper method called print resultss。

 which will show off some interesting techniques involving template template parameters and we'll use this in order to be able to print the results of our computations without having to litter our code with all those calls to copy as we've been doing up to this point。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_23.png)

![](img/841b7f0aa929ea6656b076d5a9def536_24.png)

We're going to use the IO template with the STL algorithms。

 remove copy if and copy if and the STL Fun negators， not one and not function。😡。



![](img/841b7f0aa929ea6656b076d5a9def536_26.png)

![](img/841b7f0aa929ea6656b076d5a9def536_27.png)

The copy of and remove copy of algorithms all take four arguments。

 the first two are the input iterator beginning and end first and last as always。😡。

The next parameter is an output iterator where we're going to put the results。

 and then the final parameter is a predicate that we'll use to determine whether or not the elements in the range go into the results or not。

😡，In our case， we're doing it for Iad， but of course these functions can be used more generally for other kinds of predicates beyond Iad。

😡，So let's take a look at the actual code， we're going to define ourselves a vector V1。

 vector 1 that has values one through four， they don't really have to be in any particular order。

 and then we define ourselves an empty vector vector2。😡。



![](img/841b7f0aa929ea6656b076d5a9def536_29.png)

![](img/841b7f0aa929ea6656b076d5a9def536_30.png)

We're going to start by using remove copy if and what we're going to do here at a high level is we're going to go through all the the elements in vector one from beginning to end and anything that is。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_32.png)

An even number is going to be omitted from the copy， anything that is an odd number， however。

 will be put through and will actually end up in the results and the results will end up being put at the end of vector2 by using the back inserter and we've talked about back inserter before so I won't talk about that here。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_34.png)

![](img/841b7f0aa929ea6656b076d5a9def536_35.png)

![](img/841b7f0aa929ea6656b076d5a9def536_36.png)

So let's talk about the actual predicate we pass in， of course。

 we're going to use our Iage funter and we're going to negate it by using the not one negator adapter。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_38.png)

And what not one does is we'll see。

![](img/841b7f0aa929ea6656b076d5a9def536_40.png)

If you go take a look at not one， not one is a little function。

 it's a template function so it can do some magic type deduction here and what it's going to do is it's going to take in the functer that it's passed。

 which is of course itself will be treated as a predicate and it'll end up creating something called a unary gate object to hold onto to that predicate and if you go see unary in the gate。

 you can see that un in the gate is going to go ahead and hold the predicate in a local。



![](img/841b7f0aa929ea6656b076d5a9def536_42.png)

![](img/841b7f0aa929ea6656b076d5a9def536_43.png)

![](img/841b7f0aa929ea6656b076d5a9def536_44.png)

Field and a data member called M underscore preed。 And， of course， the。

 the key operation in all the functionss is operator function call。

 And you can see what it's going to do here。 It's going to go ahead when called。

 and it's going to call the underlying funter that it's stashed away in its constructor。



![](img/841b7f0aa929ea6656b076d5a9def536_46.png)

![](img/841b7f0aa929ea6656b076d5a9def536_47.png)

Get the result。 And then it's going to turn around and negate that result。

 So that's basically what it does。 It negates the results of calling funter a funter that it owns or that it stores in its data member。



![](img/841b7f0aa929ea6656b076d5a9def536_49.png)

![](img/841b7f0aa929ea6656b076d5a9def536_50.png)

Okay so that's what we're going to do to negate the is odd value Now you might ask the question why are we doing it in this somewhat convoluted way by doing remove copy if and then negating isn't that really just doing copy if without the negation and the answer is you're correct and the reason we're doing this to start out with is that when C+ plus SL was first standardized they accidentally left the copyif algorithm out of the standard so for the longest time there was only remove copy if in the standard so a lot of people had to get used to using remove copy if in conjunction with the negator in order to be able to get the copy of semantics so that's what we're doing here we're just staying true to the origins of this don't worry i'll also show you the use of copy of here in a second as well when we're all done we're going to go ahead and print the results of vector2 and we'll show how that print works in a second。



![](img/841b7f0aa929ea6656b076d5a9def536_52.png)

![](img/841b7f0aa929ea6656b076d5a9def536_53.png)

![](img/841b7f0aa929ea6656b076d5a9def536_54.png)

![](img/841b7f0aa929ea6656b076d5a9def536_55.png)

![](img/841b7f0aa929ea6656b076d5a9def536_56.png)

![](img/841b7f0aa929ea6656b076d5a9def536_57.png)

![](img/841b7f0aa929ea6656b076d5a9def536_58.png)

The next thing we're going to do here just for Ks is I'm going to switch over from using a vector to using a deck as the output iterator where the results are stored。

 just to illustrate how you can mix and match these things very conveniently in a number of different ways。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_60.png)

![](img/841b7f0aa929ea6656b076d5a9def536_61.png)

As before we're going to use remove copy F， but this time， instead of using the not one negator。

 which has been around since the early 2000s， we're going to switch to a newer variant called not function or not FN。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_63.png)

So to go look at the not function you can see it's using much more advanced features that are more c+ plus 11 issue features than the sort of 2003 STL C++ features that were there with the not one negator and in fact you can see what it's doing under the hood is it's forwarding the parameters which are passing in is our value reference and it's doing some other magic with various adapters and function mechanisms built into C++ and STL and basically it's negating things but it's doing it a way where it'll work both for unary and binary functionss not having to explicitly express them as not one or not two so that's really the reason why people are moving towards not function and the other functionss in fact the other negators not one and not two are actually being deprecated you can still get to them but if you want to write future looking code you should get used to using not function instead of not one or not two when we're done we're gonna to of course insert everything into。



![](img/841b7f0aa929ea6656b076d5a9def536_65.png)

![](img/841b7f0aa929ea6656b076d5a9def536_66.png)

![](img/841b7f0aa929ea6656b076d5a9def536_67.png)

![](img/841b7f0aa929ea6656b076d5a9def536_68.png)

![](img/841b7f0aa929ea6656b076d5a9def536_69.png)

![](img/841b7f0aa929ea6656b076d5a9def536_70.png)

![](img/841b7f0aa929ea6656b076d5a9def536_71.png)

De this time and we're going to go ahead and print the results of the deck and I'll show you that code in a second as well。



![](img/841b7f0aa929ea6656b076d5a9def536_73.png)

Well after doing that， we're going to go ahead and reset our output to be back to zero so we're going to set its size back to zero so the decks back to being empty again and this time we're finally going to use the copy of algorithm and as you can see here the copy of algorithm is a lot more straightforward to what we're trying to do because we're going to start from the beginning of vector 1 go to the end just like before we're going to back insert into deck1 which is now empty of course at least initially empty and this time rather than using negators and all this stuff we just looked at we're just going to use a good old C plus plus lambmbda function and you can see that this lambmbda function is really the same code that we had done up here in our is odd functer except now we're able to plop it in line by using a lambmbda and you can see this as a lambda because we have the openclo square brackets and we'll talk more about how that works a little bit later and then we're going to make this a generic lambda function by having it taken an auto keyword。



![](img/841b7f0aa929ea6656b076d5a9def536_75.png)

![](img/841b7f0aa929ea6656b076d5a9def536_76.png)

![](img/841b7f0aa929ea6656b076d5a9def536_77.png)

![](img/841b7f0aa929ea6656b076d5a9def536_78.png)

![](img/841b7f0aa929ea6656b076d5a9def536_79.png)

![](img/841b7f0aa929ea6656b076d5a9def536_80.png)

![](img/841b7f0aa929ea6656b076d5a9def536_81.png)

![](img/841b7f0aa929ea6656b076d5a9def536_82.png)

which means it'll work with anything that has one parameter here。

 which in our case happens to be an int， but it could be a float or a double or something else and then what we do is we take the number。

 we mo that by two and check to see whether we had a remainder so it's basically doing the I odd computation from before except now we're doing it in line。

😡，So that's the third different variant。 We did one variant that used not one。

 We did another variant that used not function， and then we did a third variant that used a lambda function Which one should you use well。

 of course if you're stuck with old versions of c+ plus as your compiler then you're probably going have to use the not one variant if you're using newer compilers C plus plus 11 you can pick using not function or of course you can use the lambda function style as well I think it really comes down to how easy is it to tell at a glance what your code is doing so when you look at this code it's pretty clear that you're negating the results of the is odd so I think that's pretty intuitive when you look at this code it might not be quite as obvious unless of course you have memorized how you check to see if a number odd or not and so it helps to put a comment of course which I've done but it also may be a little bit less intuitive so it's kind of a tradeoff The nice thing about the lambda approaches it's directly in line and you don't have。



![](img/841b7f0aa929ea6656b076d5a9def536_84.png)

![](img/841b7f0aa929ea6656b076d5a9def536_85.png)

![](img/841b7f0aa929ea6656b076d5a9def536_86.png)

![](img/841b7f0aa929ea6656b076d5a9def536_87.png)

![](img/841b7f0aa929ea6656b076d5a9def536_88.png)

![](img/841b7f0aa929ea6656b076d5a9def536_89.png)

![](img/841b7f0aa929ea6656b076d5a9def536_90.png)

![](img/841b7f0aa929ea6656b076d5a9def536_91.png)

![](img/841b7f0aa929ea6656b076d5a9def536_92.png)

![](img/841b7f0aa929ea6656b076d5a9def536_93.png)

![](img/841b7f0aa929ea6656b076d5a9def536_94.png)

![](img/841b7f0aa929ea6656b076d5a9def536_95.png)

go searching around to see where your funkctorters are defined the downside is it may be longer amounts of code。

 and especially if you were planning to do lots of checks to see whether something was odd。

 you might want to actually make your own explicit functer in that case and use it as we've shown here in either the remove copy of negator form or the copy of nonnegator form。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_97.png)

![](img/841b7f0aa929ea6656b076d5a9def536_98.png)

![](img/841b7f0aa929ea6656b076d5a9def536_99.png)

Now that we've talked about these topics， let's go ahead and show how we're going to print out the results or how we do print the results。

 And as I mentioned before， this is an example of a template template parameter past to a C plus plus function。

 So print results takes a tight name key， which is the elements we're working on with our container。

 And then it also takes a template parameter itself。

 which is going to be used to pass sequential containers， things like vectors， decks or lists。

 And as you can see here， we're going to take our sequential container that gets passed in。

 And then we're going to go ahead and write a little generic piece of code where we start at the beginning of the container。

 And we're going go to the end。

![](img/841b7f0aa929ea6656b076d5a9def536_101.png)

![](img/841b7f0aa929ea6656b076d5a9def536_102.png)

![](img/841b7f0aa929ea6656b076d5a9def536_103.png)

![](img/841b7f0aa929ea6656b076d5a9def536_104.png)

![](img/841b7f0aa929ea6656b076d5a9def536_105.png)

![](img/841b7f0aa929ea6656b076d5a9def536_106.png)

And this way we can kind of pass the whole kitten koole in as a contfe and then we're going to go ahead and use the Ostream iterator with parameter T。

 which is the type parameter that's passed to this template in order to be able to do the iterator adapter technique you've looked at before to get the results written to the output so that's one particular way of doing things。

 obviously we're going to see some other ones when we look at the next example。

 but this is a nice example of showing how you can use template template parameters。

 if you want to be able to pass over and print the entire contents of the container that you just manipulated using remote remove copyF or copyF。



![](img/841b7f0aa929ea6656b076d5a9def536_108.png)

![](img/841b7f0aa929ea6656b076d5a9def536_109.png)

![](img/841b7f0aa929ea6656b076d5a9def536_110.png)

![](img/841b7f0aa929ea6656b076d5a9def536_111.png)

![](img/841b7f0aa929ea6656b076d5a9def536_112.png)

![](img/841b7f0aa929ea6656b076d5a9def536_113.png)

So that's the end of our first example。 Now let's go ahead and take a look at the second example。😡。



![](img/841b7f0aa929ea6656b076d5a9def536_115.png)

And this is also quite interesting and this will give us a chance to talk about yet other aspects of negators and in fact it'll give us a chance to return to our discussions of binders and it'll give us yet another chance to talk about another way to implement the print results method and this one rather than taking in the whole container is just going to take an iterator to the beginning of the range we want printed and to the end of the range we want it printed and it'll go ahead and do some really cool type deduction and we'll take a look at that as well。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_117.png)

![](img/841b7f0aa929ea6656b076d5a9def536_118.png)

![](img/841b7f0aa929ea6656b076d5a9def536_119.png)

![](img/841b7f0aa929ea6656b076d5a9def536_120.png)

So let's start off by defining an overly specific functer I call this functer int greater than three and I probably would never write code like this。

 but I just want to be able to show how you could do this if you want it to get really really specific So int greater than three of course is a unary function and kind of like the isad function it takes in a parameter in this case we've hardcoded it to int and it's going to check to see whether the parameter x past in is greater than three or not if it is greater than three it'll return true if it's not greater than three it'll return false Now you should know right off the top of the bat that this is not the best way to write funcctors because there's already functionss that exist in STL that can be adapted using binders to work in the way that we would use in greater than three but we'll talk about that in a second Okay so let's take a look at the example the main program and you can see we're going to demonstrate the use of functors being used with。



![](img/841b7f0aa929ea6656b076d5a9def536_122.png)

![](img/841b7f0aa929ea6656b076d5a9def536_123.png)

![](img/841b7f0aa929ea6656b076d5a9def536_124.png)

![](img/841b7f0aa929ea6656b076d5a9def536_125.png)

![](img/841b7f0aa929ea6656b076d5a9def536_126.png)

Not one， not two and the not function negators that we've talked about so far。

 we haven't talked about not two yet， but you'll see how that works and then we're also going to take a look at the various find if and find if not STL algorithms and of course because it's important to know how to compare and contrast the use of functors with lamb expressions and lambmbda functions。

 we'll also take a look at that as well。😡。

![](img/841b7f0aa929ea6656b076d5a9def536_128.png)

![](img/841b7f0aa929ea6656b076d5a9def536_129.png)

![](img/841b7f0aa929ea6656b076d5a9def536_130.png)

So let's start out with the actual source code we're going to define a vector that has several elements。

 it has the elements four，1，2，8，57 and it actually kind of matters for our example that they're in that order as you'll see in a moment the first thing we're going to do is we're going to use our custom funter。

 the in greater than three funter and the not one negator kind of that legacy negator。😡。



![](img/841b7f0aa929ea6656b076d5a9def536_132.png)

![](img/841b7f0aa929ea6656b076d5a9def536_133.png)

![](img/841b7f0aa929ea6656b076d5a9def536_134.png)

![](img/841b7f0aa929ea6656b076d5a9def536_135.png)

To get an iterator to the first element in our vector that has a value that's not greater than three。

😡，And so let's go take a look at findDF we've talked about FindDff before。

 but it helps to refresh your memory Now FDff is one of these kind of funky methods that it isn't quite where you think it is and in fact its actual implementation if you want to see the actual code lurks in the Ag base H file and so if you take a look here our sea lion code got us to this point and then you can see it turns around it calls underscore underscore fineDF well it turns out you can't find that method in this file and it turns out sea lion won't take us there directly but I found this a little bit earlier and I brought up the code so we could take a quick look at it。



![](img/841b7f0aa929ea6656b076d5a9def536_137.png)

![](img/841b7f0aa929ea6656b076d5a9def536_138.png)

![](img/841b7f0aa929ea6656b076d5a9def536_139.png)

![](img/841b7f0aa929ea6656b076d5a9def536_140.png)

![](img/841b7f0aa929ea6656b076d5a9def536_141.png)

![](img/841b7f0aa929ea6656b076d5a9def536_142.png)

So you can see here that find diF takes， in this case。

 it's going to take a random access iterator because of course we're working with a vector and it takes a predicate。



![](img/841b7f0aa929ea6656b076d5a9def536_144.png)

![](img/841b7f0aa929ea6656b076d5a9def536_145.png)

And then down here you're going to see that what we're going to be able to do whoops I take it back here's the find if we're going to take a look at this this is a this is an overloaded version that's used or a template specialized version here's the one that we actually want this is going to take。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_147.png)

![](img/841b7f0aa929ea6656b076d5a9def536_148.png)

![](img/841b7f0aa929ea6656b076d5a9def536_149.png)

An input iterator， which in this case will be a random access iterator and a type name for the predicate。



![](img/841b7f0aa929ea6656b076d5a9def536_151.png)

And find if takes the range from first to last as always。

 and it takes the predicate and then if you take a look down here。

 you can see what it does is it goes through that range as always。😡。



![](img/841b7f0aa929ea6656b076d5a9def536_153.png)

Iterating through it。 And what it's going to do is it's going to check to see whether or not there's a match on the predicate。

 And if there is a match， then we're done。 if there's no match。

 we keep going and we keep incrementing first by one。



![](img/841b7f0aa929ea6656b076d5a9def536_155.png)

So that's basically what Find if is going to be doing here and keep that in mind because we'll come back and talk about it a little bit more in a second。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_157.png)

![](img/841b7f0aa929ea6656b076d5a9def536_158.png)

So what we're going to do is we're going to go ahead and have the predicate be not ink greater than three and of course。

 that's going to return an iterator。 And in this case。

 the first element in this vector that's not greater than three will be the second element in the vector So we're going to get an iterator back to the second element and then what we're going to do is we're going to use our print results method。

 this new print results method to start at the iterator match and then go to the end So it's going to skip over the four in this case and start printing at one and it'll print 1。

2，8，5，7 Okay， so that's the first variant。😡。

![](img/841b7f0aa929ea6656b076d5a9def536_160.png)

![](img/841b7f0aa929ea6656b076d5a9def536_161.png)

![](img/841b7f0aa929ea6656b076d5a9def536_162.png)

Now let's come down here and take a look at what we could do if we wanted to do had a more standard code get rid of this crazy overly specific custom functer so in this case we're going to do much the same thing with findD except in addition to using not one we're going to pull out our bind second method that we taken a look at yesterday and this is basically a funter that knows how to adapt other funs and in this case it's going to adapt the greater functer which is a predefined fun that's an STL and it's going to bind it to three so what this is basically saying is find me the first。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_164.png)

Element， give me an iterator back to the first element in the vector that is not greater than three and now we're not having to write our own custom functer we're using the greater functer that already exists in conjunction with the bind second binder to bind it second parameter to three and then we go ahead and encapsulate that inside the not one negator so you can see how we're kind of chaining these adapters together in order to get the result of we want。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_166.png)

![](img/841b7f0aa929ea6656b076d5a9def536_167.png)

![](img/841b7f0aa929ea6656b076d5a9def536_168.png)

![](img/841b7f0aa929ea6656b076d5a9def536_169.png)

Well， not surprisingly we'll get the result that we want。

 we'll once again get back an iterator that starts here at one because that's the first element in the vector that's not greater than three。



![](img/841b7f0aa929ea6656b076d5a9def536_171.png)

All right， so now let's go ahead and take a look at the more modern ways of doing this and we'll see a couple different variants for various reasons the binders that we talked about yesterday。

 bind first and bind second have also been deprecated much like not one and not two and that doesn't mean that they don't exist anymore。

 just means that you should start thinking about alternative ways of doing things。😡。

And the technique that was introduced to do this is something that's called bind。

 but for various reasons bind has fallen into illreputute and in fact I'm going to show you how to do it。

 but then I'm also going to show you that it's actually discouraged and we'll take a look at that in a second。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_173.png)

But first let's talk about what bind is and in addition to using bind I'm also going to use the not function negator instead of using the not one negator so this is a modern negator used with a more modern binder if you will and so what we're going to do here for the binder is we're going to go ahead and say I want to bind greater and all the other cool thing I can do with this is I can use this more concise form of using a function you can leave out the type parameter and it can figure it out unfortunately you can't do that with bind second。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_175.png)

![](img/841b7f0aa929ea6656b076d5a9def536_176.png)

![](img/841b7f0aa929ea6656b076d5a9def536_177.png)

The compiler gets confused for various reasons so we have to be a little bit more robustbo that's another reason why they have deprecated by and second。

😡，So here's the binder， we say I want to bind I want to make a binder that'll bind something to greater and you can tell that this is going to be a bind second approach because we're going to leave a placeholder for the first parameter and of course that placeholder is going to be replaced with the elements that are in the range from beginning to end of the vector。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_179.png)

![](img/841b7f0aa929ea6656b076d5a9def536_180.png)

And then the third parameter to bind is going to be the value3。 So once again。

 we're going to be binding， creating a binder that will find the first element that's three。

 And then we use not function to negate that。 Now， I don't know about you。

 this actually is arguably better than bind first and bind second in some ways。

 but it's also kind of ugly。 And in fact，' you can tell that it's fell and disrepute because if you take a look here that the IDde is telling us use a lambda function rather than using bind。

 we really think binds a bad idea。 So be that as it may。

 I'll show you the lambda function in a second， but this is the way that you could use bind And of course。

 if you wanted to swap the order， you could turn this into a sort of a bind first by putting the three first and then the placeholder second。

 So that would be an easy way of getting the effective behavior of bind first。

 But right now we're doing bind second。

![](img/841b7f0aa929ea6656b076d5a9def536_182.png)

![](img/841b7f0aa929ea6656b076d5a9def536_183.png)

![](img/841b7f0aa929ea6656b076d5a9def536_184.png)

All right so here is the final way of doing things that we're going to show and this is going to have a little fun in addition to using the lambmbda function syntax as opposed to using binders and preexisting puns we're going to use the lambda function and then in addition to that we're also going to use the find if not method and find if not as you might imagine basically negates it implicitly negates the predicate so we don't have to negate anything anymore so let's go ahead and take a look at find if not。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_186.png)

![](img/841b7f0aa929ea6656b076d5a9def536_187.png)

![](img/841b7f0aa929ea6656b076d5a9def536_188.png)

And I think this is another one of those methods that actually is not where you might think it is。

 so let's take a look at find if not。

![](img/841b7f0aa929ea6656b076d5a9def536_190.png)

And maybe we'll get lucky， maybe we won't。

![](img/841b7f0aa929ea6656b076d5a9def536_192.png)

嗯。So。

![](img/841b7f0aa929ea6656b076d5a9def536_194.png)

So find if not is also something that's defined and basically it's just the negation it just negates the predicate so it's kind of like using a negator but it hardcodes that into the actual algorithm itself so you can see here's find if not and if you look around you'll find the source code for it。



![](img/841b7f0aa929ea6656b076d5a9def536_196.png)

So if you take a look， we use find if not and then we write a lambda function that's just going to go ahead and take in the parameter I which we use auto for so it's a generic lambda function and it's going to return I greater than three and since we're using this with find if not we don't have to negate it anymore and so it's going to return the first element that's not greater than three Okay so far so good and we print those results now I'm just going to show you not to and not two is basically the binary version of not and you might wonder when would you ever use it and the answer was not very much and here's one example where you could use it although it turns out it's probably not the best way to make it be sorting so we're going to use it for sort we're going to start at the beginning and the end of the vector and we're going to sort it and we're going to sort it in descending order by using not two on the binary funter less so basically this is equivalent to greater。



![](img/841b7f0aa929ea6656b076d5a9def536_198.png)

![](img/841b7f0aa929ea6656b076d5a9def536_199.png)

![](img/841b7f0aa929ea6656b076d5a9def536_200.png)

![](img/841b7f0aa929ea6656b076d5a9def536_201.png)

![](img/841b7f0aa929ea6656b076d5a9def536_202.png)

![](img/841b7f0aa929ea6656b076d5a9def536_203.png)

![](img/841b7f0aa929ea6656b076d5a9def536_204.png)

So not too less is basically greater and just for kicks if you don't want to use not two。

 you could use not function and that would also work nicely here as well and this is really the reason why they've gotten they've deprecated not one and not two because not function can do the job of not one and not two without you having toly add one and two to the call when you invoke the negator。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_206.png)

Okay， so。

![](img/841b7f0aa929ea6656b076d5a9def536_208.png)

That's the code， let's go ahead and run the code， and then I'm going to show you the print results method。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_210.png)

And you can see here what it does is it goes ahead and skips over。

 it goes finds the first element that's not less than not sorry not greater than three。

 which is of course one and then it prints the results out and then the final thing we do is we go ahead and we sort it。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_212.png)

Not less， so it's in descending order。

![](img/841b7f0aa929ea6656b076d5a9def536_214.png)

The last thing I want to do is I want to show you this very interesting print results method。

 this is a different way of doing things and it works nicely here because we're not trying to print the entire container we're just trying to print it from wherever the iterator came back up to but not including the end so here's what we do we're going to make this thing be parameterized by an input iterator it's a template it's a generic print results function and it takes a first and a last if first does not equal last that means that we actually found something with our iterator and so that we're going to do is we're going to copy from the first input iterator。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_216.png)

![](img/841b7f0aa929ea6656b076d5a9def536_217.png)

![](img/841b7f0aa929ea6656b076d5a9def536_218.png)

![](img/841b7f0aa929ea6656b076d5a9def536_219.png)

![](img/841b7f0aa929ea6656b076d5a9def536_220.png)

![](img/841b7f0aa929ea6656b076d5a9def536_221.png)

Up to but not including the last element。 And then we're going to go ahead and use our Ostream iterator to write the results out。

Well， the interesting question is here， Ostream itertor wants a type。

 It wants inch or double or float or employee record or whatever we're dealing with。

 So how do we actually get that Well what we're going to do is use a little bit of type deduction magic that's also been added more recently to C plus plus called decal type and decal type is this cool sort of。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_223.png)

![](img/841b7f0aa929ea6656b076d5a9def536_224.png)

Template metaprogramm type system mechanism where you give it a value in this case， star first。

 So whatever type we've got here， star first is an instance of the iterator type that we've got and decal type then statically converts that into the type that star first corresponds to。

 which in our particular case happens to be in。 So that means we're going to end up using Ostream iterator。

Less than inch greater than And so that's a way of being able to let the compiler deduce the type from the parameter that was passed in as the first parameter or the second parameter to our print results method So this is a really cool little technique this is helps us to write more generic code without having to do all kinds of other awkward things of passing in type parameters and so on。

 So this makes it really clean really concise and we can stick to just passing in。😡。



![](img/841b7f0aa929ea6656b076d5a9def536_226.png)

![](img/841b7f0aa929ea6656b076d5a9def536_227.png)

![](img/841b7f0aa929ea6656b076d5a9def536_228.png)

Input iterator ranges， and then we can use decal type to deduce the final type。



![](img/841b7f0aa929ea6656b076d5a9def536_230.png)

Okay so those are the things that I had wanted to cover in the session today。

 so at this point we've covered binders and you've seen kind of the old school bind first bind second binders。

 you've seen the newer binder approach which is bind which has been a little bit itself sort of quasideprecated even though it's fairly new people typically say you know stick with using lambmbda functions although quite honestly once you get used to this somewhat strange syntax of bind it's not too bad and I'll actually show you in upcoming sessions how you can nest binders which is pretty cool。

😡。

![](img/841b7f0aa929ea6656b076d5a9def536_232.png)

And then the other thing we talked about， of course today。

 our main focus was on negators and you saw the old style negators not one and not two。

 as well as the newer style negators， which are the newer style negator。

 which is the not function or not underscore FN negator so hopefully this was helpful to you if you enjoy the content。

 please like and subscribe and of course also feel free to follow me on Twitter。😡。

So thanks very much and I look forward to seeing you again soon。

