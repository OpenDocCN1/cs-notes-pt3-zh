# 【全集】慕尼黑工业大学 计算机编程：从入门到实战 中英字幕 p29 Lecture 29 - 对象数据类型 -BV1WFrTBZExY_p29-

![](img/d6b4fb2f86fc3baf36aa37ab89e87acc_0.png)

Welcome back after the break and let's get started with our third unit today where we would like to talk a little bit more about object data types。

 so as a quick review， we already have seen the different wrapper classes。

 Boolean character and our six integer and floating based numbers。

That have a different precision and different length in terms of memory。

 And they basically help us to use generics like the list， like the point or like the shelter。

 if you would want to do that with。对。Primitive types。Inside of the wrappper class。

 and they also help us to work more object oriented。 On the other hand。

 they have small performance drawbacks and memory drawbacks。

 You need more memory to store them and wrapping and unwrapping values is considered as an additional overhead。

So if you have a performance intense application， you might not want to use them if you want to work completely object oriented and use the full idea of interfaces。

 abstract classes， inheritance， and generics then， you should use Reper classes。

Reper glasses have a typical constructor where you can define the type based on the primitive type。

 They are like integer with an end double with a double。

 There's also one that allows you to parse a string into this data type。 So I can， for example。

 say new integer。 And then I give a string5 into it。 And then the。

Constructor automatically parses the string into an integer for me or throws a number format exception if this is not possible because you use letters that don't belong to an integer。

And the constructor then returns an integer object for a string。

 So it basically allows you to convert this automatically without invoking a method。

There's also a parse， a corresponding parse method that you could use。

 but the constructor might be more convenient in many cases。

All of them offer specific equals classes， and they basically return true if the object contains the same in value as the other object for an integer or if the object contains the same double value for a double and so on。

And they have similar things for all other classes。 Yeah， like in the here。

 you have a float that also throws a number form an exceptional。 And， of course。

 a float might contain letters， but might， they must follow a very specific format。

 So if this is not possible， the constructor fails。They have certain features。

 all the classes that we can use except char have a parsing method， aesthetic parsing method hoops。

And where you can also pass a string， this works quite similar to the constructor。

 So instead of new integer with a string， I can also say integer dot parse integer。And they all have。

Consts， min value and max value in order to allow you to work with those。

 So this is also quite convenient for the primitive data types。 you don't have that。

 They will overflow and you can't easily get them in and max value out of the box。

And additional auxiliary functions are available for the character class， for example。

 you can recognize stitchtits， convert them to lower case letters， uppercase letters， and so on。

 so again， the object oriented thinking behind that makes it powerful and provides you a basic functionality that you can reuse and that you don't need to implement。

All the numerical wrapper classes， such as integer float， are having a common super class number。

 which is abstract。 We've seen that。 So you can't really create a number object， but it allows us to。

 again， reuse certain code and also use them as generic upper bound。

When we deal with generic data types。With the limitation that we've seen previously。

 number does not allow to use the simple mathematical。Calculations like plus minus and so on in an。

 in a generic way。 Yeah， So this is actually missing in Shava。

 There are other programming languages that offer something like that， but in Chava， it's not。

 unfortunately not possible。A few specific additional aspects。

 double and float offer negative infinity and positive infinity and something that is a wrapper for not a number NAN。

 and this basically happens if you divide a double or float value by0。

 sometimes you get an arithmetic exception because you cannot divide by0 and for those two you would get not a number as a return value so if you then print the double value to the console。

 it says NA AN and you need to make sure to be able to handle that。

There are also tests for infinity and whether it's not a number。

 So if the is infinity is not a number method， you can check that。

 They are available for double and float as static methods where you need to pass the double and the float。

 but also as object method。 So if you're sure the object is not null。

 you can use the object method If the object might be null， it's more safe to use the。

Static class method。Another important object data type in Javava that is provided by the JBM itself is string。

 you've already worked with it quite often， and we'd like to give you a few more methods and help you with a few more methods stringing actually offers a lot of different methods we just collected the most important ones here。

 you can find a lot more in the reference documentation online。An interesting one is index off。

 so if you would like to get the index of a string or a substr。With in the string。

 then you can use this method and you can use it either with one argument or with two arguments starting from a specific index。

 Yeah， So if you know this is a long string and certain words are appearing multiple times。

 but you're not interested in the first one， you're just interested in the first occurrence after some time。

 then you can use the second method。You have something to get the character at a specific index。

 So if you have hello and you wna get the character at index0， it will be an H。In index1。

 it will be an E and so on。 So this is， again， backed up by an array starting with counting at 0。

And this returns a char， but this can be converted in a character， raper class。

 or you can also then convert it again in a string in case you would like to get a string。

