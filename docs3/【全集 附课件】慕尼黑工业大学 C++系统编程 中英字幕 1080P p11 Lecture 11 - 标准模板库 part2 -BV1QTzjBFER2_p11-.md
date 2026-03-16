# 【全集 附课件】慕尼黑工业大学 C++系统编程 中英字幕 1080P p11 Lecture 11 - 标准模板库 part2 -BV1QTzjBFER2_p11-

Yeah。Hello and welcome everyone to another lecture of the systems programming and C++ Practic course in which today we will continue talking about the standard library and some related concepts that we are still missing。



![](img/f2e7035ed81b94923930bff65e576a63_1.png)

![](img/f2e7035ed81b94923930bff65e576a63_2.png)

And， and the most important of these missing concepts is our first topic for today， which。

Refers to function objects and functions in general because there is a couple of things that we can do with those that we haven't seen so far。

 So right from the beginning of this course， we have learned that a regular function in C++ is initially not an object and this has a couple of implications。

 So for example， we cannot pass functions as parameters functions cannot have any state themselves。

 of course， they could be member functions of a class which then can have state and there are a couple of other implications as well。

 for example， we cannot define references to functions and so on。

This is a little bit constraining because we would， sometimes， for example。

 be like to be able to pass a function as a parameter for this reason， C plus plus additionally。



![](img/f2e7035ed81b94923930bff65e576a63_4.png)

Defins a socalled function object named requirement， which applies to an arbitrary type T。

 which has a couple of properties。 And the first of these obviously has to be is that T has to be an object。

 and then the core property is that the function call operator is overloaded for this type T。



![](img/f2e7035ed81b94923930bff65e576a63_6.png)

And that this function called operator takes a suitable argument list， which of course can be empty。

 and such objects are then often referred to as funcs。

 and we can do fun things with these for because we are now able to pass such a funter as a parameter to a function。

 for example， or anything else that we are able to do with with a regular object。



![](img/f2e7035ed81b94923930bff65e576a63_8.png)

![](img/f2e7035ed81b94923930bff65e576a63_9.png)

Now， of course， this requirement wouldn't be complete without some examples and luckily there are already a number of valid function objects defined in C++ without requiring us to do anything。



![](img/f2e7035ed81b94923930bff65e576a63_11.png)

The first valid function object is a pointer to a function。

 and then we also have Lada expressions which we're going to take a look at today and finally stateful function objects in the form of classes。

 so if you just take this function object requirement literally and implement a class that fulfills these requirements then of course you also get a valid function object。



![](img/f2e7035ed81b94923930bff65e576a63_13.png)

Although regular functions and a reference to a function by just typing the name of a function are not function objects themselves。

 they are not objects so they don't fulfill the first requirement of a function object。

 we can still use them in the same way， because implicitly if you just write the name of a function。

 this is converted to a pointer to this function。

![](img/f2e7035ed81b94923930bff65e576a63_15.png)

![](img/f2e7035ed81b94923930bff65e576a63_16.png)

And this is the first type of function object that we're going to take a look at today。

 So functions are not objects。 We've repeated this quite a few times already， so。



![](img/f2e7035ed81b94923930bff65e576a63_18.png)

You would initially think because we have when we talked about memory layout and these things we talked about the address of an object and since we said functions are not objects。

 you could think that functions do not have an address。

 but this is not true because any function just consists of a sequence of assembly instructions and if you think back to the dynamic memory lecture we talked a little bit about the process layout。



![](img/f2e7035ed81b94923930bff65e576a63_20.png)

You will maybe remember that the actual assembly code that makes up our executable is at some point loaded into memory and of course this assembly code then is simply a number of bytes starting at a specific memory address and then taking the pointer of a function makes a little bit more sense because this function pointer is simply a pointer into the region of memory where the actual assembly instructions that make up your function are located so even though functions are not objects。

 we can still declare pointers to functions which then point to these assembly instructions。



![](img/f2e7035ed81b94923930bff65e576a63_22.png)

![](img/f2e7035ed81b94923930bff65e576a63_23.png)

![](img/f2e7035ed81b94923930bff65e576a63_24.png)

![](img/f2e7035ed81b94923930bff65e576a63_25.png)

![](img/f2e7035ed81b94923930bff65e576a63_26.png)

No， I'm sorry。

![](img/f2e7035ed81b94923930bff65e576a63_28.png)

Now for simplicity， we will mostly talk about function pointers to non-me functions so to free functions and these can be declared as shown here so first we have to specify the return type then and this is important always in parentheses we have to write the an identifier for our function pointer preceded by the the star character here and then after this identify our in parentheses we have to write out the argument list and these once again as for regular function declarations can either contain named。

Prameters or unnamed parameters， I think。Now， once that we've declared such a function pointer here。

 of course， we would like to be able to initialize this in some way， and once we've done this。

 this allows us to pass functions as parameters to other functions such as constructors or member functions or free functions。



![](img/f2e7035ed81b94923930bff65e576a63_30.png)

![](img/f2e7035ed81b94923930bff65e576a63_31.png)

And some common examples of this， just to give you some motivations are to maybe pass a custom comparison functions to the STD sort function。

 which we're also going to see today， or a little bit more generically just passing a colveX to some method that you can then use for whatever logic you're implementing。



![](img/f2e7035ed81b94923930bff65e576a63_33.png)

![](img/f2e7035ed81b94923930bff65e576a63_34.png)

And such a function pointer can then be invoked in the same way as a function just that it's not a static function that you've declared somewhere。

 but this function pointer that can point to any function that matches the signature of your function pointer here。



![](img/f2e7035ed81b94923930bff65e576a63_36.png)

![](img/f2e7035ed81b94923930bff65e576a63_37.png)

So to give you an example here， let's take a look at this short code snippet here。So first。

 we declare a function call function， which does nothing else but take a function pointer and then and two arguments and then invoke the function point the function through this pointer with these two arguments。

 So it's rather useless， but it's useful to demonstrate how we can actually declare such things。

 So the first。

![](img/f2e7035ed81b94923930bff65e576a63_39.png)

A parameterrameter of our call function function here is the actual function pointer。

 and we see that the declarationation matches what we've seen on the previous slide。

 So first comes the return types so this function returns an integer， then comes an identifier。

 So a name for this function pointer just following the syntax， as it's required。

 So parentheses star and then the identifier。 And then finally we have our argument list indicating that this function。



![](img/f2e7035ed81b94923930bff65e576a63_41.png)

![](img/f2e7035ed81b94923930bff65e576a63_42.png)

The functions that we want to pass into this call function should take two integers as arguments。

 And then， of course， we have our two actual arguments here。 And then finally。

 we call the function point the function through this pointer by de referencing the function pointer。



![](img/f2e7035ed81b94923930bff65e576a63_44.png)

And then I'm supplying our two arguments here。Yeah。

We could also let the compiler automatically dereference our function point。

 So this is demonstrated in our second snippet here， which。

 apart from this small difference does exactly the same as our first code snippet。

And then just to demonstrate how we can call such functions that take function point as we now define two functions that actually match these signatures here so the add function here matches the signature of the function pointer in our first call function and this add for function here。

 matches the signature by our of our second call function function here。

 and then in our main method we simply call these rather useless functions one time we simply pass the name of our add function。



![](img/f2e7035ed81b94923930bff65e576a63_46.png)

![](img/f2e7035ed81b94923930bff65e576a63_47.png)

So here we see an example of automatic implicit conversion from a function to a function pointer。

 but we could also make this explicit by taking the address of the function that we want to pass as a function pointer here。

Any questions so far？Yeah。Looking good。 So let's move on。

 So as you can probably guess from this example。Function pointers are pretty annoying to use because you have to write a lot of text to make them work and they just look plain ugly。

 they make it really hard to see at one glance what's going on here。



![](img/f2e7035ed81b94923930bff65e576a63_49.png)

And there are some。Additional more subtle disadvantages of function pointas as well。

 because with function pointas， for example， you cannot easily capture the environment at the point when you call a function。

 so all variables that affect the semantics of a function have to be passed as actual parameters to this function and you cannot have something like a local function within other function so returning to the example of using SDD sort with a custom comparison function。

 maybe you just need this custom comparison function within another helper function。

 but if we only had function point us， we couldn't really make this comparison function local。

 we would have to define it as a free function and then of course it would be visible outside of the function where we actually need it。

And as a more flexible alternative to this two function pointers that resolve most of these disadvantages。

 C++ additionally defines Lada expressions， which on a high level construct a closure which then stores a function together with some environment that affects how this function works。

And in particular， this means that Lada expressions can capture variables from the scope where they are defined。

 and then within a lambda expression， you can refer to these variables that you have captured from the scope where they were defined。

Of course， this is a very high level description， so let's dig a little bit deeper and take a look at we can how we can actually define such Lada expressions。

 so the general expression syntax is as follows， so we have square brackets。



![](img/f2e7035ed81b94923930bff65e576a63_51.png)

Containing a captureist， then we have regular parentheses， which contain the parameter list。

 and then。We have an arrow here， just like the pointer arrow that you already know followed by the return type of our Lada expression and then finally in curly brackets。

 we have the actual body of our Lada expression。

![](img/f2e7035ed81b94923930bff65e576a63_53.png)

