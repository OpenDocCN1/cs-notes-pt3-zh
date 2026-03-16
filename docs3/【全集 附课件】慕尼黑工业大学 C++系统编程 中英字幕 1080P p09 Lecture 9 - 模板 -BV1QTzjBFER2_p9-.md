# 【全集 附课件】慕尼黑工业大学 C++系统编程 中英字幕 1080P p09 Lecture 9 - 模板 -BV1QTzjBFER2_p9-

Welcome back， everyone to another lecture of the systems programming in C++ practical course in which today we're going to talk about templates。

Now， templates is a pretty vague term， if you've never heard about it。

 so let's take a look at why we actually want to have these in our favorite programming language。

 So the main motivation here is that whenever you start implementing something you will inevitably come across some functionality that is essentially independent of a specific type T and some prime examples here are。

 for example， a swap function which shouldn't really care at all which types of elements it swaps as long as they fulfill some specific requirements。

 similarly， an STD vector doesn't really have to care about what type of elements it stores once again。

 as long as they support some operation such as moving or copying and there are many。

 many more examples that you've for example， seen in your exercises as well。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_1.png)

Here， you've also implemented some containers that were since you didn't know about templates yet constrained to a specific type。

 but we could just as well have implemented them in a generic way so that they work for almost arbitrary types。

Now， the problem here is that， of course， this functionality should be available for all suitable types T。

 but。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_3.png)

We do not want code application， which would be massive if we had to implement this manually for every possible type。

 and even then we couldn't account for user defined types that maybe we don't even know about when we are actually implementing。

 for example， our STD vector vector data structure。But this is the problem。That we have。

 and templates help us solve this problem。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_5.png)

By allowing us to define a family of classes， functions， type aliases or variables。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_7.png)

That we can then parameterize by one or more template parameters。

 And these template parameters can name types， for example， an integer or a load， and they can also。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_9.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_10.png)

Name some kinds of constant numbers。 for example， the size of an STD array is such an example where we have a non type template parameter that allows us to specify the compile time fixed size of such an array。

 And then there are some more。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_12.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_13.png)

N applications for template parameters where we can， for example。

 define template template parameters that are themselves templates once again。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_15.png)

Now in order to use such a family of classes， we have to provide a template argument which is then substituted for these template parameters。

And this then results in what is called a specialization of the template。That we can then use。

 for example， as an STD vector of integers or floating point numbers or whatever we put into the template argument of STD vector。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_17.png)

Now， the key thing here is if once we start taking a look at the syntax for templates。

 they look rather similar， for example， to generics in Java。

 but the key difference here is that templates are purely a compile time construct。

And this means that whenever you use a template， which of course， and for now is rather inaccurate。

 we'll take a look at more details about what this actually means in a couple of slides。

 but once we use a template it is instantiateiate it and template instantiation。

 then actually compiles the code for a specific specialization of your template。

 So when you write S vector of int and you start using this。

 then the compiler will behind the scenes actually generate assembly for this specific specialization of a vector of integers。

 And now if you start using a vector of floating point numbers。

 this is different from a vector of integers， then the compiler will behind the scenes once again generate the assembly code for a vector of floating point numbers。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_19.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_20.png)

And this has a couple of consequences that might be a little bit surprising if youre used。

 for example， to Java generics， which are a runtime construct one consequence that essentially explains everything else that might happen is that all template parameters have to be bound at compile time。

 so you can only put things that are compile time constants or compile time type names into template arguments。

 you cannot do anything at runtime at runtime， a template instantiation is just like any other class it's a specific version of the template and you cannot change it anymore。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_22.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_23.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_24.png)

Now， before we start looking at the sentence a little bit more formally， let's。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_26.png)

Okay， we have already a question that we can address before we move forward。 The question is。

 what is the difference between runtime and compile time well。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_28.png)

Compile time is anything that the compiler does， The compiler， for example。

 can compute some simple computations on constants if you multiply two literals。

 this is something that the compiler can evaluate while compiling your code so you can， for example。

 have an SDD array with a size that you write as four times3。

 this is something that the compiler can evaluate while translating your program。

 but you cannot have the multiplication of two variables that are not constants SD template argument because this is something that the compiler cannot evaluate to one fixed value while compileiling your program so this then something that has to be done at runtime and consequently cannot be used as a template argument。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_30.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_31.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_32.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_33.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_34.png)

So I hope this answers your question。 Please let me know if not。 In the meantime。

 let's take a look at a motivating example。 how we could try to define the STD vector template ourselves。

 Of course， this example is necessarily a little bit simplified so that we can focus on what's really important here。

 So the definition here， if we disregard this line here for a second is essentially the same as for any other class we have our class vector。

 we have then some public member functions。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_36.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_37.png)

And that's essentially the difference is that before the class keyword here。

 we write this template and then Angular brackets class t line and this tells the compiler that our vector class here is templated by a single type template parameter which we call T and then we can use this type template parameter。

 essentially like any other type alias within our vector implementation for example in the pushback function instead of specifying a certain type here we simply use this t type alias so that whenever we specialize our vector sorry whenever we instantiate our vector with a specific type。

 for example， an int this T here is going to be an alias for int and when we do it with something else。

 for example， a class a here， then t is going to be substituted for a and as a type alias to class a here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_39.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_40.png)

And by doing this， we can then rather easily implement very generic containers， for example。

 or anything else， because here， we do not have to care about what type T is specifically。

 we can just focus on the vector functionality。And then we can use this without any code application throughout our projects。

Now， of course， this is a rather informal example， so let's take a look at how formally this is specified by the C++ standard。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_42.png)

Now we can declare several entities as templates， not just classes。

 but the synt is always the same the synax is the template keyword。

 then enclosed in Angular brackets， a parameter list， and then some declaration。

The parameter list is a comma separated list of template parameters。

 which can be typed template parameters。 This is what we've seen on the previous slide。

 and they can also be non type or template template parameters。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_44.png)

And which we're going to see on the following slides。

The declaration that comes after this template keyword and parameter list can either be a class declaration or definition can be a member class or inmiration type can be a function or a member function of a class。

 it can also be a static data member at namespace scope or a data member at classco and it can be a type alias and all of these alternatives have some uses。

 although some of them are used more often than others in particular the class template declaration is I think the alternative here that's used most often throughout the Z++ code that I have seen。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_46.png)

Now， the declaration， of course， this is something that we've already covered in the previous lectures。

 the parameterist merit some more discussion here， and as we've seen on this slide just now。

 the first thing that we can put into this template parameter list is a type template parameter。

 and these are placeholders for arbitrary types。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_48.png)

This syntax， how you can put them in a template。Prame list is a type name or class。

 followed by an arbitrary name。But this name can also be omitted if it' is not necessary similar to how you can omit the name of a function parameter if it is not used。

 and this is sometimes useful if you just have to， declare a template and not actually define it。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_50.png)

Whether you use type name or class as the keyword here is entirely up to you， there is no difference。

 I don't know exactly why theres two options， I think it has some historical reasons。

 but you can use them completely interchangeably there's no effect on thecode that you write。

Now once you have such a template parameter in your template declaration。

 then in the body of the declaration， the name that you've specified is simply a type alias for whatever type was supplied during instantiation。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_52.png)

And just to give you some examples here。 So here's a formal declaration where we omit the name of our template parameters we just write class comma class and then there's another class template definition where we do actually give our template parameter a name namely T。

 and then we can write a function that returns a T takes a T as argument and does some arithmetic computation on this parameter here。

 And of course， you can easily imagine that now we can use this full class here for arbitrary arithmetic types and have a meaningful version of this bar function here that just adds 42 to our parameter of type T here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_54.png)

Now， the second alternative that we can put in a template parameter list is a non type template parameter。

 which are similar to the type template parameter placeholder for certain values instead of types。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_56.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_57.png)

