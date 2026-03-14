# 【EDUCBA】应用现代Java特性编写简洁高效的代码 ｜ Apply Modern Java Features for Clean and Efficient p06 02_03_01_尝试资源增强 -BV1twFSzNEZ3_p6-

So now we'll see try with the resources enhancements。

 Now this tri with resource statements was first introduced in Java 7。

 Okay now this statement have received a major enhancement in Java 9 let us first understand what is this try with resources now to avoid the redundant code that we have to write for exception handling The advantages of this statements are the try with resources closes all the resources that is the file database connection network connection etca automatically and no need to close them explicitly。

 This prevents your memory leaks and with the help of try with resource we can reduce the unnecessary lines of code and make the code more readable。

 So now we'll foresee see how we use to write the code in Java 7 using try with resources and then we will see similar example what were the problems coming in Java 7 and then how can we solve them using Java 9 try with resource enhancements。



![](img/abbc069e6a32dad9222cddc0648fbeea_1.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_2.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_3.png)

So let us foresee one example in Java 7， so what we'll do is let us create here a new Java class and let's remove the commence part。



![](img/abbc069e6a32dad9222cddc0648fbeea_5.png)

And then here well see import Cja dot dot au dot。Say file not found exception。

 and we say import Javava。 o dot file output。Sp okay， and then inside this class。

 we will have public static void main。What。String arguments。 And here we give say through the file。

 not。Fhund。Exception。Okay， and then inside this main method， we are first using a tribe block。

Now a try is going to have a catch saying catch exception E Okay， so here inside this try。

 we are going to put in bracket， say file。

![](img/abbc069e6a32dad9222cddc0648fbeea_7.png)

Output。Strering object as a file。Output stream is equal to new file。

Output string and here we are going to give a file name which is there Okay。

 now we will create one normal text file first Okay now we have created this book dot Txt file here So now we are going to give here the namebook dot Tx okay after this let us give a semicolon and close the bracket then we open the tri block and here we are giving a string semi string is equal to VR。



![](img/abbc069e6a32dad9222cddc0648fbeea_9.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_10.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_11.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_12.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_13.png)

Writing this。Line in the output。

![](img/abbc069e6a32dad9222cddc0648fbeea_15.png)

Fight。After which， we give her bite。

![](img/abbc069e6a32dad9222cddc0648fbeea_17.png)

Save by it， ari。Is equal to giving my string dot。Get bytes and then we use the file output stream dot。

Right， and we give the value of byte 10 and then use system dot out dot print L saying the given。



![](img/abbc069e6a32dad9222cddc0648fbeea_19.png)

String is。Written in the file。Successfully。Okay， after this， if any exception happens。

 we catch it and we print the value of E on system dot out dot print El。 Now。

 if we try to execute this， it says the given string is written in the file successfully。 Now。

 what was the problem is， Now， there were certain issues with the try with resource statement。 Now。

 this statement did not allow the resource to be declared outside the statement or the blocks scope。

 Now， for example， let's create here another。

![](img/abbc069e6a32dad9222cddc0648fbeea_21.png)

Classs， okay。

![](img/abbc069e6a32dad9222cddc0648fbeea_23.png)

So that it is easier for us to understand First thing is let us import the Java dot iio dot file。

 not found exception and import Java dot iio dot file output stream， then let us have your。



![](img/abbc069e6a32dad9222cddc0648fbeea_25.png)

Public。Static void main with string arguments and。Here， we will have。Say truth。File not。Found。

Exception， okay， so then inside this， if we create object like this saying file。



![](img/abbc069e6a32dad9222cddc0648fbeea_27.png)

Output stream， say file output。

![](img/abbc069e6a32dad9222cddc0648fbeea_29.png)

Stream is equal to new。File output stream and we give here。Say book dot Txt。

 and then if we say try and we pass here file。Output stream as the parameter。

 and we open the tri block we create here a string。



![](img/abbc069e6a32dad9222cddc0648fbeea_31.png)

Sa my string is equal to， say we are。Writing this。Line in the。Output file。And then we use here bite。

Say byte array is equal to my string。Dot。Get the bytes and use file output stream dot right method and write bytes in that then you system dot out or print El saying the given string is。