So the capture list here in these square brackets specifies the parts of the environment that should be stored in the state of our closure。

But this list can also be empty and there are some specialized syntax alternatives for the catchist。

 and we're going to take a look at those in more detail in just a second。The parameter list here。

 of course， is just a comma separated list of function parameters。

 This works in exactly the same way as function parameters for regular functions。

 And then this return type here。Can be omitted in which case you don't write the arrow followed by the return type。

 but simply directly the body after the parameter list， if you do omit the return type。

 then the return type of the Lada expression is deduced automatically from the return statements that you write inside the Lada expression body here。



![](img/f2e7035ed81b94923930bff65e576a63_55.png)

Now， let's go through these different parts of a Lada expression。One by one。

We'll start by taking a look at some general Lada expression examples before then going into a little bit more detail about the single parts just before because this isn't really dependent on anything that you're right and we've already seen that the list of captures here can be empty in which case your Lada expression doesn't capture any environment so it doesn't have access to any variables that are outside of the Lada expression body and。

As you can imagine in this case， we now have a stateless lambda expression and the cool thing about stateless Lada expressions is that they are implicitly convertible to function pointers with the matching signature so if you have a matching return type and a matching parameter list of stateless Lada expression you can use this lambda expression wherever you would have to use a function point or otherwise and here we can already see why we don't really have to use function point as anymore because anywhere where a function pointer is required we can just use a stateless Lada expression。



![](img/f2e7035ed81b94923930bff65e576a63_57.png)

![](img/f2e7035ed81b94923930bff65e576a63_58.png)

![](img/f2e7035ed81b94923930bff65e576a63_59.png)

![](img/f2e7035ed81b94923930bff65e576a63_60.png)

![](img/f2e7035ed81b94923930bff65e576a63_61.png)

Now if you take a closer look at this expression syntax here。

 you will see that intentionally we did not write this in the form of an assignment or an initialization。

 and this is because there is one peculiarity about Lambda expressions in C++ which is that they do not have a type that you can directly name so any Lambda expression that you declare gets a unique unnamed class type that's determined by the compiler and that is internal to the compiler。

 so you cannot write out the type of such a Lada expression year。



![](img/f2e7035ed81b94923930bff65e576a63_63.png)

![](img/f2e7035ed81b94923930bff65e576a63_64.png)

![](img/f2e7035ed81b94923930bff65e576a63_65.png)

And because of this， whenever we want to assign a Lada expression to a variable。

 we have to rely on template argument deduction， so either we have to use auto as the type of this variable or simply we have to for example。

 if it's enclosed in a template class， we have to use a deduced template parameter as the type for our variable to which we want to assign a lambda expression。

Now， now with the theory， for a second， let's take a look at a couple of examples here。



![](img/f2e7035ed81b94923930bff65e576a63_67.png)

So the call function here is simply the same call function that we saw in the previous example here I taking a function pointer in two arguments and here in this example we can now MC demonstration of how we can use a lambda function in place of a function pointer so here we define a lambda function that is stateless it has no captures it takes two integer arguments and it simply returns the sum of these two integers you can also see that we omitted the return type here so the compiler will automatically deduce it to be int from this return statement here which just adds to ins together and finally you also see that in assigning this to a variable we use auto because once again we cannot directly name the type of this lambda expression here in our code。

And now we can invoke this call function here and simply pass this Lada here as the first parameter because it is implicitly convertible to a function pointer being a stateless lambda function。

 but of course we can also do something else with this Lada expression here， for example。

 directly call it just like any other function by providing two arguments to the two parameters of our lambda function and using the regular function call syntax。



![](img/f2e7035ed81b94923930bff65e576a63_69.png)

![](img/f2e7035ed81b94923930bff65e576a63_70.png)

Yeah。Now， something that we have to keep in mind if we do omit。If， if we， if we， for example。

 return Lada expressions from functions is that they have unique types。

 even if they are semantically equivalent and a constructed example to demonstrate this is shown in this code snippet here。

 So we have a deduced return type here from our get function。



![](img/f2e7035ed81b94923930bff65e576a63_72.png)

![](img/f2e7035ed81b94923930bff65e576a63_73.png)

Klier function。 And then depending on a condition， we simply return these the sematically same lambda expression two times。

 But since these are two different lambda expressions， each of them gets a unique。

Type from the compiler and because of this compilation will fail because we now return two different unique types from a function。

 and then of course， the compiler cannot deduce the return type anymore because it's ambiguous。

Any questions so far regarding the basic syntax and usage of Lada expressions？그。Looking good。

 So let's move on to Lambda captures。 And this is a rather large topic when it comes to Lambdas because you can do so many different things with these Lada captures。

 So on a high level， it's pretty straightforward what they do。

 So in this capture list you simply specify what the state of your lambda expression is made of。



![](img/f2e7035ed81b94923930bff65e576a63_75.png)

![](img/f2e7035ed81b94923930bff65e576a63_76.png)

And what does this mean in a little bit more detail。

 these a Lada captures can refer to variables with automatic storage duration in the surrounding scopes up to the enclosing function。

 and it can also refer to the this pointer in the surrounding scope if this running scope contains a this pointer at also this means if we are in a class member function。



![](img/f2e7035ed81b94923930bff65e576a63_78.png)

![](img/f2e7035ed81b94923930bff65e576a63_79.png)

![](img/f2e7035ed81b94923930bff65e576a63_80.png)

。So anything that you specify in this capture list。

 either explicitly or implicitly then makes up the state of the Lada expression。

 and you can refer to this state from within the body of a Lada expression。Now。

 what makes this a little bit more difficult is that these captures can either be by copy or by reference。

 and of course， and the Lada expression behaves differently depending on how exactly you capture your state。

So if we opt for capture by copy， then for every captured variable in the Lada state。

 a copy is created， and this is then put in the state of the Lada function so here。

You essentially copy the entire state of your Lada function。

 and then from that point on it's immutable regardless of what you do outside of the Lada expression。

 the state that was copied into the Lada expression remains unchanged。In contrast， obviously。

 if we capture by reference， then instead of copying the variables。

 we simply reference them from the Lambda state。And then of course。

 any changes to the captured variables will be visible within the Lada and any changes that we make to these references from within the lambda body will be visible outside of the lambda。



![](img/f2e7035ed81b94923930bff65e576a63_82.png)

![](img/f2e7035ed81b94923930bff65e576a63_83.png)

Once again， regardless of how we capture our state。

 these captures can then be used in the Lada expression body just like regular variables or references。

 so here nothing specialist going on。Now， how can we actually write this in our code in general。

 the captures are simply provided as a comma separated list of individual captures。



![](img/f2e7035ed81b94923930bff65e576a63_85.png)

![](img/f2e7035ed81b94923930bff65e576a63_86.png)

Which in case of by copy capture is simply the identifier of whatever we want to capture or an identifier followed by an initializer。

If you want to do it by reference， then the syntax is essentially the same just that we prefix the amperserson to our identifier。

And once again， and we've already seen this on the previous slide。

 these identifiers must refer to automatic variables in the surrounding scopes。

And then this identifier can be used just like a regular identifier within the lambda body。

 and of course， every variable may only be captured once capturing a variable more than once doesn't really make sense。

Yeah。In addition to these individual comma separated captures。

 we can also have a capture default as the first capture。

 and here we simply write an equal sign to capture everything by copy or an ampersent if we want to capture everything by reference and by everything this means that any variable in the surrounding scopes can now be used within the Lambda body。



![](img/f2e7035ed81b94923930bff65e576a63_88.png)

![](img/f2e7035ed81b94923930bff65e576a63_89.png)

嗯。And if we have such a capture default， this specified de capture type for all variables that we do not explicitly capture afterwards。

 So we can， for example， have。

![](img/f2e7035ed81b94923930bff65e576a63_91.png)

A default by copy capture and then follow this by a by reference capture for some specific variables that we want to capture by reference instead of by copy。

Also quite logically， if we do have a capture default such as a default by copy capture。

 then subsequently we can only specify diverging capture types so we cannot have a capture default by copy and then explicitly specify that we want to capture some other variable will also by copy。

 this is already encompassed by the capture default here。



![](img/f2e7035ed81b94923930bff65e576a63_93.png)

![](img/f2e7035ed81b94923930bff65e576a63_94.png)

Now， once again， this is a lot of theory， so let's take a look at a couple of examples here。



![](img/f2e7035ed81b94923930bff65e576a63_96.png)

So in the first example here， we simply take a look at the various capture types and how we can specify them。

 So here。We just have two local variables within our main function。

 and then we define a number of lambda expressions with different capture types。

So our first Lada here simply captures I by copy， this is the specific explicit capture list syntax that we've seen on the previous slide and the second Lada here does the same only that it captures I by reference instead of by copy。

Now we can also use capture defaults as we've seen。

 so here we have a capture default by reference and then subsequently we specify that we want to capture I by copy。

 So this means that within this Lada here J is captured by reference because it is encompassed by the capture default here and I is captured by copy because we explicitly specify I diverging capture type here and of course we can do the same thing the other way round have a capture default by copy and then specify that we want to capture something else by reference。



![](img/f2e7035ed81b94923930bff65e576a63_98.png)