A syntax looks a little bit more like a function parameter here in that we have to specify a type followed by a name。

 And once again， the name can be omitted if we are in a forward declaration， for example。

But as opposed to function parameters， there are some constraints on the type that we are allowed to use here in that the type must be an integral type。

 a pointer type， an enumeration type or an L value reference type。

 Anything else does't worker in particular what does not not work are objects of a user defined class type。

And then once we have this nontype template parameter in our template parameter list。

 once again within the template body， we can use the name of our nontype parameter in arbitrary expressions and the useful thing about this is that the nontype template parameter are always。

 by definition compile time constants， so we can， for example。

 use them to specify the size of an array which as we've seen in previous slides also has to be a compile time constant。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_59.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_60.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_61.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_62.png)

And one useful。Thing where we can use this is actually to define something like STD array ourselves where we want to have a compile time array of that contains objects of type T and namely it contains n objects of this type。

 So here we would have one type template parameter for the type of objects that we restore and one nontype template parameter to store the number of elements that we store。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_64.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_65.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_66.png)

And then as you see here， we can implement a very simplistic version of this STD array container where we have a C style array of type T containing n elements and then for example。

 implement the subscript operator that just returns a reference to objects of type T and can do some asserting to check that we actually do not have out of bounds excesses。

 but apart from that we do not really have to do anything here to make this work。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_68.png)

The final thing that we can put in a template parameter list are template template parameters。

 But just as a disclaimer， although they look very fancy and useful， In fact， in practice。

 you do not really want to use them， they are。 They are not really that often required。

 and they also a bit clunky to use。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_70.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_71.png)

Nevertheless， for completeness。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_73.png)

The syntax here is essentially the same as the syntax for type template parameters。

 just that you prefix the type name or class keyword with another template parameter list。

And then within the template body， the name is itself a template name previously in a type template parameter。

 It was simply a type alias for another type。 Now， it is an alias for a template。

 So whenever we want to use this name， we actually have to provide template arguments to this。

Template to template parameter。 And an example of this could look。Like this shown here。

 we have a type template parameter of class array type that is itself templated with another type template parameter and a non type template parameter。

 and then we can specify， for example a member here as this array type storing integers and presumably 42 of those in this sum array member。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_75.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_76.png)

This is this specific example， for example， could then be used to either provide the STD array template to this class in case we want to store our elements here in an STD array or the array that we implemented ourselves。

 which maybe has some special functionality as an alternative in case we want to store our elements in our special array here。

 But once again， this could also be achieved by simply having a regular type template parameter。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_78.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_79.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_80.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_81.png)

In most of the cases where we don't actually have to know about these template parameters。

 and as I already said， in practice， you do not really see template parameters。

 a template template parameters that often。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_83.png)

Now， the final thing that we。One need to talk about when it comes to template parameters here is that once again。

 similar to how function parameters work， we can also specify default template arguments for a template parameter。

 which。Pas this syn that the template parameter， which is defined as we've seen before。

 is followed by an equal sign and then a default value。This default value， of course。

 has to be a type name if we have a type template parameter。

And a literal for a non type template parameter， such as a number in case we have an integral non type template parameter。

And also similar to how function parameter work， once we have a template parameter with a default value。

 we must provide default values for all following template parameters so we cannot have a default。

 a template parameter with a default value followed by a template parameter without a default value and of course the use of this is I think rather obvious if we return to our buffer example from before we might determine that most of the time our users use this buffer with SDD byte as the type and a capacity of 1024 for whatever reason and then we can provide these as default template arguments so that users don't have to repeat this every time。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_85.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_86.png)

Alright， so this is essentially how you declare templates。

 Do you have any questions up to this point。嗯。Looking good so far。

 So let's move on to actually using templates because they would be rather useless left if we couldn't use them in some meaningful way。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_88.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_89.png)

Now， in order to use a templated entity， we need to provide template arguments and this。

Has the syntax that we first specified the template name， for example。

 the name of our buffera class here， once again followed by Angular brackets and then an argument list。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_91.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_92.png)

Where the argument list is a comma separated list of template arguments。

 which then results in a specialization of the generic template for these specific arguments。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_94.png)

Of course， the template arguments that we provide。In this case here must match the template parameters。

 so there must be at most as many arguments as there are template parameters。

 and we have to have exactly one argument for each parameter that does not have a default value。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_96.png)

There are some exceptions to this， because in some cases。

The template arguments can actually be deduced automatically by the compiler。

 and this is also something that we're going to see later during this lecture。Now， just to give you。

Some examples how this could look like。 Let's start。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_98.png)

With the type template arguments here。嗯。Where our template arguments have to name a specific type。

But this type a little bit depending on how we use the template may also be incomplete。

 The rules for this， of course， are specified in the reference documentation and are a little bit too complex to talk about in detail here。

That being said， let's take a look at our example here。

 We have a class4 that has three template parameters， two of which have default values。

 And then this， of course， means。That all of the usages of this food template down here are valid so we can provide an int for the first template parameter which then of course results in a specialization that has int as the first int as the second and double as the third template parameter。

 but we can also do this with an incomplete type or a pointer to an incomplete type or some arbitrary values for the remaining template parameter as well。

 of course。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_100.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_101.png)

If we have nontype template arguments， we have to be a little bit more careful when providing template arguments because I think as I've already said before。

 the arguments for a nontype template parameter must be constant expressions。

 which can be evaluated at compile times so while the compiler is producing assembly for your program。

 this has to be already a constant that can be evaluated by the compiler。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_103.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_104.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_105.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_106.png)

There are， there is a limited set of implicit conversions that is still allowed for non type template parameters。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_108.png)

But of course， after these implicit conversions， the type of the expression that you use as a argument for a non type template parameter must match the type of this template parameter。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_110.png)

If you have something that is not an integral type or an emdmieration type and so on as a non type template parameter。

 then there are some additional restrictions。 If you have a pointer or a reference。

 they may not refer to any sub object so a non static class member or the。

Or a member of the base class of your class， and they may also not refer to a temporary object or a string literature。

 However， since these are very rarely used anyway way。

 these restrictions do not really apply to most of the code that you will write just for completeness if you ever end up having such template parameters。

 Remember that there are some restrictions on what you can actually provide as arguments for them。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_112.png)

Now once again， with this information process， let's take a look at an example。

 we now have another full class template here that this time takes a single non type template parameter of type unsigned。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_114.png)

And then both of the following two usages would be okay。

 The first one explicitly provides an unsigned integer literal here。 So here no conversion happens。

 And of course， the literal 42 is a compile time constant。 But in the second case here。

 we have the compile time constant 42， which has has type int。

 And then we have a numeric conversion from int to unsigned。Which is also allowed。

 So this will also compile here。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_116.png)

Now。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_118.png)

We've seen here that we can provide literals easily as arguments to non type template parameters。

 However， what we cannot do。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_120.png)

I we kind of provide initially a variable or the result of a function call as a non type template parameter。

 because these cannot be evaluated at compile time by default。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_122.png)

However， there are some functions that。Perform some very simple computations that might conceivably be。

Evaluated by the compiler。 And if we write such a function and we know that this is the case。

 then we can use the constant expert keyword。To indicate that the value of a function or variable can be evaluated at compile time。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_124.png)

But of course， then we incur some restrictions because K's expert variables must have literal type and must be immediately initialized。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_126.png)

And con Exp functions must have a literal return and parameter type。Now， how can we use this？

 One example here would be that for some reason， we have a compile time constant that is our number of elements and。

We want to calculate a buffer size from the number of elements where our elements have non trivial size。

 So they have size greater than one。 Then we have to， of course。

 multiply the number of elements with。The size of the element and instead of directly encoding this here。

 which for some reason in this example， we do not want to do。

 we can have a constant expert function that takes the number of elements and then returns the size of the corresponding buffer and now that we have specified this function as being constant experter。

 we can actually use this function to calculate the argument for a non-type template parameter。

 so this code here is legal because this function call here can completely be evaluated at compile time。

 If this were a regular function， this code would actually result in a compile time error in a compile error because the compiler would probably that it cannot evaluate this function at compile time。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_128.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_129.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_130.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_131.png)