![](img/abbc069e6a32dad9222cddc0648fbeea_33.png)

Written。In the file。Successfully， and after that。Here we handle the catch for any exception E。

And handle here system dot out dot print El。Value of E okay， now if we try to execute this。

 we'll get here an error。 Okay， now this is a compile time error。 fine， now。

 because the resource is declared outside the scope of the try with resource statement。

 Okay so now to solve the above error we had to do a work around in Java 9。

 we basically had to say something like after we create this we have to create here also in tried or resource another object and then use that。

 okay， so which was a very hectic one to do it。 instead of that， okay。

 now let us try this first and then we will see another example。

 so here we have created file output stream object but let us copy down this is equal to。



![](img/abbc069e6a32dad9222cddc0648fbeea_35.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_36.png)

File outputs stream we will give here， and we will replace that here。 So we are going to use this。

Here is equal2。Say this and this will give a name I too。

 So youre recording a second object of that and then here we say the second object dot right and print a given value。

 so now if we try to execute this will work properly okay。

 but this is a very unusual way of handling this instead in Java 9 we have an enhancement on this drive with resources and now we'll see how can we do that so now if we go for a new Java class and。



![](img/abbc069e6a32dad9222cddc0648fbeea_38.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_39.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_40.png)

Lettuce。First， import Java。ot file not found exception and import Java。

ot file output stream and let us create here now。

![](img/abbc069e6a32dad9222cddc0648fbeea_42.png)

Okay， now in this。Let us copy down this scored， as it is。



![](img/abbc069e6a32dad9222cddc0648fbeea_44.png)

In the class， okay， the only thing is now。Let's not create this。



![](img/abbc069e6a32dad9222cddc0648fbeea_46.png)

And only。Will pass here。The same object。And。Let's try to execute this。



![](img/abbc069e6a32dad9222cddc0648fbeea_48.png)

Let us save this。Okay， so now this works properly in the Java 9 feature。Okay。

 so with this we have seen an enhancement on the try catch okay or the try with resources in Java 9 so we'll see more on such examples but in the next session that's it from this session。

 Thank you very much。

![](img/abbc069e6a32dad9222cddc0648fbeea_50.png)

So now we will see in Java 9 the another enhancement that is anonymous inner classes and the diamond operator Now first let's understand what is a diamond operator it was basically introduced as a new feature in Java X7 and the purpose of this diamond operator is to avoid the redundant code by leaving the generic type in the right side of the expression Now a problem with the diamond operator while working with anonymous inner classes R。

 now to understand that let us take an example， okay like in Java7 it allows us to use diamond operator in normal classes but it didn't allow us to use them in the anonymous inner classes。

 for example， if we create here a new Java class。

![](img/abbc069e6a32dad9222cddc0648fbeea_52.png)

Let's remove the comment part and we will have to create here an abstract class saying my。See， okay。

 now this is we are creating here as。Say abstract T add， which is taking T nu。And safety。Numb2。

And after this in this class， we are having public systematic static void main。

 which is having string arguments as the parameter。

 and here we are saying my C object here we are passing， say。In teacher， say OBj is equal to nu my C。

Object created， and then we open this here and we give， say integer add。Saying integer x comma。

In teacher why。And inside this we say return x plus y semicolon， and here also a semicolon。

 after this， we say integer object sum is equal to say Oj dot add0010。

1 as the parameters after which we say system dot outdot print Elen the value of sum on the command screen。

 which gives us the value S 2，0，1。 Okay， now over here。

 let us see the enhancement that we have in the diamond operator。

 So the Java 9 improve the use of this diamond operator and allows us to use diamond operator with even anonymous inner classes。

 Now for that， we will have to create a new class to understand the use of it。



![](img/abbc069e6a32dad9222cddc0648fbeea_54.png)

And unlike the other classes， we will remove the comment part。

 we again create here an abstract class， saying my C1。which is having again of anonymous type。

 and it is also having an abstract T addd， which is having T nu and comma T say nu 2 after this we are having the main class which is having public static void main with string arguments and in this we are creating say my C1。