And the final two Lada expressions here will result in compiler errors because here we have a capture default and then subsequently an explicit capture of with the same capture type。

 which of course， as we've seen on the previous slide is not possible。Now。

 this is just the syntax how we can specify capture types much more interesting， of course。

 is how we can actually use this。So here we have an example of the differences between capture by copy and capture by reference。



![](img/f2e7035ed81b94923930bff65e576a63_100.png)

So。Let's assume that once again， we have this one local variable here within our main function and then two Lada functions。

 one of which captures this variable by copy and the other of which captures it by value。

 and both of these and simply refer to this captured variable in the return statement and add 42 to this。

Now the difference becomes obvious when after declaring these lambda expressions here。

 we change the value of I because now in Lada 1 we copied the value of I at the point of declaration here so the state of lambda 1 will remain unchanged within Lada 1 I will still refer to 42。

 but in Lada 2 since we captured I by reference we will now whenever we execute Lada 2 C through this reference that the value of I actually change to0 and because of this。



![](img/f2e7035ed81b94923930bff65e576a63_102.png)

If we evaluate these M2 lambda functions subsequently， we will see that Lambda 1 returns 84。

 so adding 42 to the value of I that was copied at the point of declaration here， which is 42。

 whereas lambda 2 will return 42 because of course here I references to the I and the closing score which we changed M to0 here。



![](img/f2e7035ed81b94923930bff65e576a63_104.png)

![](img/f2e7035ed81b94923930bff65e576a63_105.png)

Both of these capture types have their uses， of course。

 which one specifically you want to use depends on the context in which you are using the Lambdas and we will see a couple of general guidelines when specific capture types might make sense in just a second here。



![](img/f2e7035ed81b94923930bff65e576a63_107.png)

![](img/f2e7035ed81b94923930bff65e576a63_108.png)

Before that， just a sign note that we can also capture this pointer。Essentially。

 in the same way as regular captures with the difference that capturing this by copy actually copies the entire current object and not just the pointer and。



![](img/f2e7035ed81b94923930bff65e576a63_110.png)

If we capture I want to capture this by reference， we simply write nothing and then here you can also just deduce what's happening because here we copy the pointer value。

 but of course accessing anything through this copied pointer value will still refer the original to whatever the contents of the current object R at the time of invocation。

 whereas if we copy the current object， then the lambda will behave as if we copied a variable into the Lada state。



![](img/f2e7035ed81b94923930bff65e576a63_112.png)

And to illustrate this， we have essentially the same example as on the previous slide just that now our I value here is a member of astruct4。

 and instead of capturing I in our lambmbda functions。

 we now capture the this pointer once again the lambda 1 does this by copy。

 So here we copy the entire current object into the lambda state。

 whereas Lada 2 does it by reference where we just copy the this pointer into our lambda state and then of course referencing。

A class member here will reference the state of the original object。

 and now just in the same way as in the previous example， if we now change and the value of I。

 this will only affect Lada 2， because in Lada 1， we created a copy of the current object。

 and because of this， we will get exactly the same output as in the previous slide。

Where Lada 1 returns 42 and Lada 2 returns 84。Yeah。One thing that we have to be careful of here。

Is that。If we have a by copy capture default， this will not by default。

 actually copy the current object， but simply copy the this pointer。

 So even with a by copy capture default， the this pointer will be captured by reference。

 So this is all that this example demonstrates here。

 it's identical to the previous example with the difference that instead of explicitly capturing the thiser。

 we have capture defaults here。 and there you see that our output now differs because even with a by copy capture default。

 and we only copy the this pointer and not the current object。 So in both lambdas here。

 I refers to the I within the current object。 So if it's changed this will be reflected in the return value of our Lada here。



![](img/f2e7035ed81b94923930bff65e576a63_114.png)

Another thing that we have to be very careful of related to Lambda captures is the lifetime of objects。

 and this is something where sometimes youre forced to use a by copy capture instead of a by reference capture if you cannot ensure that the lifetime of your by reference captured values is long enough。



![](img/f2e7035ed81b94923930bff65e576a63_116.png)

And just to demonstrate this here， let's take a look at another example。

 So here we have a unique pointer， which we then。

![](img/f2e7035ed81b94923930bff65e576a63_118.png)

Capture by value。 So this is an example of the initializer syntax for captures。

 So here we define an inner capture， which is initialized to the pointer value that's contained within this unique pointer here。

 and then we simply dereference this pointer within our lambda function and return the value here。

 Now， of course we can call this lambda function and everything works fine。

 unless we at some point decided to end the lifetime of the contained object because now our lambda state here actually contains a dangling pointer at the point of declaration here。

 we copied the pointer that was contained within our unique pointer here。 But now at some later time。

 we reset the unique pointer and of course， this pointer then points to some uninitialized memory that has already been cleaned up and now calling F2 once again we'll try to dereference this pointer and result in undefined behavior。



![](img/f2e7035ed81b94923930bff65e576a63_120.png)

![](img/f2e7035ed81b94923930bff65e576a63_121.png)

![](img/f2e7035ed81b94923930bff65e576a63_122.png)

![](img/f2e7035ed81b94923930bff65e576a63_123.png)

Probably Amazonazan would complain of a use after free here。



![](img/f2e7035ed81b94923930bff65e576a63_125.png)

So this is just to demonstrate that lifetimes are important to keep in mind whenever you capture something。

 usually this doesn't have a big impact if you just use Lambdas as local variables within a function。

 but it can become very relevant once you start passing Ladas around and maybe even storing them in member variables of your classes because then you always have to keep in mind that the Lada will stay alive as long as the class that contains this with stellar alive。

 but stay alive but the captures that you specified might not stay alive as long。



![](img/f2e7035ed81b94923930bff65e576a63_127.png)

![](img/f2e7035ed81b94923930bff65e576a63_128.png)

Any questions up to this point？Right， so let's wrap up our discussion of function objects。

By talking about the final。Possibility to define function objects So we've seen function pointers。

 we've seen Lada expressions， the final way in which we can define a function object is a stateful function object。

Which behaves similar to a stateful lambda expression with some minor differences。 So so far。嗯。

We've seen that functions are generally stateless， so a function pointer doesn't have any state Lada expressions allow us some limited state state keeping。

But we cannot do everything that is possible with this Lada state in particular。

 we cannot access the state of a Lada expression from outside of the Lada expression。

And if we want to do things like this then we have to define a stateful function object where we explicitly keep the function state in a surrounding class with some member variables and then we can keep arbitrary state and we can also access this state explicitly from outside of our function object and in some situations this might be useful just a small contrived example here is something like an addstruct which contains as its state value and then invoking this function object with a parameter simply adds the value that we store within our addstruct here to the parameter value。



![](img/f2e7035ed81b94923930bff65e576a63_130.png)

![](img/f2e7035ed81b94923930bff65e576a63_131.png)

![](img/f2e7035ed81b94923930bff65e576a63_132.png)

![](img/f2e7035ed81b94923930bff65e576a63_133.png)

![](img/f2e7035ed81b94923930bff65e576a63_134.png)

And here you now see that we can define such a function object here。

 set the value to some to something and then invoke this my adder， just like any other function。

 we could also pass it to。to a function that takes a lambda as a parameter and then invoking this will simply add whatever we store it in the state to the parameter。

 the key difference to a lambda being that after initialization we can still change the state of this adder object here so at some later point we can increase the value and then invoking this my adder function object will return something different than before。



![](img/f2e7035ed81b94923930bff65e576a63_136.png)

![](img/f2e7035ed81b94923930bff65e576a63_137.png)

What is also。Sometimes useful when I'm working with functionss in general is the STD function wrapper。

 which is a general purpose wrapper for anything that is callable in essence。

So it's defined in the functional object。And with SD function， you are able to store。

 copy and invoke the Re target， which might not be possible with a function itself。

 but in order to implement this functionality， SD function potentially requires dynamic memory allocations and often add some unnecessary overhead to plain function objects because of this unless you absolutely require something like SD function。

 it should be avoided where possible。

![](img/f2e7035ed81b94923930bff65e576a63_139.png)

![](img/f2e7035ed81b94923930bff65e576a63_140.png)

Now we do have a question in the chat， is it possible to have an arbitrary number of parameters for for a function object。

 yes。You can have as many parameters to your function call operator as you want。

 and this applies to function pointers to Lada expressions and to stateful function objects。

 and in case of stateful function objects， of course you can make the state of your function object as big as you want by simply specifying however many members you need for your function object。



![](img/f2e7035ed81b94923930bff65e576a63_142.png)

Now， returning to SDD function just。A general demonstration of how， how we would。

Could use SDD function， so here we just have a simple helper function add2， which takes an integer。

 adds to and returns this once again as an integer。

 and then we could assign this to an SDD function object for which we have of course to define the correct table parameters here and then we can invoke this SDD function object just like the add2 function itself。



![](img/f2e7035ed81b94923930bff65e576a63_144.png)

![](img/f2e7035ed81b94923930bff65e576a63_145.png)

m with no big surprise this year。

![](img/f2e7035ed81b94923930bff65e576a63_147.png)

So one potential use case for SDD function is precisely the example that we've seen before。

 We have some helper function which from which we want to return a specific factor。

 we've seen that we cannot directly return Ladas from such a function because then we would get an ambiguous return type。

 but we can return an SDD function object which wraps these Lada expressions。

 and this is exactly what we do in this example here。



