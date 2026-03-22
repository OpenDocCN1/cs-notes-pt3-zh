# 【全集】范德堡大学 C++标准模板库 中英字幕 1080P p17 Lecture 17 - 函数指针和成员函数指针 -BV1KWiCBWE7M_p17-

Hello and welcome to the next session in my webinar series on C++ Standard Temp Library by example。

We're going to begin a discussion that will last for several days that will' be focusing on functors or function objects。

😡，Which are strategies used within C++ SDL to enable configuration of algorithms and containers。😡。

Functorters are a very interesting aspect of C++ SDL because they basically apply the strategy pattern and allow it to be possible to guide and modify the behavior of algorithms in containers without actually changing their internal implementation details。

We're going to begin our discussion of functionsctors by covering function pointers。

 which are a feature that has been around for a long time starting with C and then of course also continuing on in C++ in several different ways as we'll see that provide the conceptual foundation for the funter capabilities that have found their way into C++ SDL so without any further ado let's go ahead and share the screen and I'll show you where you can find the source code and then we'll examine the software。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_1.png)

So if you go to the。My GitHub repository in my C++ folder under STL S08。

 you'll find the code we're going to be looking at over the next several days。

 we're going to start by looking at the code that's in the 8。

1 subfold and that will contain the coverage of function pointers。



![](img/fe83c9eb79a2f981ea56556877891722_3.png)

So let's go ahead and take a look now at some examples。So as I mentioned before。

 funcctorters are influenced or inspired by function pointers and so we'll start by talking about how those capabilities work and then next time tomorrow we'll talk about funcctors and start seeing what they can do。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_5.png)

![](img/fe83c9eb79a2f981ea56556877891722_6.png)

So as the name implies， a function pointer is a pointer。

 it's a variable that points to the address of a function。😡。



![](img/fe83c9eb79a2f981ea56556877891722_8.png)

Now， obviously when you run your program， it's got a bunch of data and it's got a bunch of code and essentially the functions are portion of your executable code space。

 and you can actually have pointers to them， you can find the address of a function by its label by its name and you can store that off to the side and call it it runtime if you don't want to have to hard code。

 the actual calling sequence or the calling names into your code directly。



![](img/fe83c9eb79a2f981ea56556877891722_10.png)

So let's assume for sake argument we've got a function F and therefore it's got a name F and so one thing we could do of course is directly call in in the source code and then it'll go ahead and jump to that location in memory based on the compiler and the linker and so on and do its thing but we might want to abstract this and have this function called at runtime and that's useful for all kinds of things even in C where you can use pointers to functions for features like passing in the comparison function to the Q sort method just one of many examples pointers to functions are also commonly used for callbacks for things like spawning a C plus plus or C thread using the Pthreads library or the Windows thread API it's also common to use pointers to functions in the context of windowing systems where you need to have callbacks or timers of some sort so in all those cases you want to be able to know at runtime what function to call and those kinds of information you can either be returned from some type of factory method。



![](img/fe83c9eb79a2f981ea56556877891722_12.png)

![](img/fe83c9eb79a2f981ea56556877891722_13.png)

![](img/fe83c9eb79a2f981ea56556877891722_14.png)

![](img/fe83c9eb79a2f981ea56556877891722_15.png)

![](img/fe83c9eb79a2f981ea56556877891722_16.png)

![](img/fe83c9eb79a2f981ea56556877891722_17.png)

Or stored in the data structure， for example， the C++ compiler will store the virtual methods that are dispatched using C++s object oriented virtual method dispatching capability using as of pointers to functions that implement the C++ methods so that's yet another example where functions are stored in tables and then called indirectly at runtime。



![](img/fe83c9eb79a2f981ea56556877891722_19.png)

![](img/fe83c9eb79a2f981ea56556877891722_20.png)

![](img/fe83c9eb79a2f981ea56556877891722_21.png)

![](img/fe83c9eb79a2f981ea56556877891722_22.png)

![](img/fe83c9eb79a2f981ea56556877891722_23.png)

So we're going to talk about how you can program with pointers to functions and I'm going to start by giving you a very simple example that does not use pointers to functions but it'll be the motivation for an example that does in fact use pointers to functions so here we go we're going to start out by taking a look at this piece of code we've got four functions plus minus multiply and divide and those all do the obvious things they take a pair of float parameters A and B and then they perform the corresponding operation adding subtracting multiply dividing and so on and they return a float as the result from their corresponding function。