Yeah。And of course， this is also something that we've seen previously。

 if we have template template arguments， then these arguments must be a class or template。

M must be a class template or a an alias to a class template that has matching。

Matching template parameters to whatever we specified in our template template parameter。

 But since this is so rarely used， we're not going to talk about this example in detail。

 If you're interested， you can put it in Godbold and play around with it yourself。 But once again。

 you're probably not going to use this throughout this practical course and probably not。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_133.png)

That often， in the future， as well。Now， also for your own reference， we have some more examples here。

What kind of templates we can。We can specify so here we have a class template that essentially does the same as the example that we've seen before we have a fixed size array that takes elements of type T in a C style array of size N。

 then we can also define function templates。One example here would be the swap function where we want to swap two elements of an arbitrary type T so we can also define this and then of course。

 implement our swap logic without actually caring about the type T here。

Something a little bit of a spoiler for a later part of this lecture。

 something that works for function templates here is template argument deduction。

 so if we have two objects of type A， we can either invoke the swap function followed by the template argument list here。

 but we could also omit this template argument list in this case and that the compiler deduce that the type of this template parameter needs to be a for this to work。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_135.png)

Furthermore， something that we can also define as an alias template， this is sometimes useful。

 especially if you have some very nested namespaces as we show in this example here。

 so here we have an arbitrarily complex namespace here that contains a template of some type and then within some other namespace in our case here。

 the global namespace we want to use this template。

 but we don't want to write how this something extremely nested before this name in all the time so we can define a type alias that is templated with a template parameter T and then using the irregular syntax for a type alias have the using handle。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_137.png)

Name for this equals and then another type， which in our case is a specialization of this handle template here using T for the first template parameter and then a fixed void pointer as the second template parameter here。

 and then， of course， we can use this type alias with the single template parameter。

 just like any other template with a single template parameter here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_139.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_140.png)

The final thing。That we can do on a global scope is define variable templates。

 which sometimes is useful， for example， if you need to use pi within your code but need to use it with different floating point types。

 then you could define a variable template that is templated by specific floating point type that you want to use and simply convert the most precise value of pi that you can represent in a long double to this probably less precise floating point type here and then do something like。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_142.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_143.png)

AndComp the area of a circle with an arbitrary floating point precision by templating this area function with the floating point type and then use the specialization of our variable template to get the actual value of pi with this floating point type。

 but you already see this example is although useful already a bit constructed and you won't really see variable templates that often in your own code and also in other code that you may take a look at。

All of what I've said now， of course， also works within a class。

 so we can also define class member templates where we have a non templated class。And then。

 for example， have an alias template as a member of this class or a function template as a member of this class。

 And then， of course。We can use the full class itself without any template arguments because it is not a template。

 but once we call the print size function， for example。

 which has a template parameter we have to once again provide arguments for this template parameter here。

All right， once again， any questions up to this point before we continue。Looking good so far。

 Alright， So now you've seen how we can declare templates and how we can。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_145.png)

Actually use them。 But how we use a template now looks pretty obvious， but there is unfortunately。

 a little bit more going on that we。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_147.png)

Have to take into account to essentially understand why we can do certain things and we cannot do other things and also how we have to structure our code when we write templates。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_149.png)

And this whole discussion revolves about around the issue of template instantiation。And the， the。

 the motivation， why we have to talk about this is that a function or a class template by itself is。

Not a type in its own right。 It's not an object or any other entity that might be known to C plus plus。

 And in particular， this means that no assembly at all is generated from a file that contains only template。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_151.png)

Definitions。And only once we somewhere have a template specialization。

 So we provide template arguments to a template。 Does any assembly appear， So only instantiated。

Templates are actually types or objects， for example， in the case of a variable template in。

 and in order to。Obtain this instantiation， we have to specialize our template somewhere by once again using it。

And during this template instantiation， the compiler then generates the actual function or the class  for a specific template specialization。

 So if we write SDD vector of int， for example， at this point。

 the compiler generates the specialization of STD vector for int。

 and this is then a regular type name， STD vector by itself is not a type。

Template instantiation can happen through one of two ways。

 We can have an explicit instantiation where we explicitly request that a specific specialization of a template is instantiated。

 most of the time， however， template instantiation happens implicitly。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_153.png)

And this happens whenever we use a template specialization in a context that requires a complete type。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_155.png)

So。As an example， if we。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_157.png)

If you take a look at our alias template example here。

 this class here by on its own is not a type name， but down here since we declare a variable of a specific specialization of this handle class here at this point a complete type is required and at this point the compiler actually generates the code for the specialization of handle with type int and void pointer as the second template parameter。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_159.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_160.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_161.png)

Not that this also applies when this instantiation here is placed in a completely different translation unit than the template declaration。

 the instantiation still happens at the time that we require a complete type。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_163.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_164.png)

All right， so。As usual， we now have two ways in which we can instantiate a template so let's take a look at them in turn。

 and the first was the explicit template instantiation where we force instantiation of a specific template specialization。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_166.png)

For class templates， the syntax here is the template keyword followed immediately without any angular brackets by the class abstractstruct keyword and then the template name。

 and then we provide a list of arguments like we would provided when just using it for example。

 as a variable type。For function templates， this looks similar。 we also have the template keyword。

 but then of course we have the return type of our function。

 We have the name of our function template followed by the argument list。

 and then we also have to specify the parameter because of course there could be several overloaded functions by the same name so we have to know the parameter types to be able to determine which overload。

 We intend to instantiate here。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_168.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_169.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_170.png)

These explicit instantiations， of course， have to follow the one definition rule if we instantiate the same template explicitly twice。

 so for example， we have an explicit instant instantiation of STD vector in and then another explicit instantiation of the same type。

 we will end up with an ODR violation during linking。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_172.png)

对。Once we have specified such an explicit template instantiation somewhere。

 then the compiler generates the assembly that belongs to this specific instantiation。And， of course。

 this requires that the definition of the template is visible at the point of explicit instantiation。

 Not that this means that the function bodies also have to be visible at this point。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_174.png)

So the full implementation of your template has to be visible at the point where you request explicit instantiation here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_176.png)

If you do use explicit instantiation， this will most likely。

Happen for your own template types and if you determine that you want to use explicit instantiation。

 usually this means that both the definitions and the explicit instantiation should be placed in the implementation file。

A question from the chat whether explicit instantiation looks almost like a forward declaration。

 Stactically， yes， semantically something completely different happens here because a forward declaration simply makes a name known at a certain point and no code is generated for an explicit template instantiation this line here actually results in assembly generation。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_178.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_179.png)

And for this reason， you can only have one explicit instantiation to avoid one definition rule violations whereas we can have arbitrarily many forward declarations of a name because here we specifically only declare the name and we do not define it。

Now， to give you an example of explicit template instantiation。

 let's take a look at these two templates here。 we have a template class that has a single template parameter and we have a template function that takes a single template parameter。

 Now if we want to explicitly instantiate this template A with type int here。

 we could write templatestruct a followed by the int as the template argument and similarly if we want to explicitly instantiate this function here。

 we have to write。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_181.png)

The return type， which of course， if we want to specialize for float is float。

 then the function name followed by the argument list and then the parameter types here。

 which since we replace T by float are also going to be float。

And I think there is another question coming up。 So let's pause for a second。Question from the chat。

 what is a use case of explicit instantiation， This is a very good question。Most of the time。

 at least personally I have found that I use explicit template instantiations if I have， for example。

 a class that by itself is not templated。And then I have a template function as a member function of this class。

 of which I know that I'm going to call it with maybe two or three different types and nothing else because the interface of the class that I'm implementing just specifies I can call this function with let's say int unsigned or long。

 and I want to do slightly different things depending on the particular type that I use。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_183.png)