You can replace single characters with new characters。 This is quite good for string manipulation。😊。

Notice that you always， and this is important。 you always get a new string。

String is an immutable class。 You can't change the string within the class itself。

 It always will return a new one， and the existing one will stay。 This is quite important。

You can get the substrs based on a specific begin index that is inclusive and a specific end index that is exclusive。

So the end index itself will not be taken into account for the new substr。And what is quite powerful。

 you can split a string based on certain words， simple words。

Or characters like white space or commerceas。Or even based on regular expressions。

 you will learn more about regular expressions in a later workshop for now。

 you can basically use the split method， for example， if you have a comma separate file。

 comma separate value files， CSV， that's what is behind Excel， by the way。

 then in order to get all the strings， you could say please Tra split the big string。

Based on the comma。And then you get a string array with all the values in your comma separated value file。

And last but not least you can strip white space。 This is quite handy when you deal with user interfaces because sometimes users type in their name。

 but then they have a space or sometimes they have additional white spaces like taps or new lines and you basically would like to get rid of them and strip does that for you。

 but only for all the trailing in the end and all the leading white spaces。

 So if you have a sentence with white space in between， this is not removed。

 but everything in the beginning and in the end is removed。

And then you don't need to take care of it。There are many more methods。

 but those are the most important ones that you should be able to use。 Yeah。

 so if there is a homework exercise， if there is a supervised exerciser in the team project。

 later on， we assume that you know those methods and that you can use them， but again。

 sometimes there are multiple ways how to achieve a result。

 It's not that specific exercise asks you hey， this can only be done with this particular method， No。

 sometimes you have multiple ways to achieve this。The good thing is in Intelliche。

 And this is something that I'd like to show you again。

 because and I I kindly ask you to carefully watch how I do that。 Yeah。

 those are important skills to navigate through code。😊，In Intelliche。

 you can easily also go to the definition of a string and how you can use it。 Yeah， So if I。

Just hover over it。I get the documentation。The string class represents character strings。

 all string literals and Java programs are implemented as instance of this class。

 and so strings are constant and so on。 so you can read everything。 It's a big documentation。Yeah。

So that's quite powerful already just hovering a bit。And then if you command， click on Mac or C。

 click on Windows， you can jump into the source code of this class。

And see what kind of methods and attributes we have in here。And， of course， this is a bit cumbersome。

 Yeah， you don't need to understand all this code， but we can also open the structure。

And then look through it and see what kind of methods we have。 And， of course。

 this is something that you hopefully know if you have a string。Like this。And you click the dot。Then。

 you get。呃。Drop down， kind of a drop down menu with all the different methods that the class offers。

And this is typically sorted by。Priority， yeah， so the ones that are。

Invoked more often are at the top。 And then at some point， it basically。lists them alphabetically。

Right， so， and then you can even type and get recommendations based on what you have started。

 what kind of method you would like to use。 And this is really powerful and experienced programmers。

 They master this skill。 They are so fast because they can quickly navigate through code and understand what's going on。

And this is something that I'd also like to show you if you would like to understand。

Who is invoking your code？ Yeah， let's assume we have a shape。Let me or this one here。

 if you would like to understand who is invoking this method， you can also command click on it。

 unfortunately， no one is using it， but maybe I'll go to shape and then I see shape if I command or control click it is used in two different places so I can also get a usage and then navigate back and if I would now do some Java documentation here。

Yeah， shape is abstract。And should be subcast。Then I can also hover over it and get this as a documentation in here。

 So this is really powerful。 Make sure that you understand this in order to be able to navigate through code。

 And this makes you really faster， a lot more faster。 in the end。😊。

Here's an example how to split a string， let's assume you have this comma separated value string。

 one， comma 2， comma 3， comma 4， and then you'd like to get all the values in an array and calculate the sum out of it。

 you can invoke the split method and provide a comma。

As the regular expression or word in order to split it here。

And then we can basically iterate over all the string values using a an enhanced for loop。

And use the integer parse int method， or alternatively the new integer method in order to get the int value of it and sum it up with the plus equals operator in our variable sum。

 and then this would output 10。What would be the output if I add comma 5。15， exactly。Yeah， so。

Here we have a very nice example of the split method that we just learned about and the parse int method that we have seen before。

 And， of course， parse int could throw an exception。

 and we will learn how to deal with those exceptions in the next unit。

We already talked about the Chaba collection frameworks。

 which is very handy when it comes to those different object data types。

 because it is based on generics， and we've already covered how to implement or how to use a set。

 how to use a list。 And we've basically implemented our own queue。

 but the collections framework already has a queue might have a slightly different API in terms of method calls。

 but you can still use it。 You don't have to come up with your own queue。 So that's nice。

 And this is something that we can work with。 Now， what we did not cover yet is the map。