![](img/f2e7035ed81b94923930bff65e576a63_149.png)

![](img/f2e7035ed81b94923930bff65e576a63_150.png)

![](img/f2e7035ed81b94923930bff65e576a63_151.png)

![](img/f2e7035ed81b94923930bff65e576a63_152.png)

So apart from some boiler plate to make this code interesting。

 we once again have this condition here and depending on the condition。

 we return two different Lada expressions which are then implicitly converted to an instance of STD function and as opposed to the previous example we now get no compilation errorssq to ambiguous return types because our return type is always this one STD function type here。



![](img/f2e7035ed81b94923930bff65e576a63_154.png)

![](img/f2e7035ed81b94923930bff65e576a63_155.png)

![](img/f2e7035ed81b94923930bff65e576a63_156.png)

And then of course， we can use this get function helper here to obtain a function and then invoke this factor in this case without any arguments because our Ladas and the STD function do not return any parameters。



![](img/f2e7035ed81b94923930bff65e576a63_158.png)

Yeah。Now。A final。A final list of small guidelines when working with function objects is that in general。

 code that intends to call function objects should rely on templates。

 So what does this mean a bad example of a function that takes a function is shown here where we explicitly state。

That we want to take a pointer to a function that returns in and takes no arguments。

 and then just for the sake of example， it simply evaluates this function。Why is this bad。

This is bad because if we take a look at the example down here。

 we artificially constrain ourselves to just function pointers or stateless lambdas so。If we have。

 for example， a function stateful function object here。

 and we cannot pass this to our bad function here because it is not a function pointer and this function here is not implicitly convertible to a function pointer either and we would get the same error if instead of a function。

 we wanted to use a stateful Lada here。 this would also not work because a stateful lambda is not implicitly convertible to a function pointer。

What should we do instead， instead of explicitly specifying the function pointer that we want to use。

 we can simply template this function here。And let the compiler figure out what the actual type of our functionta here is。

 So here we don't put any restrictions on what， what we can pass to our good function here。

 apart from that， it must be callable without any arguments。 this applies to stateless， Lambdas。

 this applies to state full lumbs， Lambdas， and this applies to stateful function objects。

 So to these good function here， we can pass whatever we want。

 as long as it's callable without any parameters and returns and integer。



![](img/f2e7035ed81b94923930bff65e576a63_160.png)

![](img/f2e7035ed81b94923930bff65e576a63_161.png)

So this is the usual way in which you want to implement any code that takes functions and then does something with them always try to use templates for that。

Right， so this concludes our discussion of function objects。

 if there are any final questions regarding this， please let me know now before we move on to our next topic。

I。Right， everything's looking good so far。 So let's move on now that we know about function objects。



![](img/f2e7035ed81b94923930bff65e576a63_163.png)

![](img/f2e7035ed81b94923930bff65e576a63_164.png)

We can take a look at another component of the standard library， which is the algorithms library。



![](img/f2e7035ed81b94923930bff65e576a63_166.png)

And the algorithms library essentially defines all kinds of operations on ranges of elements that are usually specified by two iterators。

 an iterator to the first element and the past the end iterators or an iterator past the last element of the range that we want to consider。



![](img/f2e7035ed81b94923930bff65e576a63_168.png)

And within this algorithms library we have functions for sorting， for searching， manipulating。

 and so on such ranges of elements。Yeah。You've already seen in the previous lecture that pointers essentially can be treated just like iterators and these functions within the algorithms library can be used on ranges of pointers or ranges of any appropriate iterator types。

So the core algorithms library is split across four headers that are listed here in this lecture here we will just focus on the algorithm header because this bundles the most relevant parts。

 this of course doesn't mean that the other parts are not useful if you are interested you can always take a look at the reference documentation and see for yourself which kind of functionality is contained in these other headers here。



![](img/f2e7035ed81b94923930bff65e576a63_170.png)

Now the first very useful function within the standard library is the SDD sort function that we've already talked about today a little bit。

 which does what its name implies， specifically sorts all elements in a range first to last in ascending order。



![](img/f2e7035ed81b94923930bff65e576a63_172.png)

![](img/f2e7035ed81b94923930bff65e576a63_173.png)

，The syntax here is just sort with two random axis iterators for first and last and some requirements on the elements。

 in particular the elements have to be swappable and the elements have to be move assignable and move constructable if we think about this a little bit this makes sense。

 we cannot sort without swapping elements or moving elements from one place to another。



![](img/f2e7035ed81b94923930bff65e576a63_175.png)

S theD sort itself does not guarantee the order of equal elements。 so it's not stable。

 There are alternatives。 We'll see this towards the end of this part of the current lecture。

 and of course。SDD sort guarantees that it will need on the order of endlock and comparisons for sorting。

Just a brief example down here， nothing too surprising。

 we can define an STD vector and then sort it using the STD sort function by simply passing the begin and end it us off this STD vector to the sort function and subsequently the elements of our vector will be sorted。



![](img/f2e7035ed81b94923930bff65e576a63_177.png)

Of course。Right now， sort is already useful but a little bit useless because we can only sort an ascending order。

 but of course we can change this by supplying a custom comparison function and which can be supplied to the sorting algorithms。



![](img/f2e7035ed81b94923930bff65e576a63_179.png)

This comparison function is then supplied as a function object。

 so here we can apply what we've learned in the first part of today's lecture with some additional requirements on this function object。

 in particular the compare named requirement， which just states that this function object has to establish a strict weak ordering on the elements。

 which。

![](img/f2e7035ed81b94923930bff65e576a63_181.png)

![](img/f2e7035ed81b94923930bff65e576a63_182.png)

Once again， kind of makes sense if we want to order。

 we need the comparison function to be well behaved so that sorting actually makes sense。

The somewhat informal syntax of this comparison function is that it。

Should take two parameters and return a booleion， and it should return true if and only if a is considered to be less than B。

 according to some strict week ordering less here。And a simple example where this is useful is if we want to sort the same vector as the previous example but instead of sorting it in sendinging order。

 we want to sort it in descending order， then we can supply a custom comparison function here。

 which considers one object to be less than another when the numeric value is greater and then of course this will invert the order in which our elements will show up in the final sorted vector here。



![](img/f2e7035ed81b94923930bff65e576a63_184.png)

So sometimes SDD sort may not be the optimal choice。

 so there are some further sorting operations in the algorithms library。

 one problem with STD sort is that it does not necessarily keep the order of equal ranked elements and that it always sorts the entire range that you pass to SDD sort which may be unnecessary。

 for example， for top K queries。

![](img/f2e7035ed81b94923930bff65e576a63_186.png)

Now if you want to keep the order of equal ranked elements。

 there's SDD stable sort with the same signature as STD sort。

 but of course since it has to include some additional logic to keep the auto of equal rank elements it's a little bit more expensive than STD sort in general and if you don't need equal rank elements to bes you should prefer STD sort over STD stable sort。

If we have top K areas， we can use SDD partial sort。

To just partially sort a range and if you simply want to check sortedness of a range there are the is sorted and is sorted until HeA functions in the algorithms library once again。

 if you determine that you would like to use one of those please take a look at the reference documentation where the actual signature and semantics are explained in much more detail than in this lecture of course。



![](img/f2e7035ed81b94923930bff65e576a63_188.png)

Yeah。Now。Once we've sorted something， it's only natural and to start searching within a sorted range and for this。

 the algorithms library also offers a variety of operations。

 both un sorted and also on unsorted ranges， but of course this is especially interesting for sorted ranges sincere we can。

Sometimes guarantee more optimal complexity bounce than we can on unsortted ranges。

Especially if we have to do repeated lookups into some data structure。

 then usually sorting will pay up so the initial cost of sorting the range and will be offset by the much faster lookups into a sorted range。

 but if you only need。

![](img/f2e7035ed81b94923930bff65e576a63_190.png)

A couple of lookups throughout the entire lifetime of your program。

 then maybe you can also get away with simply searching on an unsorted range instead of sorting this range。



![](img/f2e7035ed81b94923930bff65e576a63_192.png)

![](img/f2e7035ed81b94923930bff65e576a63_193.png)

Of course， there are some additional arguments against sorting。

 maybe you are simply not allowed to sort a range of elements because it comes from the outside and its order is immutable and also if you have frequent updates or insertions。

 this becomes a little bit more difficult if you have to maintain sorted order and it also becomes a little bit more expensive to keep a range sorted in the presence of updates and de insertions。



![](img/f2e7035ed81b94923930bff65e576a63_195.png)

The general semantics of these search operations are that they return an iterator that points to the result of the search operation。

 and if a search operation was unsuccessful， then these operations usually return the past the end iterator of the range that you supplied to the specific search function here。

 So if search was successful， you get an iterator somewhere between first and last exclusive and if searching was unsuccessful。

 then you get this last iterator here。

![](img/f2e7035ed81b94923930bff65e576a63_197.png)

![](img/f2e7035ed81b94923930bff65e576a63_198.png)

![](img/f2e7035ed81b94923930bff65e576a63_199.png)

On unsorted ranges， there's the following functions defined by the algorithms library。

 so first you can find the first element that satisfies some criterion there's SDD find。

 which just takes an e value and then searches for this value in a range and there's also find if and find if not which instead of a value。

 take a predicate which is then evaluate it for each element of a range and they return the first element that matches the supplied predicate here。