But the implementation is similar enough that I can use a single template function to implement all of this。

Then， I could。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_185.png)

Declare this template member function in the header file。

 implement the template function in the implementation file and then explicitly instantiate this member function also in my implementation file。

 The advantage of this is that then I don't have to put the definition of this function in the header file because if we rely on implicit template instantiation。

 which we're going to see in just a second we have to actually see the function definition at the point that we implicitly instantiate the template。

 which of course requires that we put the code in the header file instead of the implementation file。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_187.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_188.png)

I hope this gives you。Some intuition when you want to use them。

 and I hope that you actually followed my explanation， Let me know if this anything。

 anything of this was unclear。In the mean time， let's move on to implicit template instantiation。

 which we already。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_190.png)

Touched upon just now。So as we've previously said， using a template specialization whenever we require a complete type triggers implicit instantiation。

 and this happens only if this specific specialization has not been explicitly instantiated before。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_192.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_193.png)

Another thing that can be very surprising is that if you have a class template。

 the members are only implicitly instantiated if they are actually used。

 so only because we define a variable of a class template type。

 this does not mean that the member functions of this class template are also instantiated。

 and we were going to see。On the on the next slide that this can be a little bit surprising at first and because it allows code to compile that you wouldn't expect to compile。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_195.png)

Now， the most important thing， however， about implicit template instantiations is is what I said it just now in explaining why you might want to use explicit instantiation。

 And that is that the definition of a template must be visible at the point of implicit instantiation。

 And usually this means that all definitions of a template have to be provided in the header file。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_197.png)

If implicit instantiation is desired and this is because if we were to put the definitions in the implementation file。

 the only place where we could actually implicitly instantiate our template would be in this same implementation file。

 which of course if you think of an STD vector， is not at all what we intend to do with this if we define an STD vector。

 we want to be able to use STD vector in arbitrary translation units not just in some vector do CPP implementation file。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_199.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_200.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_201.png)

Now once again， let's take a look at an example， we now have astruct a that is parameterized with a type T and we then have a function fo that takes a parameter of type t returns t and simply adds 42 to this parameter here。

 and then we also have a function bar that is intentionally not defined here， so it's just declared。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_203.png)

Now。Once we define a variable of type A with int as the parameter， this instantiates only the class。

 but not its member functions。And then once we call a member function。

Then the code for this member functions is actually generated so here we only instantiate the code for the construct and probably the destructure of this specialization and in this next line here we implicitly instantiate the full member function。

And since the member functions are only instantiated once they are actually used。

 this code will compile， although we never define the bar function as long as it's not used it's not instantiated and we do not have any errors regarding a imaging missing definition here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_205.png)

Also， something that's important to keep in mind here is implicit instantiation happens whenever a complete type is required。

 so if we， for example， define a pointer to a specialization。

 then this specialization is not going to be instantiateated because a pointer does not require a complete type。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_207.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_208.png)

Okay。Now there are two ways to instantiate a template so when would you want to use them we've already talked about this a little bit。

 but there are some more cases that might also be useful so implicit instantiation is what you usually want when you use templates because then your template can be used with any suitable types and also no unnecessary assemblymblies generated。

 we do not generate assembly for all arbitrary possible STD vectors。

 we only generate the assembly that is required for the specializations of STD vector that you actually use in your code。

Of course， the disadvantage is that if you want implicit instantiation。

 then the full definition of your templates has to appear in the header and another disadvantage that follows from this is that the user of our templates has to compile them because the assembly is only generated when they are used and then of course this means that whoever uses our templates also has to compile this code。

Just for clarity， this is， of course something that the compiler does for you there's nothing that you have to explicitly do。

 but you will still notice this regarding the compile time if any of you for example。

 have used the Bo library which relies very heavily on templates。

 you most likely have noticed that compile time jumps up quite significantly once you start templates from the Bo library simply because your code compiles all these complex templates that the Bo library defines。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_210.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_211.png)

And this is also one point where explicit instantiation might make sense because these explicit instantiations are usually put in implementation files and then can of course be compiled into a library and shipped with a library that already contains the compiled version of a specific specialization of your templates。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_213.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_214.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_215.png)

And here， of course， you can then also put the definition in the respective implementation file and encapsulate implementation details like you would want to。

 but of course， then your templates are only usable with the types for which you explicitly instantiated them and not arbitrary types in particular。

 not types that you did not know at the time you were writing your templates。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_217.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_218.png)

So usually when you use and write templates， you want implicit instantiation。

And this is what we would recommend going for。Always as a first step。

 And then only once you determine that you have such a case as I described before where you know that your templates are only ever going to be instantiated for a limited set of types。

 Then you can decide that explicit instantiation actually makes sense。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_220.png)

Now。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_222.png)

Because the compiler actually generates code for instant instantiations。

 we have to be a little bit careful because this code is generated for each instantiation with different template arguments。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_224.png)

And conceptually， how you can think of this is that the template parameters are simply replaced textually by the template arguments。

 and then the resulting code is compiled by the compiler。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_226.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_227.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_228.png)

And of course， if one instantiation law generates 1000 lines of assembly。

 10 instantiations will generate 10，000 lines of assembly。

 so if for some reason you are constrained regarding the size of your executables。

 this is just something that you have to keep in the back of your mind when you're using templates。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_230.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_231.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_232.png)

And we've already talked about the fact that templates can substantially increase the compilation time because of course。

 you have to actually compile all these specializations。

These instantiations are generated locally for each compilation unit。

 so implicitly templates are have the keyword in line because the same instantiation can exist in different compilation units without violating the one definition rule。

 This is just a technicality that's required internally to make this implicit instantiation。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_234.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_235.png)

Approach work。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_237.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_238.png)

Even if we dolic if we do desire implicit instantiation and we have to provide all of our template definitions in the header files。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_240.png)

We should still in our opinion， prefer out of line definitions。

 So this means that even though we have to provide everything in the header。

 we should still follow the approach that you've used up to now that our class definition just contains function declarations like you can see for the convert function here or the constructor here and then provide。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_242.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_243.png)

The actual definitions after our class definition so that the interface of our class is a little bit more readable than it would be if we had some very complex function definitions mixed in with the declarations of our class members。

 However， as you can see in this example here， this requires。

A little bit of boilerplate code since every time。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_245.png)

We want to provide such a definition out of line。 We have to once again provide this template parameter list。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_247.png)

So that we can actually name our template type here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_249.png)

And， of course， this is cumulative。 If we have a template class and then we have a template member function of this template class。

 we have to repeat the template parameter list for both of these templates so that we can actually then。

Specify the correct return type and the correct type of our class here。

So this is something that's important to keep in mind simply because you code one compile。

 if you don't do this， but the error messages are unfortunately not that helpful。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_251.png)

So， yeah， just keep this in mind。 And I think there is a question coming up。 So let's。

Take some seconds and wait for that。Is the order of the template。Prameter is important in this case。

 So you probably mean these two lines。Actually， I'm not 100 per sure。 I don't。 I think not。

Or maybe they are， I think they are because。We what we have here is a member of the template class A here。

 So that's why we should specify the first the template parameters to thestruct a first and then。

We we after we have written this line， we determine， okay， this member function is also a template。

 so we have to provide。These template parameters as well after the class templates because I think the order in which these template parameters are actually bound wouldnt be wouldn't be unique otherwise。

 we need some ordering here so that the compiler knows what is T， what is R。

But I might be wrong about this。 So if you're interested immediately just put it in the compiler Explorr。

 otherwise I'll take a look at this after this lecture and then let you know through metatamost。Yeah。

All right。With this， let's move on。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_253.png)

To another syntactic thing that we can do with templates。

 a problem that we have with templates is that。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_255.png)