Of type in teacherger， say OBj is equal to saying new。My C one。

Open this and open the bracket and here we say integer add we pass here integer x comma integer y。

 and inside this we say return x plus。Why。Then let's close it and again here， okay， we will say。

In teacherja。Says sum is equal to say OBj add and 101， and we say system dot out dot print Ellen sum。

 but now what we'll do is we will go to the properties here in the source package and we will make this as Java 7 and now we will try to execute it。



![](img/abbc069e6a32dad9222cddc0648fbeea_56.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_57.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_58.png)

So now if we try to execute， we'll get here an error。 and this is。

 you cannot infer the type arguments for anonymous inner classes。

 It is not supported in the source 7， so。

![](img/abbc069e6a32dad9222cddc0648fbeea_60.png)

Unlike if we try to execute this in the Java 9 or any higher version of it。

 then we won't get any error and this will execute properly like now we would be getting here the output as 201 after the proper execution of it right so this will only execute in Java 9 but not the earlier versions of it Similarlyly let us move on to another annotation in Java 9 now here we have aa where argument notations or annotations to suppress the unsafe operation warnings that arises when a method is having some where arguments or variable number of arguments we can see so the a safefe where argument annotation can only be used with methods that is final or static methods or constructors that。



![](img/abbc069e6a32dad9222cddc0648fbeea_62.png)

Okay， so that cannot be overridden because an overriding method can still perform some unsafe operations on their variable number of arguments So in the Java 9 extended the use of the safe where argument annotation and it can now used with even the private methods as well this is because the private methods cannot be overridden okay so now earlier this annotation was limited only to final or static methods or constructors now it can be also used with private methods okay now when do we do not use the Saware argument annotation now over here let us see an example now let us create a new Java class and let's remove the comment part here and we will first say import Java dot Ut dot。



![](img/abbc069e6a32dad9222cddc0648fbeea_64.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_65.png)

At a list。After which we will import here Java dot Uil dot list。 and then in this class。

 we will first create a private void。

![](img/abbc069e6a32dad9222cddc0648fbeea_67.png)

Say print， your will give list。And names and then inside this we run a four loop saying list of type string same name names and here we are saying system dot out taught print L name in bracket to be printed okay here we end this particular method after which we have public static void mean which is taking this string arguments as the parameter and here we are creating object new class 34 say obBj is equal to new。



![](img/abbc069e6a32dad9222cddc0648fbeea_69.png)

New class 34， and then we create list of type spring as list is equal to new array list。



![](img/abbc069e6a32dad9222cddc0648fbeea_71.png)

Of type， string。 And after we have created this， we add the item in that， said Kevin。



![](img/abbc069e6a32dad9222cddc0648fbeea_73.png)

Then we again say list to dot add， say Rick， then list to dot add， say Negan and list to dot add。

 say。Suhu。After this， we say OBj dot print and we give there the value list。



![](img/abbc069e6a32dad9222cddc0648fbeea_75.png)

Okay， so now over here。

![](img/abbc069e6a32dad9222cddc0648fbeea_77.png)

Okay， now here we have got certain warnings other than that。

 we have not got any error while executing it， but now with the same example， okay。

 before this private method， if we use at the rate， say safe。Where。Arguments， okay。

 and then we give this private void print width list and names。

 and then we use a for loop for printing the values there。 again。

 create the object and try to print it。 So now you won't get any errors as such or any warnings also as such if you are trying to execute the same okay。

 now similarly， let us see some stream API enhancements in Java 9。

 So now already we have learned that in Java 8， we had introduced the stream API along with several other cool features also。

 now， let's see in Java 9， what is this stream API improvements are Now。

 in Java 9 have added the following four methods of to the stream class。

 Now since stream is an interface the methods added to it are default and static。

 first is your drop while。 take while iter it and of nu label。 Now let us see what is。

Stream drop while method2 Okay now here we will see one an example of the same of the method drop while which will drop all the elements of the stream until the given predicate falls。

 So let us see an example of this。 Okay， so let us create here a new。



![](img/abbc069e6a32dad9222cddc0648fbeea_79.png)