Yeah。You can also search for a range of elements within another range of elements with the STD search function and finally this is also sometimes useful you can count matching elements either by supplying a specific value to the SDD count function or once again a predicate to the count if function here。

But of course， this is only a selection of some useful functions there are many more useful operations。

 and once again we would like to refer you to the reference documentation for an overview of those。

Just as a brief example here， for S defined find， for instance。

 let's assume we have some vector V containing some elements and then。

And we invoke the SD find function on this range。 So the range is specified by passing the begin and end iterwriters of our vector。

And for STD find， we have to supply an actual value here。

And then we get an iterator to the first element that has the specific value and as expected。

 we can see that the distance of this iterator from the begin is3 because the first element with value 7 here is at index3 within our SD vector。

And of course， if we search for something that's not contained within our vector。

 we get the end iterator of our range as a result from the defined operation。



![](img/f2e7035ed81b94923930bff65e576a63_201.png)

A question from the chat is whether the actual algorithms used for sort can vary between implementations of the standard library and whether it is always in place。



![](img/f2e7035ed81b94923930bff65e576a63_203.png)

The actual algorithm is not specified by the standard library。

 there are some pretty strict constraints on the complexity both in terms of memory and time that SDD sort must meet and in practice this means that SDD sort is almost always implemented as quick sort。



![](img/f2e7035ed81b94923930bff65e576a63_205.png)

With。Some some additional magic so SDD sort implementations are usually quite involved to exploit presorted ranges and make sorting efficient in general。

 but the specific algorithm is not specified by the standard library if you're interested you can take a look at the documentation for STD sort and read through all the complexity requirements that STD sort must meet。



![](img/f2e7035ed81b94923930bff65e576a63_207.png)

Yeah。Alright， moving on with our examples here， let's take a look at SDD find if。

 so we've seen SDD find where we always have to supply a value that we' are looking for in case of SDD find if instead of a value we supply a preddicate。

 which once again is passed as a function object as you can see down here。

 where we use SDD find if to find the first element which is not even which we can implement by。



![](img/f2e7035ed81b94923930bff65e576a63_209.png)

![](img/f2e7035ed81b94923930bff65e576a63_210.png)

Passing this Lada expression here， it takes a single argument of the matching type and then simply returns a booleion if our predicate matches and a boan if our predicate matches and once again we get an iterator to the first element that matches our predicate here。

 in our case the iterator will have a distance of two from the begin because the first element that is not even is an index 2 with an our vector。

And， of course。Find if not inverts our predicate here， which is shown in the second example here。

 so here we our predicate checks whether a value is less than or equal to 7 and find if not finds the first element for this predicate is not met。

 which of course is going to result in the end iterator because all of our elements in the vector are less than or equal to 7。



![](img/f2e7035ed81b94923930bff65e576a63_212.png)

Now， if we do have sorted ranges， then the standard library provides us with optimized search operations。

 which internally use binary search， obviously， since we are operating on sorted ranges and therefore guarantee。



![](img/f2e7035ed81b94923930bff65e576a63_214.png)

![](img/f2e7035ed81b94923930bff65e576a63_215.png)

![](img/f2e7035ed81b94923930bff65e576a63_216.png)

A complexity of log n comparisons when the range is given as a random access iterator。

This is very important to keep in mind here， this complexity guarantee only applies when we have random access iterators。

 if we have， for example， a linked list which does not provide random access iterators。

 then the complexity is still linear in the number of iterator increments。

 even though our range may be sorted here。

![](img/f2e7035ed81b94923930bff65e576a63_218.png)

![](img/f2e7035ed81b94923930bff65e576a63_219.png)

And just like the search operations on unsorted ranges， our binary search operations can of course。

 employ custom comparison functions。

![](img/f2e7035ed81b94923930bff65e576a63_221.png)

The most important of these and binary search functions are STD binary search。

Which simply checks whether an element is present within a sortred range。And then。

We can use SD lower bound or SDD upper bound to search for boundaries of a range of elements with the same value and this if we actually need both bounds。

 we can do this with one function called to SDD equal range。

 which searches for all occurrences of a certain element。



![](img/f2e7035ed81b94923930bff65e576a63_223.png)

![](img/f2e7035ed81b94923930bff65e576a63_224.png)

![](img/f2e7035ed81b94923930bff65e576a63_225.png)

So you will maybe notice the symmetry between these functions and the functions that are defined on sorted containers in the standard library and this symmetry is in fact intentional。

 so just like you can use SD lower bound within a set or a map。



![](img/f2e7035ed81b94923930bff65e576a63_227.png)

You can use SD lower bound or upper bound on any other sorted range that is by chance。

 not a set or a map。

![](img/f2e7035ed81b94923930bff65e576a63_229.png)

But the semantics are exactly the same here。So once again， just a couple of examples here。

 so STD binary search， as we've seen， simply checks whether an element is present within a range and therefore returns pool。

 if we meet the actual values， then we have to use STD equal range here。

Apart from that using SDD binary search is quite straightforward。

 so once again we specify a range of elements here and a value that we're looking for and then we get a return value of true if our range contains a value 3 here in this case and a return value of falses if it does not contain evalue such as0 in this second example down here。



![](img/f2e7035ed81b94923930bff65e576a63_231.png)

SDD lower bound gives us an iterator that points to the first element that is not less than the search values or the first element greater than or equal to the search value。

 So if we apply this to our example vector here and search 4 M3。



![](img/f2e7035ed81b94923930bff65e576a63_233.png)

We will get an iterator to this first three here because this is the first element that is greater than or equal to our search value here。

 but this also works for values that are not exactly contained within our range。

 So if we do an S lower bound search for0， then we will get the begin iterator because the first element that's greater than or equal to0 is this one at the begin of our iterator here。

And likewise SDD upper bound gives us the first element that is greater than the search value。

 so if we once again search3 here， this will now give us an iterator to this four here because this is first element greater than the search value and you can already see by combining SD lower bound and ST the upper bound you get exactly the range of all elements that have the value that we're looking for so SDD lower bound points us to the first element and SD the upper bound points us to the first element past the final element with the same value you can use the iters returned by SDD lower bound and STD upper bound to iterate over all elements with the same value as the one you were looking for。



![](img/f2e7035ed81b94923930bff65e576a63_235.png)

![](img/f2e7035ed81b94923930bff65e576a63_236.png)

And this is precisely what SDD equal range does， so this gives us as a return value。

 this pair of iterators， the begin at the end of a range and this is exactly identical to using SD lower bound and SDD upper bound to separately acquire these two iterators just that the implementation is probably a little bit more efficient since we don't have these separate to binary searches for determining these iterators here。



![](img/f2e7035ed81b94923930bff65e576a63_238.png)

![](img/f2e7035ed81b94923930bff65e576a63_239.png)

![](img/f2e7035ed81b94923930bff65e576a63_240.png)

Now。The final part that is quite useful that we want to highlight of the algorithms library here is the support for permutations within the algorithms library。

Which allows us to iterate over permutations in lexographical order。

So this is quite useful if if for any reason you need to permute any range of elements。

 then you can use this functionality。

![](img/f2e7035ed81b94923930bff65e576a63_242.png)

To iterate over all permutations of a range in lexicoographical order。 But， of course。

 this has some requirements。 So we at least need some bi directionional iterators for this to work。

 Once again， the values have to be swappable。 Obviously， since we。

Since we want to permute them and they have to be comparable， so by default。

 the order that specifies this lexiographical order of elements is determined by using the less than operator。

 but we can also supply a custom comparison function so in that case our comparison function is used and the elements themselves to not to have a meaningful implementation of the less than operator here。



![](img/f2e7035ed81b94923930bff65e576a63_244.png)

![](img/f2e7035ed81b94923930bff65e576a63_245.png)

Quite often， we simply need to permute a range of integers and to initialize such a dense range of elements。

 we can use the SDD Yota function， which initializes a range。

Of integers or anything else that is inable， and then we can use the SDD next permutation or previous permutation functions to iterate over these permutations in lexicoographical order。



![](img/f2e7035ed81b94923930bff65e576a63_247.png)

So let's take a look at these functions in a little bit more detail。 So first of all。

 the STD Yota function initializes a dense range of elements。



![](img/f2e7035ed81b94923930bff65e576a63_249.png)

So we give this function a range of elements as to iterate us and then a starting value for our denses range of elements。

 and then what it will do is it will iterate over this range of elements and fill them with increasing values starting at this start value that we specified and these values are incremented using the overloaded increment operator。

 so of course it works for integers， but it also works for any custom object that overloads this increment operator。



![](img/f2e7035ed81b94923930bff65e576a63_251.png)

And just。As an example here let's assume we have an array of integers on the heap that contains five elements。

 then we can call the SDD Yota function with the begin and end pointers of this array starting at a value of 2 and subsequently our heap array will now contain the value 2。

3，4，5，6， so a dense range of increasing elements starting at the value 2 here。



![](img/f2e7035ed81b94923930bff65e576a63_253.png)

。Now， once we have such a dense range of elements or any other sorted range of elements， we can。



![](img/f2e7035ed81b94923930bff65e576a63_255.png)

Use the STD next permutation function to reorder the elements within such a range to the lexiographically next permutation。