A program I can try to instantiate our templates with arbitrary arguments。However。

 the template itself might assume certain things about its parameters， so for example。

 it might assume that the parameter has a specific member function or objects of our template parameter type are movable or copyable or things like these。

Without any further intervention from the side of the programmer， however。

 all of these assumptions are implicit。 The template might document it this somewhere in a comment note T has to be movable。

 but this is all implicit and it's not enforced by the compiler so。In if we do it like this。

 the behavior of templates resembles duck typing， so they compile for anything that fulfills this these implicit assumptions and doesn't compile for anything that doesn't fulfill them。

 however， of course this might result in unintended uses of our templates where accidentally something works and。

Because ofduct typing， then our code just compiles， but semantically， this doesn't make any sense。

And the more serious thing here is that。Compile errors when using incorrect template arguments tend to be extremely unpleasant to read。

 they might easily result in hundreds of lines of errors where the compiler just lists the complete stack what it where it tried to replace a template parameter and then somewhere deep within the standard library。

 for example， you get an actual compile error and this。

Is extremely hard to debug and is one of the reasons why templates have such a bad reputation because they result in these error messages that make it essentially impossible to do any meaningful debugging of why compilation fails in case you used an incorrect template argument that didn't  fulfill some of these implicit assumptions。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_257.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_258.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_259.png)

And just to give you an example of a very simple example how this might go wrong is that we have another template class A here that's parameterized with a type T。

 and then we have a function bar that tries to invoke a full function on an object of type T。

 So here we implicitly assume that whatever template parameter。

 we pass to our class here has is is is first is a class。 So not an integral type。

 And second that this class contains the member function fool。 Now we can。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_261.png)

Easily just define an object of type A here with an int parameter because here。

 the bar function is not yet instantiated only once we try to invoke this bar function with an integer does the compiler instantiate this function and then determine an integer obviously doesn't contain a full member function and produces a compile time error in this line here。

 And of course， you can already imagine that even in this simple example。

 it's not obvious that the actual error lies in your template argument here and not。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_263.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_264.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_265.png)

In this line here， that's essentially unrelated to the root cause of your error here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_267.png)

Fortunately， since C++ 20， there is something that is called concepts and Con that allow us to explicitly specify at least some requirements on template parameters。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_269.png)

And once we have explicitly specified these requirements。

 the compiler can then check that whatever template argument we provided to a template actually fulfills these requirements and then with this added information。

 the compiler can then generate much more informative error messages that are actually human readable to some extent and allow us to actually figure out what's going wrong。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_271.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_272.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_273.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_274.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_275.png)

Of course， this then greatly improves the type safety of our templates because instead of implicit assumptions that we are free to violate。

 we now have explicit concepts that constrain our template parameters here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_277.png)

However， of course this can still only check syntactic requirements。

 there might be some added semantic requirements that we still cannot check through concepts because of course。

 while we can tell the compiler easily about any syntactic requirements。

 it would be very hard to tell the compiler about any semantic requirements。The standard library。

Since C++ 20 already provides us with a large set of useful concepts which are defined in the concept header and also in some other standard library headers。

 for example， the iterator head us or the ranges head us。

That we will also touch upon in a later lecture。And then these specify syntactic requirements on a number of types。

 For example， there is an SDD swappable width。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_279.png)

conceptcept that as the name implies checks everything that's syntactically required so that we can swap two types and then it also specifies some additional semantic requirements that are necessary so that swapping two objects actually make sense。

 it might compile， but it might still not make any semantic sense and these semantic requirements are then also documented in the reference documentation。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_281.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_282.png)

That being said， we can， of course， also define our own concepts。Unfortunately。

 this is a rather complex topic on its own and is beyond the scope of this lecture。

 we will try to return to this towards the end of our practical course if there is some time left and take a look at how we can write our own concepts as well。

For the time being， we just refer you to the concepts that are already provided by the standard library。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_284.png)

Which， of course， we can also apply to。Whatever templates you might write and the way to do this is that once we have some concepts。

 we can use constraints to apply some restrictions to template arguments or function declarations and there's several valid syntaxes for this that are shown here。

 So two of these options involved the requires keyword so you might have the requires keyword immediately after the template parameter list followed then。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_286.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_287.png)

By a concept such as SDD floating point， which checks that the template type here T here is actually a floating point type。

 And we can also put this requires phrase after the。The function signature here， this is equivalent。

 and we can also immediately replace the type name or class keyword by the name of the corresponding concept。

 Now this。Burden down here， of course， allows us to use only one concept whereas these and requires clauses here would allow us to use the regular logical operators such as logical and or logical or to require to specify compound constraints where we。

 for example， require that our type T is a floating point type and then apply another concept。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_289.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_290.png)

That has also， that also has to be fulfilled here。Once again， this is of course。

 necessarily incomplete。 there is a lot more going on and there is a lot more that you can do with constraints。

 Once again， we would like to refer you to the end of our practical course where we can hopefully talk about that in a little bit more detail for now。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_292.png)

Let's just stick with some observations about concepts and constraints。

 which are essentially that these are extremely useful to make working with templates a little bit easier。

 Unfortunately， a lot of the standard library doesn't use them yet。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_294.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_295.png)

We are not entirely sure why this is the case。 We assume that this has to do with backward compatibility so as not to break existing code that。

Relies on the older behavior of the standard library types。Nevertheless。

 we are free to use concepts and constraints in any new code and because of this you should use concepts and constraints as much as possible in your own code to really make explicit what kind of assumptions you make about your template parameters。

And I've already said we only scratched the surface of this topic in this lecture here。

 There are many more details in the reference documentation。 Of course。

 you're free to look at them if you're interested。 And we will try to return to this topic towards the end of the course in the meantime。

And what you should already do is you should learn to read the error messages that are produced by constrained violations。

 and you can， for example， do this by visiting the compiler Explorr that we host and play around with some simple template definitions and instantiations that for example。

 violate a concept and then take a look at the compiler output and try to match this to the errors that you intentionally made in your code。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_297.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_298.png)

Or any questions up to this point。Looking good。Right， so let's move on to more technicalities。

 As you can see， templates are。Unfortunately， a rather theoretically complex topic of C+ plus we cannot really talk a lot about implementation。

 We have to talk about a lot of theoretical stuff that we have to take care of。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_300.png)

Another example of such theoretical things are dependent names。

Because if we take a closer look at a class template， for example。

We can see that some names may be deduced to refer to the current instantiation of a template。

 and in particular as this means the class name itself which we can use without template parameters within a class template itself and also the name of any members or nested classes of a class template。

So what does this mean， this means that for example。

 if we have a template class A that defines a nested class B。

 then we can use this name B without having to write the outer class before it and implicitly this B then refers to the nested member of the current instantiation of our template here。

And similarly， for example， if you write the constructor。

 then you can simply write a for the name of the current class and implicitly this a then refers to a with the template parameter T。

 So the current instantiation of our template here。And of course。

 the same goes for member functions where we can simply call them。

 and implicitly they always refer to the version in the current instantiation of our class template。

So within classes。Everything works rather straightforward， however。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_302.png)

Once it comes to members of templates， then we have to be very careful because。

Any names that are members of templates， so for example。

 if we want to refer to thisstruct B from outside of our class， then it's a member。

 it's a nested class of our template A， and then these members are not considered to be types by default by the compiler。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_304.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_305.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_306.png)

So we see that this happens whenever we use a name that is a member of a template outside of any template declaration or definition。

 so this usage happens outside of the definition of this template。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_308.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_309.png)

Or when we use a name that is not a member of the current instantiation within a template declaration or definition。

 So we might want to， we might have a static function here。

 and we might want to call a static function that。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_311.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_312.png)