Interface and specific implementations of the map。 And this is what we would like to do next。

 So we would like to look how map works。 And then there will be a small exercise with maps that you can learn how or practice how to use it。

Java UT map is a generic type， and instead of just having one type definition， it has two。

 a key K and a value we。It is an interface。 We now actually know what interfaces means。

 so it specifies certain methods that implementing classes such as the hash map need to offer。And we。

 with the interface， we can actually easily ex exchange the implementation later on。

 So whenever we use the interface， we can exchange the implementation easily。 Yeah。

 the interface here is typically the static type or compile time type。😊，And implementation。

 hashmap or link hash map or anything else that you might come up with。

Is the runtime type next to the new operator。And with that， we make sure that later on。

 we only use methods provided by the interface and nothing that depends on the concrete implementation。

A map is similar like a mathematical function。 You have like an input， and you map it to an output。

 a key to value。It's important that the key basically follows a set。

 so it can only contain each key once。 It's not possible to have in a normal set as in a normal map。

 It's not possible to have multiple values。For the same key， it's always one key， one value。

And this can， for example， be used in order to cache results。 So if I have a very computational。

 intense result， and I'm sure I need it later on。And someone might invoke this again。

 I could cache it， right， I could cache the input data as a key and the output data as a value。

 And this is where those maps are also heavily used in practice。Of course。

 we have different implementations， the most common one that many people use is the hashmap。

And then we have certain methods that we can use。 First of all， we need to define the map。

 And now you see we have two elements。 In this example， we have string and integer。

 but we could use any types that we want。 Even our own types that we define can be used in here。

And if we use string in inte， we could， for example。

 count words with a word count and put put is the method to add elements。 Yeah， it's called put。

 We put something into the map。AndWe could add university as a key and 10 as a value。

And we can add highbraron as a key and5 as a value。When we do that。

 we actually populate the map with key value pairs。 Now。

 if we would put again an element with the same key。

 then the original value would be overwritten with the new one。

Yeah so put either inserts a new key value pair。Or overrdes an existing one with the new value。

Because every key only appears in once。We can invoke the size and find out how many elements we have in the map。

 We can get the value of a specific key， using the get method。And print it to the console。

 like here 10。If we do that for a key that is not part of the map， we get null。

 and then we would also print null in here。 Yeah， so Moonian is not part of the word count yet。

Therefore we get now， and we can also use the enhanced for loop。

 but it's a bit cumbersome to use it directly on the map。 it's possible。

 but then you would need to work with an entry which is a bit weird。

 and most of the times you are interested to iterate over it based on the keys or the values。

And that's much easier。 So what you typically would do is you say four string word word count keyet。

And then the word is the key， and then you can invoke the get method in order to get the value。

In some cases， you also like to just iterate over the values。

 and then you can invoke word count dot values。And。

Quick question to the people who did not go to the next slide yet。

What will keyet return and what will values return。Which type would it return， Any idea。I mean。

 the method is called key set， so。What does keyet probably return if you need to guess。

Multiple keys that we can iterate on in a loop。But which data type is it？A string。 no， no string。

Sorry。Int， no， int would make if you can't iterate over int。Yeah， that's the question。

 Is it an array， Is it a list， Is it a set， Is it something else。It's a set， exactly。 Yeah。

 the method is called， maybe， maybe this was easier。 I don't know。 But the method is called key set。

 Yeah， It provides you a set of the keys that are used in the map。😊，Yeah， so。

A map only has one key at a time， which is similar to a set。

 a set only has an element once at a time。 We cannot have multiple elements in a multiple values in a same values in a set。

Now， what does the dot values method return？Any idea。An array， a key list， a set， a list。

 another map。Any ideas？That's a list。 And why is it a list well。

It could be the case that multiple keys have the same value。 That's perfectly fine。

 So we could add moonian。 We could say word count， word count， put moonn Hiian and then5 again。

 This is perfectly fine。 And if we get all the values， this means they can appear multiple times。😊。

So a set is not appropriate。 we need to use a list。That's the basic semantics behind it。We have。

An overview of the most important methods here。 We can get the size。

 We can check if the map is empty。 We can put a key value pair。We can get the value for a given key。

 We can remove certain keys。 We can check if the map contains a key， and if it contains a value。

 we can get the key set， as we've seen， this is a set， we can get the values。

 which returns a collection， but in fact， it's a list。😊。

And we can clear the map and remove all case with all their values。Any questions regarding the。Map。

 data type and。All the methods that you see here。It's an important data type。

 and you might use it in many different。Programs in the future。 So we'd like to practice it。

 and we'd like to do the following exercise as a playground exercise now。

 So this is not an Artemis exercise。 You need to solve it in your playground。And the idea is。

 we have a static method called factorial。And this factorial method。