![](img/abbc069e6a32dad9222cddc0648fbeea_80.png)

Java class now。And we will have to go for import first。

 import say Javava do uil dot stream dot star and will create here public。😔，Static wide main。

 which will take。String arguments and inside this will first create of type in teacher say my stream。

Which is equal to say stream dot of here we pass some values， 11，2240，6000， and then we say。

My stream dot， we use drop file in bracket we use nu。Numb is less than 50 dot， say for each。南 in。

You print a value of print Alllen the value of nu， so we are saying drop while the value of nu is less than 50 so whichever less than 50 would be dropped apart from that whichever values remain abbing given to us as the output now similarly we will see another example okay of similar one wherein we use the stream method of take while for that Okay。

 so we have seen here the example for drop file now let us take the example for take while so now in this let us create a new。

Java class again， and unlike the earlier one will import Java dot U dot。



![](img/abbc069e6a32dad9222cddc0648fbeea_82.png)

Stream dot star。And let's take public static void。Mean with string。Arguments。And inside this。

 we will create again。Stream off， say。In teacher。And object semi my。Stream is equal to。

Say stream dot。Of in bracket，17，20，30，40，60，91，20。After which， we say here。My stream， dot。

Safe take vi in bracket， numb。Were in number， less than 50 dot。Runner for each loop。Noum。

And print those values using。System dot out dot。Print Elen， the valley of nu。Okay， now here。

 what mistake have we done is we are creating here inside main the object of stream。😔。

In bracket integer object as my stream， which is equal to we are giving here stream dot of。

 and we have given here the values have not ended here with the semicolon。 Okay。

 so now let us try to execute。 Now well get， we are saying take while。

 So take while the value of nu is less than 50。 So only those value which are less than 50 would be picked up。

 The value which are more than 50 would automatically be removed from the given list That is what is the method of take while。

 Now， let's see a similar example for a stream iterate method。 Now。

 the iterate method basically takes three arguments。 First argument is the initializing value。

 the returns stream starts with this value。 Second argument is the predicate。

 The iteration continues until this given predicate returns fall。

 and the third argument updates the value of the previous iteration。

 So now over here suppose we create。

![](img/abbc069e6a32dad9222cddc0648fbeea_84.png)

An， or rather， we can do it in the same thing。 Now， or let's try to do it here itself， say in stream。

Dot。Irate， and here we give one， So let's give here comma sum。



![](img/abbc069e6a32dad9222cddc0648fbeea_86.png)

Is numb less than 30 than numb。

![](img/abbc069e6a32dad9222cddc0648fbeea_88.png)

Saying none multiplied by3 dot。Using for each， giving none。



![](img/abbc069e6a32dad9222cddc0648fbeea_90.png)

And saying system dot out print Ellen the value of num。

 So now here you can see the first is the output earlier second is from 1。 Okay。

 we are saying multiplly by 3。 okay， then again，3 multiplied by 3，9 again。

9 multiplied by 3 comes 27 Soil it is less than 30 we are getting the output。

 S we give here less than 50。 So then the output will change in this case。Now。

 starting from one wherein numbers is less than。50， we have told。Let's try to execute ya。

 but 9 into 27 is not less than 50。 So what we'll do is let's take it less than 200。Yeah。

 so then the value have extended because then you are trying to multiply nu with the value 3 over here。

Okay。That's how you get the values here executed。 So now let's see the last type of method with the stream that is the off and nullable。

 So now here we'll see how to use this method let us create in the same program。



![](img/abbc069e6a32dad9222cddc0648fbeea_92.png)

Sa， let's create again here。Stream of spring type will give your name as my S is equal to stream dot of。

Nbel。No。😡，And then， we use here。Say my S dot for each STR， and we give here system dot out dot。

Print L， SR okay。Let us try and get the output。Now it is if it is nullable。

 okay now this method is basically introduced to avoid the null pointer exception。

 so this method will return an empty string if the string is null。

 it can also be used on a non empty string where it returns a sequential stream of single element。

Okay， so we'll continue more on such examples， but in the next session that's it from this session。

 thank you very much。

![](img/abbc069e6a32dad9222cddc0648fbeea_94.png)