![](img/f2e7035ed81b94923930bff65e576a63_257.png)

嗯。And this function will return false if the current permutation was the lexiographically last permutation。

 so this means that the range is sorted in ascending order。

 then lexiographically there is no greater permutation and if we started at a range that was sorted in descending order。

 we have now iterated through all permutations of this range。So as an example。Let's。

I think there's a typo here。 So if the current permutation was leicographically last permutation。

 then the range is of course， sorted in descending order。

 so usually we started a range thats sorted in the sendinging order and then permuted until until its' order and descending order。

 So this is a type of this should be descending here。



![](img/f2e7035ed81b94923930bff65e576a63_259.png)

![](img/f2e7035ed81b94923930bff65e576a63_260.png)

But regardless， let's take a look at this example。 So here we do have a range that is sorted in ascending order and then by calling STD next permutation。

We see that the first call will swap3 and2 and then I'm calling next permutation once again and we'll move to the lexiographically next permutation。

 which keeps the3 as the lowest element but swaps this two and1 in the first two places here。And。

 of course， SD previous permutation does exactly the same thing only that it moves in the。

In the opposite direction。 So nothing too special going on here。



![](img/f2e7035ed81b94923930bff65e576a63_262.png)

And then finally， just an outlook on what else there is in the algorithms library。 there are。

 of course， many more operations。 there's things like SDD Min and SDD Max that are also defined over a range of elements instead of two elements。

 there is SDD merge and in place merge for merging of sorted ranges if。



![](img/f2e7035ed81b94923930bff65e576a63_264.png)

![](img/f2e7035ed81b94923930bff65e576a63_265.png)

You for example， implement a merge sort yourself but still want to rely at least in parts on the standard library。

 there is a multitude of set operations such as set intersection union and difference。

 there's a lot of heat functionality things like SDD unique pointer， for example。

 are also part of the algorithms library theres functionality for taking a random sample of elements。

 there's swapping of elements and all kinds of modifications to ranges so we have only looked at read operations on ranges。

 but there's also a lot of modification operations that you can apply such as copying elements rotating or shuffling elements within a range。

 and this is even still not an exhaustive lists so once again the reference documentation contains the full list of operations within the algorithms library。



![](img/f2e7035ed81b94923930bff65e576a63_267.png)

![](img/f2e7035ed81b94923930bff65e576a63_268.png)

So with this。We are through our quick spotlight of the algorithms library。

 Are there any final questions on this part？

![](img/f2e7035ed81b94923930bff65e576a63_270.png)

。Everything appears to be。Clear so we can move on to yet another library within the standard library。

 which is the Rangs library。

![](img/f2e7035ed81b94923930bff65e576a63_272.png)

![](img/f2e7035ed81b94923930bff65e576a63_273.png)

So this ties in nicely to our discussion of the algorithms library and specifically operations on ranges of elements。

Because what we see there is that usually we specify ranges as a pair of iterators。

 so the first iterator and a pass the end iterator。



![](img/f2e7035ed81b94923930bff65e576a63_275.png)

And ranges essentially give us an abstraction of this iterator pair description of ranges and simply say a range contains a range of elements and we don't really care about whether they are specified by a pair of two iterators or in any other way。



![](img/f2e7035ed81b94923930bff65e576a63_277.png)

![](img/f2e7035ed81b94923930bff65e576a63_278.png)

So this notion of a range of elements is formalized by the range concept in the ranges header。

 and we can iterate over the elements of a range in the same way as over the elements of a container or the elements of a range that is specified by such an iterator pair here。



![](img/f2e7035ed81b94923930bff65e576a63_280.png)

This Rangs library here was newly introduced in C++ 20 so compiler support may still be incomplete。

 I do know for effect fact that MSVC doesn't fully implement all operations on the ranges yet and also we've encountered some bugs in the GCC implementation of ranges so if you use them just be prepared for a little bit of pain in case you hit such a case of bugs or incomplete implementation here。



![](img/f2e7035ed81b94923930bff65e576a63_282.png)

![](img/f2e7035ed81b94923930bff65e576a63_283.png)

Also because they were just newly introduced in C++ 20 large parts of the standard library。

 such as precisely the algorithms library， for example， don't make use of ranges yet。

 but if you write your own code that has to deal with ranges then it's certainly worth a thought of using this ranges library over this explicit iterate a pair description of ranges because they make a lot of things much easier as we will see in the following。



![](img/f2e7035ed81b94923930bff65e576a63_285.png)

And the main reason why they make some things easier is that we can take a view of such a range of elements。

 and then we can manipulate this view through socalled range adapters and these range adapters apply various transformations。



![](img/f2e7035ed81b94923930bff65e576a63_287.png)

To such a view or to the elements that are contained within such a view。



![](img/f2e7035ed81b94923930bff65e576a63_289.png)

And something that's also very nice is that such range adapters can be composed in a functional way to yield more complex composed transformation on a range of elements。



![](img/f2e7035ed81b94923930bff65e576a63_291.png)

So before we go a little bit deeper into the Rangs library， maybe a quick motivating example here。

 so something that occurs quite frequently is that we have an associative container or an SDD map or an SDD unored map。

 and we want to iterate over just the keys or just the values of this map。



![](img/f2e7035ed81b94923930bff65e576a63_293.png)

![](img/f2e7035ed81b94923930bff65e576a63_294.png)

Without the ranges library， we cannot really do that。

 we have to iterate over the elements within our map which are pairs of keys and values。

 and then we always have this pair of elements either we treated as a pair directly。

 then we have to access the key or the value depending on what we want or we use a structured binding。

 but then we have an unused variable within our structured binding which is also not too nice with the ranges library。

 what we can now do is we can take the map， which is implicitly converted to a range that views the elements that are contained within this map and then apply the keys transformation so the keys range adapter that is defined in the standard library to this view of the elements within our STD map which then simply results in another view on a range in which now we only have the keys of our elements here and then we can iterate over the elements within this range and only have the key as our iteration variable here。



![](img/f2e7035ed81b94923930bff65e576a63_296.png)

And correspondingly， the output will be13 since our map contains M keys1 and3。And of course。

 now that we have this general idea of what we can do with the R this library。

 I think it's quite easy to think of more complex transformations that would be quite cumbersome to implement without the support of these range adapters here。

 but that become very simple to implement and also very obvious if we employ these range adapters within our code。



![](img/f2e7035ed81b94923930bff65e576a63_298.png)

Now as we've already seen within our example here， most containers can directly be used as ranges。

 but of course， the detailed requirements are specified by the corresponding concepts within the range header。

 and in particular what's important here is that there is a viewable range concept which allows a range to be converted to a view which we can then transform further through these range adapters。



![](img/f2e7035ed81b94923930bff65e576a63_300.png)

![](img/f2e7035ed81b94923930bff65e576a63_301.png)

![](img/f2e7035ed81b94923930bff65e576a63_302.png)

So most of the time this is probably what we're going to use。

 so we have some container and then we view this container as a range of elements。

 but in some cases it might also be useful to directly create some commonly used views without constructing a dedicated container。

 So for this there is some so-called range factories that are defined。



![](img/f2e7035ed81b94923930bff65e576a63_304.png)

![](img/f2e7035ed81b94923930bff65e576a63_305.png)

In particular we can create an empty view， we can create a view that contains a single element and we can use we can create a view that contains repeatedly incremented values。

 so just like the SDD Yota function， this range factor is also called Yota and its semantics are essentially the same as for the SDD Yota function here。



![](img/f2e7035ed81b94923930bff65e576a63_307.png)

![](img/f2e7035ed81b94923930bff65e576a63_308.png)

![](img/f2e7035ed81b94923930bff65e576a63_309.png)

And once again， just as an example， once again， containing a little bit of functionality that we're going to talk about on the next slides。

 let's assume that we have a Lada function。That takes a value and returns the square of this value and then we have a loop over a composed view here in which we first generate a dense range of elements with the SDD views Yota range factory so once again we pass the begin and the past the end value here so this view will initially contain the values 1 to34 and then we transform this view with the square function here so we take each of the elements within our view here and apply this Lada function which returns the square of the element and then of course if we print the values that are in this composed view here we will see that these are exactly the square numbers from1 to 4。



![](img/f2e7035ed81b94923930bff65e576a63_311.png)

![](img/f2e7035ed81b94923930bff65e576a63_312.png)

![](img/f2e7035ed81b94923930bff65e576a63_313.png)

Now what we've seen here by using this pipe operator is the application of a so called range adapter。

 so such range adapters apply transformations to the elements of a range。



![](img/f2e7035ed81b94923930bff65e576a63_315.png)

![](img/f2e7035ed81b94923930bff65e576a63_316.png)

What they do is they take a viewable range as their first argument and return a view。

 so initially these behave just like function objects。And of course， as such。

 they may take additional arguments if this is required by the transformation。

What we've seen in our examples here is now an instance of the third property here。

 which is that the pipe operator can be used to chain unary range adapters。

 so a unary range adapter is a range adapter that just takes a viewable range and no additional arguments。



![](img/f2e7035ed81b94923930bff65e576a63_318.png)

![](img/f2e7035ed81b94923930bff65e576a63_319.png)

But there is， of course， a way to work around this， which we're going to see in just a second here。