![](img/fe83c9eb79a2f981ea56556877891722_25.png)

![](img/fe83c9eb79a2f981ea56556877891722_26.png)

![](img/fe83c9eb79a2f981ea56556877891722_27.png)

![](img/fe83c9eb79a2f981ea56556877891722_28.png)

We're then going to write a function here with the name that's called switch with a capital S to differentiate it from the structure in the control construct in CNC++ that we'll select among alternative labels or cases。

 and what we do here is we pass in two floats A and B and a character op code and the character op code would correspond to the character plus or the character minus and so on。

 as you can see here in the code。

![](img/fe83c9eb79a2f981ea56556877891722_30.png)

![](img/fe83c9eb79a2f981ea56556877891722_31.png)

![](img/fe83c9eb79a2f981ea56556877891722_32.png)

![](img/fe83c9eb79a2f981ea56556877891722_33.png)

So then we go ahead and switch on the op code and we then turn around depending on is that what it is that the character was。

 and then we call the corresponding method we call plus minus multily divide and so on。

 store the result into a local variable called result。

 and then we return the result as the result of this method now we don't have to do it quite this way we could have gotten around this by having each of the cases return as opposed to set of field and then break set of value and then break but I just did it this way for convenience。



![](img/fe83c9eb79a2f981ea56556877891722_35.png)

![](img/fe83c9eb79a2f981ea56556877891722_36.png)

Okay so let's take a look at the code， the next piece of code the next piece of code is a little bit more interesting this is called switch function pointer and we don't really need the word switch here we should probably call it invoke function pointer or something like that and the difference between these two pieces of code is unlike this version which took an op code and switched on it and this version we're actually going to pass the address of the function we want to have call and so what we're going to do is we're going to call switch function pointer with to floats A and B and then a pointer to a function and then it's going go ahead and basically call that pointer to function which of course is dispatched dynamically with the parameters A and B and then it will return the results so you can see it's much more concise and there's no switch statement by the way we don't have to run we don't have to write the code with this syntax we could use this syntax instead this is perfectly legitimate pointer to function call syntax and in fact it's actually a little bit more。



![](img/fe83c9eb79a2f981ea56556877891722_38.png)

![](img/fe83c9eb79a2f981ea56556877891722_39.png)

![](img/fe83c9eb79a2f981ea56556877891722_40.png)

![](img/fe83c9eb79a2f981ea56556877891722_41.png)

![](img/fe83c9eb79a2f981ea56556877891722_42.png)

![](img/fe83c9eb79a2f981ea56556877891722_43.png)

Faful to what's actually going on when you declare when you declare the parameter here。

 but I don't know about you， but I find that just a little bit ugly so i'm going to call it like that it's a little bit a little bit cleaner to do it this way so now it looks more like a regular function call。

Okay so let's see how we actually can call these two different methods so down here in the main program we're going to call the switch method that takes an op code and we're going to pass in two and five as floating points and we're going to pass in the plus op code so of course that's going to add them together and then down here we're going to call our switch function pointer method passing in two and five except this time we're going to pass it the address of the minus function and by the way we don't have to put the address there we can also leave the address of operation off it means the same thing that behavior is identical let's keep it in there just for kicks。



![](img/fe83c9eb79a2f981ea56556877891722_45.png)

![](img/fe83c9eb79a2f981ea56556877891722_46.png)

So when we run this code， let's see what happens。😡，And as you can see， we get the result we expected。

 or at least I expected because I tested the code to make sure it did the right thing before I ran it and basically what it does。

 the first version goes ahead and applies the addition operation because we pass in the plus sign as the op code and the second version applies the minus operation because we pass in the minus function as a function pointer and so that's just an example of the concept of function pointers and a very simple illustration of how to use them in practice。



![](img/fe83c9eb79a2f981ea56556877891722_48.png)

![](img/fe83c9eb79a2f981ea56556877891722_49.png)

![](img/fe83c9eb79a2f981ea56556877891722_50.png)

![](img/fe83c9eb79a2f981ea56556877891722_51.png)

![](img/fe83c9eb79a2f981ea56556877891722_52.png)

Now you might be wondering at this point what theck does this have to do with STL C++ well the reason it has to do with C++ and STL is that funs work more or less the same way the function pointer that I just passed in here with a couple of exceptions number one the function pointers are not easily in line because they're passed by their address whereas funs are actually objects so we can have the compiler do all kinds of aggressive inlining and number two。