Basically calculates the factorial number of a positive integer。And the factorial number is defined。

 for example，5 is the factorial of 5 is 5 times 4 times 3 times 2 times 1。 So it's 120。

And this method does that using a for loop。Now， the thing is that calculating this is quite expensive。

 right， especially for large numbers。And in order to improve this， we'd like you to use a map。

As a caching mechanism。So please create a hash map。With the key long as the input。

 the number that we insert like 5。And the value is also along。 That's the output of the method。

The factorial of 5 is 120。Now。In order to improve the performance， we only calculate the factorial。

 if the cache or a map does not。Have the result yet。If it has the result。

 we simply get the result and return it immediately。That's the idea。Okay。

 so copy and paste this into your playground。 I'll do this as well。Here we go。Can be any playground。

Or mainine？Functional。And now what we can do first is we create a main function and we call this。

 we say factorial of five。And then， I say。System out printline factorial of 5。

And then we'll try it out。And then， it should return。120。 Okay， I have some。Issues in my code。

 Let me get rid of the other classes。 Now it should work。Yeah，120。 And， of course。

 you can also do higher numbers。 Yeah， So 25， I'm not sure if this can be displayed。 Yeah， it can。

 Yeah， So this is still possible if you go to 55。It's still not super。Slow。

 but the numbers get larger and larger。 And， of course， this leads to 55 iterations within the loop。

 So this is not the definitely not the fastest one。 And if you go to， I don't know，100。 Yeah。

 maybe let's do crazy number 1255。Then we get 0。 Why is this the case。

 Because we basically overflow the long and it doesn't really make sense to do that anymore。 Yeah。

 so let's do something reasonable。 Let's do it two times with 40。

 And this means we calculated two times。 And already with 40， we have an overflow。 Yeah。

 So you see the numbers。 They really increase quickly。 So let's do it with 20。 Yeah， with 20。

 we get two values and they are perfectly fine。 But it means we need to do this two times。

 And what I kindly ask you now is to use a map。And if the result is already available。

 return it immediately。😊，If not， you'd simply do the normal calculation。

 but at the end of the calculation， you put it into the map。

 So the boiler blade is like this you to do。Instantiate a map。That's your first to do。Second， to do。

Check if the map。Contains the key。Number。If yes， return。The value of it。Otherwise。

 we simply do the calculation， and then we have a third to do here。Store a new。Key number。And value。

Our factorial。In the map。And that's basically it。 Yeah。

 copypy and paste the code into your playground。And。Keep the implementation like it is。But。

Do something in the beginning to improve the performance and make sure in the end that if you don't hit the map and if you can't return it immediately。

 you will store the result accordingly。And you have now around five to 10 minutes to work on this。

 and then I'll show you an example solution。Okay， please stop working for a moment and listen again so we can quickly look at the example solution。

This is how it works and you see I did it slightly different here。And basically。

Created the map already beforehand。 Yeah， so this is， of course， not correct。 Yeah。

 I can't create it within here。 Insiating the map must be。Done beforehand， otherwise， it will not be。

Available afterwards， sorry for this mistake， but we'll clarify this here and this is because it's a static method。

 this also needs to be static and it can be final。 This is optional and it's a map with the key long and the value long we call it cache and it's a new hash map。

And now we can in the beginning of the factorial method。

 check if the cache contains the key based on the input based on the number that we have here。

 if this is the case we print it and return the value by using the get method immediately。

If this is not the case， we do the normal calculation here and then catch the result in the end。

Let's see if that works。 So if I update my implementation now with this。Example solution。Here we go。

 I need to import。The map and the hash map to make this work。

 so make sure you have import Shava UT hashmap and Sha UT map。And now， I can。

Invoke this again and do it。Five times with 20。And then I see。How often I do the multiplication？

They are based on the additional print statement in the for loop。And。I'll do that quite often here。

 Yeah， so this is the expensive part in our example。 but for the second calculation。

 I hit the cache and there's no multiplication and so on。That's basically the idea here。

Are there any questions regarding the？Exampleles solution。Anything that is unclear。How to use a map。

So， again。Important， we define it outside of the function。 In the beginning。

 we check if for the given input， there is already an output。 If yes， we return it immediately。

 If not， we do the expensive calculation。And then cash the result in the end。In practice。

 those caches are used very often and you need then to think about when do you invalidate results in a cache。

 how much memory does the cache actually use and how much performance do you save of it and this is always a tradeoff so even if you have a cache you need to maintain it and you potentially also need to delete it in case the results get outdated。

If there are no more questions， we'll do another quick break and continue at 5 past 5 with the last unit for today。



![](img/d6b4fb2f86fc3baf36aa37ab89e87acc_2.png)