Now， for now， let's stick with unary range adapters that just take a view as their first argument。

 then we can chain these unary range adapters in two different ways。

 So let's assume we have range adapters C1 and C2 and a range R。

So the functional the function call way to do this would be to just apply C1 to R and then C2 to the result of applying c1 to R。

 so this gives us the view that results from first applying C1 to R and then applying C2 to the result of this transformation。

Now with the pipe operator we can also write this as R pipe C1 pipe C2。

 which is semanally exactly the same， so this is just syntactic sugar for this notation here。

 but once again we do here is we first apply C1 to R and then apply C2 to the result of this previous operation year。



![](img/f2e7035ed81b94923930bff65e576a63_321.png)

![](img/f2e7035ed81b94923930bff65e576a63_322.png)

Both of these are exactly equivalent， so this is something that we can see in our example here。

We once again have our SDD map containing some values。And then with the functional syntax。

 we can simply iterate over the result of applying the reverse view to the keys view of our map。

 and of course， this will then print the keys contained in our map in reverse order here。



![](img/f2e7035ed81b94923930bff65e576a63_324.png)

Exactly， the same result could be achieved instead of。

Applying these range adapters by using the pipe composition syntax。

 so here you will see that the is the order of application here is reversed。

 we start with our map and then we first apply the keys range adapter and then we apply the reverse range adapter。

 but of course this is just syntactic sugar and the output will be exactly the same。

 namely we will print the keys of our map in reverse auto here。



![](img/f2e7035ed81b94923930bff65e576a63_326.png)

。So。With unary range adapters， it's clear how we can use them， but of course。

 many of the interesting range adapters such as the transform range adapter that we've seen in a previous example take multiple arguments but。



![](img/f2e7035ed81b94923930bff65e576a63_328.png)

![](img/f2e7035ed81b94923930bff65e576a63_329.png)

We can transform them into unary range adapters because they can be carried。

 So if we have a range adapter。

![](img/f2e7035ed81b94923930bff65e576a63_331.png)

C that takes some arguments A1 to A N， in addition to the range that every range adapter takes as an argument。

 then we can pass only the arguments to our range adapter。 So right C。Followed by our arguments。

 and then this object is a unary range adapter， essentially it's the current version of our multiple argument range adapter in which the arguments are fixed to specific values here。

And this means of course， that all three of the following expressions are equivalent。

 so the function called syntax of calling such a multiple argument range adapter would simply be past the range as the first argument followed by all the arguments that are required for our range adapter but we can use this current version here to first create a unary range adapter by only passing the arguments and then applying this unary range adapter to our range and then for unary range adapters we've seen that we can use the pipe operator so finally we can transform。



![](img/f2e7035ed81b94923930bff65e576a63_333.png)

![](img/f2e7035ed81b94923930bff65e576a63_334.png)

![](img/f2e7035ed81b94923930bff65e576a63_335.png)

This line here into the pipe composition syntax that we already know。

 where we first write R followed by the pipe operator and then of course this should be the current version of our range adapter。

 so just C parenthsesis A1 to AN， the R shouldn't be contained in this call here。



![](img/f2e7035ed81b94923930bff65e576a63_337.png)

And to give an example of this admittedly rather theoretical discussion。

 let's take a look at another code snippet。

![](img/f2e7035ed81b94923930bff65e576a63_339.png)

So once again， we have a list of numbers here and our square function that computes the square of a number。

 and then we can。

![](img/f2e7035ed81b94923930bff65e576a63_341.png)

rite the semantically same code in three different syntactic ways。

 so the first would be to use the function called syntax pass the range as the first argument and the parameter to the transform range adapter the function here as the second argument。

 and then we will of course print the square numbers from one to four here。



![](img/f2e7035ed81b94923930bff65e576a63_343.png)

The current functional syntax would be to first create a unary range adapter from our transform function by just passing the square functionor here and then applying this unary range adapter to our range of numbers here and the pipe composition syntax which we would probably usually use is then to first write our range followed by the composition operator here and the courage version of our range adapter。



![](img/f2e7035ed81b94923930bff65e576a63_345.png)

Of course when it comes to specific range adapters we've only seen a small selection of examples up to now there are many useful range adapters that are specified in the ranges header such as a filter adapter that use all elements that satisfy a predicate。

 the transform adapter that we've already seen which applies a transformation function to all elements and they these keys and values adapters which use the first or second elements of a range of pairs and many more for example。

 for skipping some elements from a range selecting specific elements from a range based on their indexes and so on。

 once again all of these are of course listed in the reference documentation。

Any questions on rangers？Yeah。Yeah。그。

![](img/f2e7035ed81b94923930bff65e576a63_347.png)

Alright， then so then let's move on to the final part of the standard library that we want to highlight because it is also quite useful。

 which is the random library， which as its name already suggests。

 defines pseudoran number generators and a variety of random number distributions that we can use to obtain all kinds of pseudoran numbers within our code this library is defined in the random header so if you want to use it don't forget to include this header here and it bundles several useful distinct components so one is in abstraction for random devices then of course the core component are various random number generators and then some rappers to generate actual numerical distributions from these random number generators。



![](img/f2e7035ed81b94923930bff65e576a63_349.png)

![](img/f2e7035ed81b94923930bff65e576a63_350.png)

Something that's that we cannot overstate here is that these this functionality here should always be preferred over functionality from the C standard library header because。



![](img/f2e7035ed81b94923930bff65e576a63_352.png)

The R function defined in the C standard library produces very poor random numbers。 so unfortunately。

 I lost the reference for this， but I read somewhere that in one implementation of run the lowest bit simply alternated between 0 and one。

 which is， of course， the opposite of a random distribution of bits。

 and this is especially serious if。

![](img/f2e7035ed81b94923930bff65e576a63_354.png)

Rand is used together with modello operations and we'll see and why this is so dangerous at the end of today's lecture。

 So if you need random numbers within your code your first。

Your first choice should be at the C++ random number library。

 Of course this library also has its limitations if you have some specialized needs。

 then you will probably need to use a thirdpart library anyway。

 but in this case we can assume that you know what you're doing so then you're on your own but apart from that never use the sealed standard library random number generators always prefer the C++ implementation of random number generators。



![](img/f2e7035ed81b94923930bff65e576a63_356.png)

![](img/f2e7035ed81b94923930bff65e576a63_357.png)

Now with that said， let's take a look look at how we can use this library。

At at the core of the random library， there are various pseudoran number generators。



![](img/f2e7035ed81b94923930bff65e576a63_359.png)

Which are actually not random number generators， but random bit sequence generators。



![](img/f2e7035ed81b94923930bff65e576a63_361.png)

That simply。Sample random bit sequences from a uniform distribution of bits of a given length。

 and these different generators have some slightly different properties， of course。



![](img/f2e7035ed81b94923930bff65e576a63_363.png)

That influence their behavior。 These random number generators can， of course。

 be seeed to get a reproducible sequence of pseudoran numbers。

 and they can be quality compared to compare the state of such a random number generator and something that can be quite annoying depending on what you want to implement。

 They are unfortunately not threat safe。

![](img/f2e7035ed81b94923930bff65e576a63_365.png)

![](img/f2e7035ed81b94923930bff65e576a63_366.png)

![](img/f2e7035ed81b94923930bff65e576a63_367.png)

So if you need random number generators in a multithed program。

 you either have to implement some custom random number generation use a third party library。

 or this is probably sufficient for most use cases simply use a separate random number generator for each thread that needs random numbers。



![](img/f2e7035ed81b94923930bff65e576a63_369.png)

Despite the variety of random number generators that are available。

 one should usually prefer the Mer and twister generators that are defined within the standard libraries within the standard library because those produce the highest quality random numbers from within the pool of random number generators that is available within the standard library。

In addition to these random number generator， there's also a default random engine type alias for some random number generator。

 but this implementation is implementation defined， so if you want portability。

 you shouldn't use this type alias because then you cannot be sure then it behaves the same on all platforms to which you might want to distribute your program。



![](img/f2e7035ed81b94923930bff65e576a63_371.png)

![](img/f2e7035ed81b94923930bff65e576a63_372.png)

![](img/f2e7035ed81b94923930bff65e576a63_373.png)

。Most of the random number generators that are defined in the standard library are actually specializations of an underlying random number engine。



![](img/f2e7035ed81b94923930bff65e576a63_375.png)

Which has a number of parameters that can be tuned， but。

Unless you know exactly what you're doing by modifying these parameters。

 you should always use the predefined random number generators because it's quite easy to end up with a random number generator that's not actually random if you modify these parameters in a wrong way。

 but I personally have not yet encountered a use case in which this would be required。

 so I think Im using the predefined random number generators covers most if not all use cases for random number generation in usual programs。



![](img/f2e7035ed81b94923930bff65e576a63_377.png)

![](img/f2e7035ed81b94923930bff65e576a63_378.png)

![](img/f2e7035ed81b94923930bff65e576a63_379.png)

![](img/f2e7035ed81b94923930bff65e576a63_380.png)

![](img/f2e7035ed81b94923930bff65e576a63_381.png)

So we've said that we should prefer the MerRS and twistta generators。

 which are predefined for 32 bit and 64 bit in output width of integers through the type aliases that are shown here。

And these then produce high quality unsigned random numbers between0 and the maximum value that can be represented by an unsign of the respective Bi width here。