![](img/fe83c9eb79a2f981ea56556877891722_54.png)

![](img/fe83c9eb79a2f981ea56556877891722_55.png)

![](img/fe83c9eb79a2f981ea56556877891722_56.png)

Function objects or functors are objects as the name implies。

 and therefore they can actually store state whereas pointer to function as the form I showed here does not store state and so we're going to leverage that in our future discussions when we really get into the nuts and bolts of funs in order to see how they're actually better in many ways than pointers to functions。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_58.png)

![](img/fe83c9eb79a2f981ea56556877891722_59.png)

But before we get into that， let's go ahead and take a look at some more examples。

 so if we go over here。

![](img/fe83c9eb79a2f981ea56556877891722_61.png)

Open up this example。

![](img/fe83c9eb79a2f981ea56556877891722_63.png)

So here's an example that kind of shows you the richness of pointers to functions in C++ so what I showed you in the previous example really was focusing on kind of the C style pointers to functions that we've come to know and love as being part of the C programming language。



![](img/fe83c9eb79a2f981ea56556877891722_65.png)

![](img/fe83c9eb79a2f981ea56556877891722_66.png)

![](img/fe83c9eb79a2f981ea56556877891722_67.png)

What I'm going to do now is I'm going to talk about the C++ capabilities that go above and beyond that。

So as you recall in C++ as much as you want or as much as you can。

 it's helpful to associate your methods and group them into classes。

 we can have utility classes which just have a bunch of static methods。

 we can have classes that have state and here's a simple example of a class that has state it's not the world's most profound class but it will be enough to illustrate the point we're trying to show。



![](img/fe83c9eb79a2f981ea56556877891722_69.png)

![](img/fe83c9eb79a2f981ea56556877891722_70.png)

So we have something called example class and it's going to be past an int。

 which is defaulted to zero， and as you can see here。

 it goes ahead and takes the parameter and stashees it away in the private I_ data member。



![](img/fe83c9eb79a2f981ea56556877891722_72.png)

![](img/fe83c9eb79a2f981ea56556877891722_73.png)

And then it's got three different methods in this class， One is a fun。And as you can see。

 that is a non constant method that takes three parameters。

 adds them all together together with a value of I and returns the result。

It has something else called another fun， which also takes three parameters and the difference between these two is that this version is a con version。

 it goes ahead and just adds A B， well actually it doesn't add it， takes I underscore， adds it to A。

 then it subtracts B， then it adds C。😡，And then notice how up here we have。



![](img/fe83c9eb79a2f981ea56556877891722_75.png)

A fund have a side effect and update the contents of I underscore so that one's a non constant method because it changes the state of the object of the example class instance。

 whereas another fund does not。😡。

![](img/fe83c9eb79a2f981ea56556877891722_77.png)

![](img/fe83c9eb79a2f981ea56556877891722_78.png)

And then just for kicks， we have a third method here called a static fund for a static function。

 and it takes three parameters and it adds them all together and it's going to be a static method so you can't rely or you can't access the actual state of an instance because there is no instance for a static fund so those are the three general types of methods you can have in C++ classes you can have。



![](img/fe83c9eb79a2f981ea56556877891722_80.png)

![](img/fe83c9eb79a2f981ea56556877891722_81.png)

![](img/fe83c9eb79a2f981ea56556877891722_82.png)

Noncon member functions that are non static， you can have con member functions that are nons static and then as we see here we can also have a static method that's a static member function it's really pretty much like a C+ or like a C style function that's within nested within a class。



![](img/fe83c9eb79a2f981ea56556877891722_84.png)

![](img/fe83c9eb79a2f981ea56556877891722_85.png)

![](img/fe83c9eb79a2f981ea56556877891722_86.png)

Okay so now that we've got those three different categories of things。

 let's go down here and let's define pointers to each of those types of things so as you're going to see here we're going to define something called pointer to function and that takes three parameters the first of which is a floatat and the second two or characters and returns afloat and we give that a null pointer we could actually have left out the null pointer it would have been initialized to null since it's a basically a global variable here。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_88.png)

![](img/fe83c9eb79a2f981ea56556877891722_89.png)

![](img/fe83c9eb79a2f981ea56556877891722_90.png)