Belongs to a different specialization。 we might have a static function full parameterized by another class class R template parameter and then we might want to call this full function for the argument int。

 regardless of what R type T here is this would also be an example where we have to refer to a member of a template in our case the a specialized with int version。

 and then this name would also not be considered to be a type by the compiler。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_314.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_315.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_316.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_317.png)

Now， of course。Especially when referring to a nested type of a template。

 we know that this is a type and we actually want to use it as a type。

 but in these cases then we have to use the type name disambiguator to tell the compiler we know that this is a type。

 please treat this name as a type。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_319.png)

Once again， there is an exception to this rule because in some contexts。

 only valid type names can appear and then we can omit this disambiguator once again。

 this list of such cases is rather complex and if you want to have a more detailed overview。

 please take a look at the reference documentation。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_321.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_322.png)

In the meantime， because this was a lot of talking about something very obscure initially。

 let's take a look at an example of what this actually means here。Now。

The first thing that we have here。Is astruct a that is not a templateulator that defines a member type alias for the type float here。

那。We， then we have a second template， a second class that is templated。

And just to make these members here a little bit more clear。

 we see that we instantiate our template here with this type A。

 so this T here is for now going to be an alias to our class A here。

So we can then define another member type alias。 that is an alias for the member type alias that's contained in our template parameter in this context here。

 because we're defining a type alias。 The compiler knows that there can only be a type on the right hand side here。

So if we do not require any disambiguator， we can simply write T column column member type alias。

 and the compiler will know this is a type name here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_324.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_325.png)

However， if we want to define a pointer to this float here through this type alias。

 then we do have to use this abiguator， so we have to write a type name before actually referring to this a member type alias。

And the reason for this is just what we've seen on the previous slide without the type named thisambiguator。

 The compiler will assume that this name here， this member type alias is not a type。

 So it will assume that this is some static data member of the template parameter class here。

 and then this expression T colon colon member type alias star pointer would actually be treated as a multiplication between this static data member and another name pointer。

 which of course wouldn't be defined， but。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_327.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_328.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_329.png)

And at this point， the compiler doesn't care about this。

 So in these cases where it's not obvious to the compiler that the name that you're referring to is a type you have to prefix it with the type name disambiguator to really tell the compiler this is a type name。

 Please treat it as such。Similar rules apply to template names within template definitions。

Just like any。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_331.png)

Any member of a template here is not considered to be a type。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_333.png)

Any member any name that is not a member of the current instantiation is not considered to be a template name。

 so we have a similar problem when we want to call a templated function because here the compiler will also initially not think about this name as a template and then similar to the type name case we now have to use the template this ambiguator to tell the compiler this name is actually a template name。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_335.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_336.png)

Once again， I'm to make this more clear a brief example。

 we now have a templatestruct A that itself defines a template member function called convertver here。

Now， when can this case that we've seen up here happen， for example， it can happen。

Within another function where we define an object of type A that's specialized to int。

 and then we want to call the convert function with another template parameter here。Now。

 as I outlined above here， the compiler will initially not treat this convert name as a template。

 so if we omit this template disambiguator here， the compiler will think the convert function is not a template function and then produce a compile error because you provide a template arguments to something that the compiler thinks is not a template function。

 and then to tell the compiler that this is in fact a template function we have to use this template disambiguator。

Alright， so any questions about dependent names， I know this is rather complex。 so please。

 if anything was unclear， let me know now so that we can clear it up right away。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_338.png)

Alright， looks as if you are prepared for all the compiler errors that you might encounter during your program assignment。

 So let's move on to another technicality。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_340.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_341.png)

Which is reference collapsing， because， of course。Templates themselves and especially templated type aliases may form references to references which as you will recall aren't possible within c++ but we can still construct cases in which initially will have a reference to a reference and an example here is shown below。

 so we have another template class that defines a type alias so we have a template parameter T。

 and then we define a type alias to an R value reference to T which is of course just t followed by two ampersent characters here。

Now， we can instantiate our full template with。The type T as an R value reference to int。And now。

 of course， if we replace textually T by R value reference to in。

 we will see that this type alias here now is an R value reference to an R value reference。

 And the question now is what is going to be the type of x because we know that in C plus plus there are no true references to references。

 And in such cases， the reference collapsing rules apply。 Fortunatelyly。

 these are rather straightforward because。If we have an R value reference to an R value reference in such a case here。

 then this collapses to an R value reference。 So the type of x in our example here is going to be an R value reference to int and any other combination forms an L value reference。

 So if this type alias here would have been an L value reference or our template argument here would have been an L value reference。

 only type of x would have been also an L value reference。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_343.png)

All right。The next topic that we're going to cover is something that。

Ass a little bit more immediate applications in your own code， and that is template specialization。

 particularly explicit template specialization。None of this has nothing to do with explicit template instantiation。

 it's a separate topic that unfortunately just has a very similar name。

Explicit template specialization is useful when we want to modify the behavior of our templates for specific values of the template arguments and something where this。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_345.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_346.png)

Maybe be useful is if we have a templated find method that takes the container on which we want to search as a template parameter。

 then we can employ different algorithms， depending on what capabilities these containers have。

 So for example， if the container is an array， then we can could do binary search。

 But if it is a linked list， then we cannot do binary search we have to do a linear search。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_348.png)

。Nevertheless， we might still conceivably want to have such a templated find function so that we can use it with arbitrary containers。

 and in this case we can still achieve what we want to do here by explicitly specializing our templated find function。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_350.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_351.png)

And which allows us then to define implementations。

For certain template arguments that are different from the generic template definition。

There are once again two， two variants of explicit template specialization。 we can either。

Specify all template arguments in which case we then have a full specialization。

 but we can also only specify some template arguments which would then result in a partial specialization。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_353.png)

。So as an example of full specialization， we we have seen that we can then define a specific implementation for a full set of template arguments。

 and a full specialization has to appear after the declaration of the original template in order to define such a full specialization。

 we。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_355.png)

Write the template keyword followed by an empty template parameter list and then followed by a declaration。

Most type of templates can be fully specialized。 in particular， classes can be fully specialized。

 which we see in our example down here。 So here we have。

Some container that's parameterized by the element type here and we provide some generic implementation up here。

 and then for some reason we want to provide a specific implementation for long elements and we can do this by having a full specialization of this template here using the syntax as is shown here so we have an empty template parameter list。

We then have the declaration and of course， this declaration here then has to include the template argument list for which we want to specialize in our case long here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_357.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_358.png)

AndNow if we define objects of various instantiations here。

 we see that if we instantiate the container with a float。

 then we will use the generic implementation， if we instantiate it for long。

 then we will use this specific implementation that we wrote down here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_360.png)

For a partial specialization， it' essentially an extension of the syntax that we've seen on the previous slide。

 So once again， this has to appear after the declaration of the original template。

 And here instead of having an empty template parameter list。

 we have some parameter in our template parameter list and then。

We can use these parameters and specific values in the argument list of our declaration here。

 and you would already see this only works for class templates。As shown in this example down here。

 for example， now we have what we touched upon previously。

 we have the search algorithm that's parameterized by the container type and the value type。

 and this search algorithm contains a find function that takes a container and a value。

 and we can then。For example， specialize this search algorithm class for a specific container。

 but not for a specific element type。 And then we would write just the element type in our template parameter list。

 and in this argument list here provide。A specific type name for the container namely a vector of T。

 but leave the value type here templated by just writing T。

 and then we can implement a fine function that does binary search on a vector but still without caring about the actual type of the values here and then here in our generic implementation。

 of course， we could simply implement a fallback linear search granted that our container provides us some generic interface that we can always use something like iterators for example。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_362.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_363.png)

And I think there is a question coming up， so let's wait for some some time。

What does this specialization look like with out of line definitions？

Essentially the same as for the out of line definitions that we've seen before。

 So here we would simply have to write template class T， then search algorithm SD D vector of T。

 comma T， column column on， find and so on。So for a non specialized template。

 we simply write out all the arguments to our class as template parameters for a specialized specialized version。

 we still have some template parameters， but for others。

 we simply bind the arguments to a specific value。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_365.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_366.png)