![](img/f2e7035ed81b94923930bff65e576a63_383.png)

![](img/f2e7035ed81b94923930bff65e576a63_384.png)

And usually， you want to provide an initial seed to these random number generators in their constructor。

 which can either be a fixed value or。As we see on this slide here。

 if you want actual more or less random numbers， it should of course not be a fixed seed。

 but instead some random value that's determined through some hopefully reliable way because it's quite difficult to actually get random numbers in the first place the standard library defines the SDD random device abstraction that you can use as a standard interface to whatever source of external randomness is available within your system。

 so this could be simply reading from dev random on a Linux system if you have some specialized setup。

 this could be some kind of hardware that samples atmospheric noise for true random numbers or anything else so all of these can be accessed through SD random device provided of course that the C+ plus implementation actually。



![](img/f2e7035ed81b94923930bff65e576a63_386.png)

![](img/f2e7035ed81b94923930bff65e576a63_387.png)

![](img/f2e7035ed81b94923930bff65e576a63_388.png)

Has。An implementation for have a specialized hardware you have within your system。

So this is the only source of real randomness provided that you have， for example。

 something that samples atmospheric noise and this is probably the common case this can degrade to a pseudo random number generators when there is no source of true randomness within your system nevertheless usually if you need just random numbers within your system you will see at some point code like this shown here where you initialize a random number engine in this case a 32 bit percent twister and you see it with whatever SDd random device gives you as an initial random number here。



![](img/f2e7035ed81b94923930bff65e576a63_390.png)

![](img/f2e7035ed81b94923930bff65e576a63_391.png)

![](img/f2e7035ed81b94923930bff65e576a63_392.png)

![](img/f2e7035ed81b94923930bff65e576a63_393.png)

。Any questions so far。

![](img/f2e7035ed81b94923930bff65e576a63_395.png)

Nothing coming up。 Alright， so now that we have these random number generators that just give us random unsign integers。



![](img/f2e7035ed81b94923930bff65e576a63_397.png)

With a Bi width， we can then use these initial random numbers and feed them to the random number distributions that are also specified in the random library here and of course this is useful because what we initially get from a random number generator is yet rather useless there is a fixed output range and a fixed output distribution so the distribution of values from a random number generator is by definition uniform if we want something else from a uniform distribution we have to do some additional work here。



![](img/f2e7035ed81b94923930bff65e576a63_399.png)

For this， the random the random library provides us distribution objects that transform the output of a random number generator。

 So these uniformly distributed random numbers into。



![](img/f2e7035ed81b94923930bff65e576a63_401.png)

。Whatever kind of distribution we want to use such as another uniform distribution with a different range or a normal distribution。

 Bernoulli distribution and so on so all of these wellknow distributions are provided in the random library here。

 and of course we can combine them with all the random number engines for generating just random unsigned integers here。



![](img/f2e7035ed81b94923930bff65e576a63_403.png)

![](img/f2e7035ed81b94923930bff65e576a63_404.png)

Also， some of these distributions provide separate implementations for discrete or continuous distributions。

 and so for example， a uniform distribution can either be continuous on a range of floating point values or discrete on a range of integers。



![](img/f2e7035ed81b94923930bff65e576a63_406.png)

And this is precisely what is done by the SD uniform into distribution type。

 which generates discrete uniform random numbers in a range and between an upper and a lower bound。

 just note that the range here is inclusive so both the upper and the lower bound can and will be included in the range of numbers generated by such a distribution here。



![](img/f2e7035ed81b94923930bff65e576a63_408.png)

![](img/f2e7035ed81b94923930bff65e576a63_409.png)

The actual integer type that you want to use is specified as a template parameter。

 so you've constructed as a uniform interdis with your integer type and then the bound of the range in which you want to generate numbers as the parameters here if not specified these values will default to0 and the maximum value of T。

 but most of the time there is no real use case for the default constructor here since you always have some range that you want to specify。



![](img/f2e7035ed81b94923930bff65e576a63_411.png)

![](img/f2e7035ed81b94923930bff65e576a63_412.png)

And then to actually get numbers from such a distribution， you。

pass a random number generator to the function call operator of this distribution and then the return value will be a sample from your distribution here。

 so in this code snippet down here there's an example once again we define a random number engine here then we define a distribution of integers in our case between minus2 and2 and then we can sample values from this distribution by invoking the function call operator passing our random number engine and taking the return value of this function call here。



![](img/f2e7035ed81b94923930bff65e576a63_414.png)

The same is， of course possible for floating point numbers for which we have SDD uniform real distribution。

 which apart from a different return type and being continuous instead of discrete works in exactly the same way as the uniform into distribution。



![](img/f2e7035ed81b94923930bff65e576a63_416.png)

Now a couple more words on seeding and random number generators， usually if you have production code。

 your random number sequences should not be predictable。

 so random number generators should generate a new sequence of random numbers every time your program is run。



![](img/f2e7035ed81b94923930bff65e576a63_418.png)

![](img/f2e7035ed81b94923930bff65e576a63_419.png)

And of course， since the seed value of your generator is used to calculate all other random numbers。

 usually the seed should itself be a random number。

 and we've already seen that we can use STD random device to obtain such an initial random number。

Of course， in DV code or for tests and experiments。

 deterministic sequences are preferable because then you can actually reproduce。

 for example crashes or bugs in your code much more easily and for that you can supply a fixed arbitrary integer as dec to your random number generator and then of course the generated sequence will always be the same as long as the stays the same。

And just the final word of warning。When you take the entire lifetime of your program。

And take a look at the entropy of your random number generator so informally speaking how random the numbers are that are generated by this generator。

 then this entropy is entirely dependent on the entropy of the seed generator So if you generate bad seed numbers so for example。

 there are only six different seed numbers that you pass to your random number generator then your random number generator itself over the entire lifetime of your program will also produce very bad random numbers。

 So this is just a side note that's still important to keep in mind。

 especially once you start relying on high quality random numbers within your programs。



![](img/f2e7035ed81b94923930bff65e576a63_421.png)

![](img/f2e7035ed81b94923930bff65e576a63_422.png)

![](img/f2e7035ed81b94923930bff65e576a63_423.png)

。And finally， just a closing example， how we would generate random dice rolls here。

 as we've seen on the previous slide， and we use STD random device to generate seats set up a random number generator with a random number from this random device and then a uniform in distribution。

With a lower bound of one and an upper bound of6 to generate uniformly distributed dice rolls between one and six here。

Now。We specifically picked this example of generating random dice rolls because there's a very common pitfall that unfortunately。

 you see in a vast amount of examples when it comes to generating random numbers， and that is。



![](img/f2e7035ed81b94923930bff65e576a63_425.png)

Generating random dicetros by using modullo operations here。

 And this is quite dangerous because you can very easily end up with random numbers that are actually not that random anymore and specifically have a different distribution from what you would actually expect。



![](img/f2e7035ed81b94923930bff65e576a63_427.png)

![](img/f2e7035ed81b94923930bff65e576a63_428.png)

So why is this a problem so most random number generators generate values in the interval between0 and 2 to the power of w minus1 for some value of w because we have random numbers of a sort bit width and the values are uniformly distributed between all values that can be represented within this bit width here。



![](img/f2e7035ed81b94923930bff65e576a63_430.png)

![](img/f2e7035ed81b94923930bff65e576a63_431.png)

![](img/f2e7035ed81b94923930bff65e576a63_432.png)

And now whenever our Moulu operation uses a right hand side that is not a power of two。

 this modlo operation will generate more smaller values than it will generate larger values。

So to illustrate this， let's go back to our random dice roll example here。

 and let's assume a perfect random number generator with a bit width of3 to make obvious what's happening here。

 So the random number generator will then produce all values in between 0 and 7 with equal probability 18。



![](img/f2e7035ed81b94923930bff65e576a63_434.png)

![](img/f2e7035ed81b94923930bff65e576a63_435.png)

And now if we implement our random dis rolls as simply taking such a random number。

 computing the modlo6 and then adding one so that we get values between one and 6。

 we can by simply counting C that the probability of our random dice roll function returning1 or2 is one quarter。

 and the probability of our random dias roll function returning 3，4，5 or6 is 18。



![](img/f2e7035ed81b94923930bff65e576a63_437.png)

![](img/f2e7035ed81b94923930bff65e576a63_438.png)

Because。Only for the values0 and I'm sorry only for values1 and2 there are two values produced by the random number generators that after applying modlo will end up at this value and for all the remaining values only one value that the random number generator can produce will produce the respective dies role here。

 so of course this is an exaggerated example since the bandwidth width of our generator is so small。

 but still you can see that using modlo to generate random numbers can introduce Q into your distribution and because of this and especially because there are much better ways to achieve your goals in C++ you should simply never use modlo to generate random numbers within a specific range of values。



![](img/f2e7035ed81b94923930bff65e576a63_440.png)

![](img/f2e7035ed81b94923930bff65e576a63_441.png)

![](img/f2e7035ed81b94923930bff65e576a63_442.png)

So with this， I'd like to thank you for your attention。

 are there any final question on today's lecture？Yeah。All right。

 then it doesn't look like it in that case， see you this Friday and goodbye。



![](img/f2e7035ed81b94923930bff65e576a63_444.png)

Yeah。