![](img/fe83c9eb79a2f981ea56556877891722_91.png)

![](img/fe83c9eb79a2f981ea56556877891722_92.png)

Not really a good idea to have global variables， I'm just doing this for the illustration purposes and to keep my example easy to comment。



![](img/fe83c9eb79a2f981ea56556877891722_94.png)

The next thing we're going to do is we're going to define a pointer to non con member function。

 and this pointer to non con member function is going to be associated with example class。😡。



![](img/fe83c9eb79a2f981ea56556877891722_96.png)

![](img/fe83c9eb79a2f981ea56556877891722_97.png)

And to make this interesting， I probably should have defined another couple methods in there that had the same signature and showed how you can plug and play them in various ways and perhaps we'll do that for some future example。

 so the difference is that this particular point or two member function needs to be called in the context of an instance of example class。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_99.png)

![](img/fe83c9eb79a2f981ea56556877891722_100.png)

And then the third pointer to function we're defining here is that pointer to constant member function。

 and as you can see here， it's a con。

![](img/fe83c9eb79a2f981ea56556877891722_102.png)

And it's expecting to have a pointer to a constant member con member function well。

 as luck would have it， we have all those different methods defined in our example class。

 so now let's go ahead and see how we can use them。



![](img/fe83c9eb79a2f981ea56556877891722_104.png)

So down here we're going to go ahead and define ourselves a pointer to con member passing it in the address of example class Col colon another fun so you can see how that gets done so that's taking。



![](img/fe83c9eb79a2f981ea56556877891722_106.png)

![](img/fe83c9eb79a2f981ea56556877891722_107.png)

This guy， which is a constant member function。

![](img/fe83c9eb79a2f981ea56556877891722_109.png)

And then we're going to define and assign pointer two member。😡。



![](img/fe83c9eb79a2f981ea56556877891722_111.png)

Which is the non con version and that's going to be the address of example class Col colon aF。



![](img/fe83c9eb79a2f981ea56556877891722_113.png)

And then the last thing we're to do is we're going to assign pointer two function to the address of example class colon colon a static font Now if I tried to mix and match these things。

 it wouldn't compile because C++ obviously is smart enough to know the difference between pointers to member functions。

 pointers to cons member functions and pointers to static functions or static member functions。



![](img/fe83c9eb79a2f981ea56556877891722_115.png)

![](img/fe83c9eb79a2f981ea56556877891722_116.png)

![](img/fe83c9eb79a2f981ea56556877891722_117.png)

![](img/fe83c9eb79a2f981ea56556877891722_118.png)

We then define ourselves an instance of example class。

 we call instance one and we give it a 10 and then we go ahead and we call these pointers to member functions and pointers to functions so this one's going to be called with the value 12。

5 and A and B that's the noncon member function。😡。

![](img/fe83c9eb79a2f981ea56556877891722_120.png)

That's non static we're then you're going to call pointer to con member。

Which is a pointer to a cons member function。And we're going to pass in some parameters for that。

 and then the final thing we're going to do is call the pointer to function。

 which of course is the static function。

![](img/fe83c9eb79a2f981ea56556877891722_122.png)

And then just for kicks， we're going to go ahead and show how we can make another instance of example class this time we'll allocate it dynamically using the new operator and we're going to stick this inside a unique pointer and if you recall a unique pointer a really cool holder abstraction in C+ plus 11 and beyond that improves upon some of the quirks of the previous auto pointer which has been deprecated and basically assumes ownership of the pointer and make sure the pointer will be released when the unique pointer goes out of scope and just to illustrate we can do all these pointer tricks and pointer member function tricks on pointers even unique pointers。

 we go ahead and say instance2 get which gets us the underlying pointer that the unique pointer encapsulates and then we go ahead and call the pointer to member method passing in these parameters and notice the syntax here the idea here is to try to mimic the syntax of pointers to functions as much as possible。



![](img/fe83c9eb79a2f981ea56556877891722_124.png)

![](img/fe83c9eb79a2f981ea56556877891722_125.png)

![](img/fe83c9eb79a2f981ea56556877891722_126.png)

![](img/fe83c9eb79a2f981ea56556877891722_127.png)

![](img/fe83c9eb79a2f981ea56556877891722_128.png)

![](img/fe83c9eb79a2f981ea56556877891722_129.png)

![](img/fe83c9eb79a2f981ea56556877891722_130.png)