I hope this was sufficiently clear。 Please let me know if not。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_368.png)

In the meantime， let's return to something that we've already briefly discussed towards the beginning of this lecture。

 and that is template argument deduction because in some cases。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_370.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_371.png)

We do not actually have to specify template arguments for class and function templates because the compiler can deduce them automatically。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_373.png)

Nevertheless， all template arguments have to be known to instantiate a class or function template。

 so if we want to rely on template argument deduction。

 this only works if the compiler can actually deduce all template arguments。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_375.png)

But。in some cases， we don't have to specify all of them exactly when the compiler can deduce the missing ones。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_377.png)

And most of the time， we can actually omit template arguments entirely， which makes it possible。

 for example， to use templated operators。Which wouldn't be possible otherwise。

 there's no syntax to provide template arguments to an operator such as plus。

 So here we actually have to rely on template argument deduction if we want to write templated operator overloads。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_379.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_380.png)

This is not what we're going to see in this example here here we simply have our swap function that we've seen a couple of times before and here we have a single template parameter of type T that specifies what types of objects we want to swap and then we can call this swap function on two integers without actually specifying in as the template argument because the compiler can deduce that the template argument has to be in so that the signature of this swap function matches the parameter that we passed to it。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_382.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_383.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_384.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_385.png)

So。In case of a function template， as we've seen on the previous slide。

 we have seen that the compiler attempts to deduce the template arguments based on the types of the function arguments。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_387.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_388.png)

And of course， this deduction may fail because there might be cases in which ambiguous types are deduced。

 and also something that the compiler cannot do is deduce the return type of a function。

 So this only works for the template for the function arguments。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_390.png)

The rules， once again， are very complex。 you can take a look at the reference documentation。

Intuitively。You can simply。Check if the return type of a function is templated with a template parameter that doesn't also appear in a function parameter。

 then deduction will most likely not work if the arguments to your function specify all of the template types that are used in a function template。

 then function template argument deduction will most likely work。

Except when deduction will be ambiguous， this is something that he will quite frequently encounter。

 for example， when using the maximum function defined in the standard library。

 we've repeated the signature or the approximate signature here for completeness。

 then something that will not compile if if you invoke maximum on two different integer types without specifying。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_392.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_393.png)

A template argument because then for the first parameter the compiler did use that T should be int。

 but for the second parameter the compiler did uses that t should be long。

 and then it cannot decide which is true So here you have to explicitly say。

 do you want to compute a maximum of integers or a maximum of long values。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_395.png)

For class templates， argument deduction also works， however， in a slightly more restricted scope。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_397.png)

In particular class template argument deduction only works in declarations that also initialize a variable in new and in new expressions。

 and here the template arguments are deduced based on the types of the constructor arguments。

 so similar to function template argument deduction if your class has a template parameter that does not appear in the constructor arguments then deduction will not work but if it does then you can also omit the template arguments from a class name。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_399.png)

And something where this might work here。Is for example。

 with this fo class that takes A T as is its constructor argument。

 then we can simply write initialize an object of type fo without writing the template argument list because here T is deduced to be in。

Based on this constructor call here。那。Something where template argument deduction comes in extremely handy is the auto placeholder type。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_401.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_402.png)

And this auto of placeholder type。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_404.png)

Can essentially be used to de automatically deduce the type of a variable from its initializer。

 similar to。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_406.png)

How class template and parameters are deduced from the constructor。And this deduction， in fact。

 actually follows exactly the same rules as the function template argument deduction that we've seen before。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_408.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_409.png)

And may be accompanied by the usual modifiers such as cont or the pointer or the reference。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_411.png)

Symbols here。 And this is extremely convenient when using using complex types。

 such as M standard library iters， which we can see in our example down here。

 So let's say we have an unordered map， which maps integers to strings。

And then we need an iterator into this map， then without A。

 we would have to write something like SDD on orlet map， repeat all the template parameters。

 and then access the iterator。Type here and initialize this， of course， to the beginning。

 So no one wants to read type names like this。 They are very unhandy and they make your code quite hard to read。

 It would be much better to simply replace this complex type by auto and that the compiler deduceed the type of your iterator。

Now that being said， you might now think let's always use autoto everywhere and be done with it。

 We don't have to care about specifying types or references or point us anymore。

 But this is something that we would discourage you from doing。 so although it would work。

 autoto doesn't need any modify us to work。 this makes code quite hard to understand。

 And because of this we recommend that whenever you use autoto。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_413.png)

You make this auto type as specific as possible。 So you always add all modifiers that you know to apply to the auto type。

 So by way of example， let's see what this means。So let's assume we have a function fool that returns a pointer to a pointer to a constant。

Then we could write auto and some variable name equals the return value of this full function call。

 This would be considered that code， because here。We didn't actually apply all the modifiers that we knew to auto。

 and then autoto is actually deduced to a pointer to pointer to constant。Similarly。

 if we just apply const to our autoer， then autoer is still。Am deduced，um。

I think to a pointer to pointer to int。 so this should be a typo that is deduced to constant here。

 And likewise， if we just specify the pointer symbols here， then outer is deduced to be constant。嗯。

So the， the good example how we would recommend you always write your code is。

Make the auto itself as specific as possible by adding everything that you know about the type modifiers to the auto type。

 So in our case here， we know that F returns a pointer to a pointer to a constant。

 so let auto be deduced to int and add the constant the pointer modifiers to our auto type here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_415.png)

The reason why we recommend this。Is。That auto is not deduced to a reference type。

 So it might be deduced to a pointer type， as we see here。

 and might be deduced to something consed or non consed。

 but it will never be deduced to a reference type。 And here you might actually incur unwanted copies。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_417.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_418.png)

If you do not add all modifiers to auto， So it's better to just get in a habit of adding all modifiers so that you do not run into this problem here。

And just to give you an example， what can happen here is。That's。That。

Take constructstruct A that returns a constant reference to itself from some function。

 If you now just write auto a1 equals the return value of this function here。

 then auto is not deded to a reference type。So autoto is instead reduced to const a。

 and because of that， this return value here is actually going to be copied into a1。And instead。

 if we actually do apply all known modifiers like we should。

 then auto itself is deduced to a and we then have a con's reference to a as we probably intended。

 and we can assign the return value here without copying our object a around。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_420.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_421.png)

Any questions on this， I think so。Question is， but should one use auto in these simple cases？

This is a matter of code style and personal preference。

Something that I've observed in myself when I started learning C++ is that the more I got used to C++。

 the more I used autoto， even in simple cases。There are no really good rules when you should and when you shouldn't use it。

 So this is a little bit up to intuition。嗯。Technically， nothing prevents you from always using auto。

 so maybe the best guideline that I can give you is whenever it's important that whoever reads your code sees what the specific type of a variable is or whether when you have to make absolutely sure that your variable has a specific type then use type names otherwise use auto So for example。

 some somewhere where it's。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_423.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_424.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_425.png)

Quite useful is whenever you return point as a references to some classes。

 then using auto is perfectly fine， especially if you have long class names then it might make your code more readable and more concise if it's a simple integers。

 then you can argue that you might not want to use auto but once again this is rather subjective so there are no clear rules that really tell you when to do what so just。

Try using it， try to get used to it and develop your own preferences for when you want to use auto when you don't want to use auto。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_427.png)

That being said， there are some cases we actually have to use auto。

 and this is when we want to use structured bindings。This is quite useful when working with SDD pair。

 for example， or SDD topple， because it allows us。To automatically expand the elements of a pair。

 for example， so the syntax here is always the auto keyword followed by an identifier list in square brackets and then this is either so this is always initialized to an expression but the syntax for initialization can either be the assignment parentheses or the curly brackets syntax here。