![](img/fe83c9eb79a2f981ea56556877891722_131.png)

While acknowledging the fact that for pointers to member functions， you've got to have an object。

 so in this case， this is the object。😡，And the syntax is dot star to dereference that pointer to member function and down here we have a pointer so it'sarrow star and that's a bit a little bit weird at first。

 but it's really no weirder than the underlying C pointer to function syntax。

 which is also kind of weird at least to me。😡，So let's go ahead and run this code and hopefully it'll show you what it does so you can see here that when we call this function。

 it goes ahead and basically does all the magic needed to do this operation。



![](img/fe83c9eb79a2f981ea56556877891722_133.png)

With these values。And keep in mind that the A and B turn in basically into integers and that's why the number is so high。

 they turn into their ASI equivalentvals。Here's the pointer to con member。

 here's the call to the pointer to function， and then the final thing we do here is we go ahead and。

Do this version， it's calling it through a unique pointer which encapsulates the underlying pointer to the dynamically allocated example class。



![](img/fe83c9eb79a2f981ea56556877891722_135.png)

![](img/fe83c9eb79a2f981ea56556877891722_136.png)

Okay， so that's kind of showing you some other interesting things with pointers to member functions and pointers to functions and pointers to con non static member functions and so on and so forth。



![](img/fe83c9eb79a2f981ea56556877891722_138.png)

![](img/fe83c9eb79a2f981ea56556877891722_139.png)

To be honest with you， I don't do a whole lot of programming with pointers to member functions in my code。

 but that's not to say that they don't come in useful and there are certainly situations where they can be quite useful。

 it just that for what I typically program I don't use those things a lot。

 but they do exist and you should be aware of them because if nothing else you want to be up on your C++ trivia in case you're ever in a job interview and someone askeds you to explain all this stuff。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_141.png)

![](img/fe83c9eb79a2f981ea56556877891722_142.png)

![](img/fe83c9eb79a2f981ea56556877891722_143.png)

Okay， the third and final example we're going to look at today， again。

 our goal here is just to provide the foundations for funcctors which we'll cover next time in its full blown glory。

 we're going to talk about how you can basically pass functions as parameters to functions。

 so that's what we would call a higher order function。

 a function that takes a function as a parameter and how you can also return functions to return functions from functions。

 which is another dimension of the so-called higher order function。😡。



![](img/fe83c9eb79a2f981ea56556877891722_145.png)

![](img/fe83c9eb79a2f981ea56556877891722_146.png)

![](img/fe83c9eb79a2f981ea56556877891722_147.png)

![](img/fe83c9eb79a2f981ea56556877891722_148.png)

So once again we're going to use our plus and minus operations just kind of cut and pasted them from before and I'm showing you here how we're able to pass a pointer so this syntax is a little bit wonky but pass pointer takes a pointer to a function that takes three parameters and returns af floatat and then what it does in this particular case it goes ahead and it runs it calls the function that was passed in in order to do its thing。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_150.png)

![](img/fe83c9eb79a2f981ea56556877891722_151.png)

And we'll take a look and see what that's going to be when we take a look at the code a little bit later。

It's also possible to return functions or pointers to functions from a function。

 which is another aspect of a so-called higher order function and this is one of those things where trying to get your head around the syntax without using type def is enough to melt your mind so to make your life a little easier I did a type def。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_153.png)

![](img/fe83c9eb79a2f981ea56556877891722_154.png)

![](img/fe83c9eb79a2f981ea56556877891722_155.png)

![](img/fe83c9eb79a2f981ea56556877891722_156.png)

And then I declared my function here， which is called get PTf or get pointer to function to return this type def you can define this thing in line without a type def。

 but it's very， very convoluted so what we're doing here is we're going to pass in an op code and then get PTf is going to take a look at the op code and then return the corresponding pointer to function that's associated with that op code so as you can see here if you pass in a plus you'll get the plus back if the if the op code。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_158.png)

![](img/fe83c9eb79a2f981ea56556877891722_159.png)

Is equal to。I spell if it's equal to minus， then we go ahead and return the minus and and otherwise。

 you know else。Let's let's be really sinister let's do things you should never do let's return null pointer not a good idea of course。

 but i'm just trying to show an example not right production code here so that's how we're going to get back a pointer to a function by having a factor method that looks at some parameter and returns the corresponding pointer to function。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_161.png)