The auto typetan name here may be CV or reference qualified。

 and what this does then is that the identifiers in the list that we specify here are bound to the elements or sub objects of the initializer on the right hand side。

First， there are some restrictions on this， so structured binding can bind to arrays。

 topple like types and to accessible data members of custom。Types。And this is very useful。

 especially during iteration， especially when you iterate over associative containers such as hash tables or maps。

 which in C++ always have a pair as its value type where the first element of a pair is the key and the second element is the value。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_429.png)

So once again， rather theoretical。 So let's take a look at an example here， we define。

Our own type fo， which contains a two。Two data members that are publicly accessible。

 and we also have a function bar that returns a pair and what we can then do。I'm sorry。

 What we can then do is。Either have an array and bind the elements of this array containing four elements to foreign names using a structured binding。

 we can bind。An object， a reference to the。Data members of an object of type 4 by using the structured binding syntax。

 but qualifying the auto with the reference qualifier here。Or we can simply。

Take the return value from the bar function， which is an SDD pair and。

Have L and R referred to the first and the second elements of this pair。

 So all of these work and depending on what you intend to do with， for example。

 an SDD pair might save you a little bit of code and make your code more readable because instead of referring to P dot first and P dot second。

 you can hear specify names that actually make clear what P dot first and P do second semantically mean so you could name these。

 for example， key and value if you're dealing with an associative container or something similar that you can probably think of yourself。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_431.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_432.png)

Now， since we are already a little bit over time， I'm going to very briefly only talk about template parameter packs and leave the details up to you this part of our slides are any way rather superficial because this is once again one of the topics that are much more complex than we could explain in a single vector。

 if you're interested read our slides take a look at the reference documentation and play around with your own code examples。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_434.png)

嗯。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_436.png)

What template parameter pack essentially allow you to do is define templates that accept zero or more arguments。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_438.png)

So the syntax， how you do this is for in the template parameter list。

You have these three dots that follow either the type name for a non type template parameter or the type name and class keyword in a type template parameter。

 and once you have such a template it is then called avariic template。Where this is very useful is。

In function parameter packs where you have a veryic function template。 And then you can write the。

The arcs that you， the name that you gave to this parameter pack， followed by three dots。

 followed by a variable name， and this then allows you to have functions that take a variable number of arguments。

Yeah。So what this makes use here is parameter pack expansion where we have a pattern followed by three dots here。

 which then expands to a comma separated list of the patterns where this of course。

 must contain at least one parameter pack。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_440.png)

So to give you an example and then we'll leave it at that。

 let's take a look at this code snippet here in the first definition here， we see that we。

Have a type template parameter pack that we call T and then define the a tople template。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_442.png)

We then have a function template that also takes a template parameter pack and then make use of this template parameter pack in expansion here to define our function parameter here。

 So this function parameter is going to be a topple that contains as its template arguments。

 exactly the arguments that we used in the instantiation of this print topple function here。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_444.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_445.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_446.png)

And something that we could also do is make use of the function parameter pack here where we have another template parameter pack up here。

 but instead of expanding this parameter pack into the template arguments of the topple type we immediately make use of the function parameter pack syntax that we saw in the previous slide and essentially define a print elements function that now takes a variable number of template of arguments depending on what the template arguments to this parameter pack are and this then with these definitions here。

 what we can now write is， for example， we can now write a topple type that takes three template parameter。

 but we could just as well define a topple that takes four or 10 or arbitrarily many。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_448.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_449.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_450.png)

Tempate parameters and then for example， pass this topple2 hour print topple function here。

 and then template argument deduction will resolve the template arguments to this print topple function to be in。

 in and float。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_452.png)

Likewise， we can call the print element functions with a varying number of function parameters。

 and once again， template argument deduction will resolve this template parameter per here to consist of four integers because our types of the literals here are in。

 and then the compiler will determine that this parameter per here in this case contains of four integers。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_454.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_455.png)

The remaining slides about veryatic templates now deal a little bit with how you can actually implement veryic templates。

 So the straightforward way here is tail recursion， which you can see in this example。

 And there are also a number of fold expressions which implement essentially reductions of a parameter pack over a binary operator。

 So this is also something quite cool， however， rarely used。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_457.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_458.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_459.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_460.png)

And you can also see an example of a simple code expression on this slide here。

The final couple of things that we need to address in this lecture。

Are slightly unrelated to what we've done up to now。So。

You've already seen and maybe got an intuition that templates are a huge。

Sub language essentially of C plus plus， there's a lot of things that you can do。 and， in fact。

Since templates are instantd at compile time， we can do some form of programming at compile time。

 this is actually quite heavily used in some libraries it's used in the standard library in its extremely heavily used。

 for example， in boost this type of programming is called template meta programming socal calledled because where programming essentially within。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_462.png)

We have a separate programming language， which with which we can program whatever we can then actually use at runtime within our C plus plus programming language。

 And a fun fact about this is that with tempites， we could actually， in theory。

 build a cururing machine purely during compile time。 So this is just。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_464.png)

A an interesting side note here。 And， of course， because templates are tuuring complete。

 we can essentially implement everything that we want just in templates。 But， of course， this is。

Sometimes very useful but also rather involved to actually get right just to give you an intuition of what this means is we have an example down here where we define a factorial template that takes a non type template parameter n and then recursively computes the value of the n factorial number by simply multiplying this non type template parameter with whatever the previous factorial number is。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_466.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_467.png)

Of course here we need a base case for our recursion in case of template meta programming this is done by a full specialization so we have the full specialization for the zero factorial number which is by definition1 and then if we instantiate this factorial template here for some number what is happening is that the compiler during compileiling our code will instantiate this factorial with n equals 6 and it will then see the factorial with n equals 6 refers to factorial with n equals 5 so it will also instantiate this until we arrive at the base case and then the value here is going to be the multiplication of a number of compile time constants which of course the compiler will then immediately compute and give us this factorial with n equals6 value as the sixth factorial number all computed add compile time。

Now， you can already see maybe you can imagine some cool things that you can do with this。

 especially since our template parameters can also be types so we can do some computations on types。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_469.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_470.png)

But嗯。For the time being and。Especially for the purposes of this lecture， we're just going to。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_472.png)

Leave it at this year。 The final thing that we want to talk about is the static assert declaration。

 which is。Rather useful because it's also part of this compile time aspect of C plus plus。

 which similar to the regular assert declaration。That you've already seen allows us to check some condition with the difference that the regular assert does this during runtime。

 whereas the static assert does this during compile time。

The syntax here is simply the static assert keyword followed by a Boolean constant expression or a Boolean constant expression and a message。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_474.png)

And this Boolean constant expression of course must be something that evaluates to bull at compile time。

 so it can either be a simple arithmetic expression， for example。

 some simple computations or calls to constant expert functions。

 and of course it has to evaluate to bull。

![](img/3c84ea7bb30301c7e98b16aeda2b580a_476.png)

Something where this might be useful is this down here in its present from this example doesn't really make sense。

 if we had an integer as our template parameter end here。

 then we could check with a static assert that we do not try to。

Specify a buffer with negative size for our example with an unsigned as the non type template parameter here。

 we can check that our buffer is never empty by statically comparing this template parameter to 0。

 so whenever we try to instantiate this non empty buffer with n equals 0。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_478.png)

![](img/3c84ea7bb30301c7e98b16aeda2b580a_479.png)

Then we will get a compile time error that this static assertion here failed， which， of course。

 is better than getting a runtime error that we then have to debug。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_481.png)

Right， and then on this final slide， once again， something that you can take a look at if you're interested。

 this is another example of template meta programming where we do some computations with type just like I said before。

So with this， our lecture is concluded for today， please let me know if there are any closing questions。

Yeah。Doesn't look like it。 So then see you on Friday。 Goodbye everyone。



![](img/3c84ea7bb30301c7e98b16aeda2b580a_483.png)