![](img/fe83c9eb79a2f981ea56556877891722_162.png)

![](img/fe83c9eb79a2f981ea56556877891722_163.png)

Down here we have a function， which we call a fun， which has three parameters and I probably to be consistent probably should have moved this up here。

 so we're going to put this guy up here because he's really associated more with。



![](img/fe83c9eb79a2f981ea56556877891722_165.png)

![](img/fe83c9eb79a2f981ea56556877891722_166.png)

![](img/fe83c9eb79a2f981ea56556877891722_167.png)

This example of passing a pointer to a function， and I probably should also use something here to make it more clear what's going on let's。



![](img/fe83c9eb79a2f981ea56556877891722_169.png)

Do a little refactor and let's rename this thing to PTf so we're going to pass a pointer to function。



![](img/fe83c9eb79a2f981ea56556877891722_171.png)

Okay so let's now go take a look at the code that's going to do all these fun things。

 so here's the main program， the first thing we're going to do is we're going to go ahead and pass the a fun pointer to the pass PTf。

😡，Function and again keep in mind I don't have to put the address of sign here I just did it out of habit perhaps in either case if you use the name of a function it turns into a pointer to a function and taking the address of the name of a function won't make it a pointer to a pointer to a function。

 which is one of the somewhat mysterious aspects of CNC+ plus syntax and type checking rules and type model rules。

 but just have to remember that。

![](img/fe83c9eb79a2f981ea56556877891722_173.png)

![](img/fe83c9eb79a2f981ea56556877891722_174.png)

![](img/fe83c9eb79a2f981ea56556877891722_175.png)

Down here we then define a pointer two function which takes two floats and returns a float and we give it the value of null initially and then we use our good friend the get PTR or PTF method to get pointer to function method which is the factor method where we pass it in an op code and it gives it back the corresponding function so here we say get PTf with an op code of plus we get back the plus operation at least we hope we do we'll see what it does in a second and then over here we go ahead and call it get PTf with the minus op code and we'll get back the minus function and then that should do a minus so let's go ahead and run the code。



![](img/fe83c9eb79a2f981ea56556877891722_177.png)

![](img/fe83c9eb79a2f981ea56556877891722_178.png)

![](img/fe83c9eb79a2f981ea56556877891722_179.png)

![](img/fe83c9eb79a2f981ea56556877891722_180.png)

And you can see what it does when we go ahead and past this function here then。



![](img/fe83c9eb79a2f981ea56556877891722_182.png)

That is going to do this operation there we're going to basically pass in this function to pass PTf where it will be called to do the result and get 207 and then down here we're going to go ahead and get the addition function and we're going to add 2。

4 to 4。2 thereby equaling 6。6 and down here we're going to call get PTf with the minus op code which we'll get us back the minus function and we'll we called that we're going to subtract 2。

4 from 4。2 yielding 1。8 so fortunately the mathematics all works out and everything behaves as we expected。



![](img/fe83c9eb79a2f981ea56556877891722_184.png)

![](img/fe83c9eb79a2f981ea56556877891722_185.png)

![](img/fe83c9eb79a2f981ea56556877891722_186.png)

![](img/fe83c9eb79a2f981ea56556877891722_187.png)

![](img/fe83c9eb79a2f981ea56556877891722_188.png)

![](img/fe83c9eb79a2f981ea56556877891722_189.png)

![](img/fe83c9eb79a2f981ea56556877891722_190.png)

So what I wanted to do today was just start building the foundation for talking about pointers to start talking about pointers to functions to build the foundation to talk about funcctors。

 which is what we're going to cover next so starting tomorrow we're going to talk about funcctors and you'll see that C+ plus STL comes with many many dozens of predefined funcctors for things like arithmetic operations like plus and minus but their functors not functions as we just saw as well as all kinds of other funcctors out of the box。

 things like like the relational operators less greater less than greater than and so on as well as all the logical operations as well like。

😡。

![](img/fe83c9eb79a2f981ea56556877891722_192.png)

Logical or logical and and so on I honestly have never used those in my code。

 but the other ones we talked about like the relational operations very widely used for things like configuring priority sets or configuring sets as a way to order and dictate which way the ordering takes place so you'll see that the funks that are built into C++ STL are extremely useful and we will start to talk about those things tomorrow。

So until then， thanks for joining， please feel free to like and subscribe and also please feel free to follow me on Twitter。

