# 【EDUCBA】应用现代Java特性编写简洁高效的代码 ｜ Apply Modern Java Features for Clean and Efficient p03 01_03_01_流媒体教程 -BV1twFSzNEZ3_p3-

Now， same example will see using streams object。 Okay。

 so what we'll do is let us create here again a new Java class。And。Let's。Import again， here。

The Java dot u till dot。Add a list， and。Java dot u dot list， after which， let's create。

Static void main。What。String arguments。

![](img/af25830157e35371d8bd7722b0f6912a_1.png)

And inside this will now create again of type string see。Names， which is equal to new。



![](img/af25830157e35371d8bd7722b0f6912a_3.png)

A a list of type string， and then we say name start add。Again。Name， start add。Name st。Add。And last。

Say， Steve。And then here now using this stream and the Lada expression willll create here a long variable count willll say is equal to name st stream。



![](img/af25830157e35371d8bd7722b0f6912a_5.png)

Dot use filter。Sair Estia。StR dot length。

![](img/af25830157e35371d8bd7722b0f6912a_7.png)

Less than 6。Dot count。And then we say system not out or print， Elen。See， there are。Value of count。

See。Stringngs。Witht。Lent。Less than6， okay。

![](img/af25830157e35371d8bd7722b0f6912a_9.png)

Now let's see the output again， getting the same thing， but see the difference。



![](img/af25830157e35371d8bd7722b0f6912a_11.png)

How many lines of code we have written to achieve the same thing without using strings and how many lines of code we have written to achieve strings。

 the same output using the stream object and the Lada expression。

 so that is more simple and saves the coding lines and get and gets you the same result also right？



![](img/af25830157e35371d8bd7722b0f6912a_13.png)

![](img/af25830157e35371d8bd7722b0f6912a_14.png)

So now so now let us understand how to work with the stream in Java now as we have seen the working of stream can be explained first is creating a stream。

 then performing the intermediate operation on the initial stream to transform it into another stream and so on a further intermediate operations in the above example we have used here the filter operation is the intermediate operation there can be more than one intermediate operation also and then we can perform the terminal operation on the final stream to get the result in the example here we have used count as a terminal operation So now coming to your Java stream features stream basically does not store the element it simply transforms the aggregate operations like filter count。



![](img/af25830157e35371d8bd7722b0f6912a_16.png)

To get the basically your desired stream of data， then the aggregate operation that we perform on the collection ari or any other data source do not change the data of this source。

 they simply return a new stream so for example the code that we have is basically filtering the strings with less then the length less than6 using a stream operation but it doesn't change the element of the list and all the stream operations are lazy in nature which means that they do not execute it until they are needed。

 for example if we want to display only the first two elements of the list using stream。

 then stream operation would stop at the end of second after displaying the second element of the list Now let us see some examples on Java strings we'll see first for iterating and displaying your selected integer values so let us create a new Java class and let us。

Add here， same， Java dot， u dot。Stream dot star after which here will add。Public static void main。

 which takes string。Aguments。And here， we create。Say stream， dot。Irate1 comma count till count plus1。

Dot。Filter you're using here number。As。Number modulus 3 if it is equal to 0。Dot limit。six。Dot。For it。

Say system do out dot print El， and here we will be using double colon for printing the value。

Then we end it。 So now if we execute， we get it。

![](img/af25830157e35371d8bd7722b0f6912a_18.png)

Till the6 value is reached is the limit as 6 and every value of every number that we are printing is modular 3。

 the remainder comes to 0。 Okay， so those all values have been basically displayed。 Similarlyly。

 let's see another example for concatenating two streams together。 So let us create a new Java class。



![](img/af25830157e35371d8bd7722b0f6912a_20.png)

![](img/af25830157e35371d8bd7722b0f6912a_21.png)

![](img/af25830157e35371d8bd7722b0f6912a_22.png)

![](img/af25830157e35371d8bd7722b0f6912a_23.png)

And let's remove this patch， well have to import Java dot uil dot。😔。

Aris and import Java dot u dot list， Also Java dot u dot， stream dot stream。Okay。

 and then in this class， let's create。Public。Stantatic wired man width。

String arguments as the parameter。 and first you will create here of tight string。



![](img/af25830157e35371d8bd7722b0f6912a_25.png)

Sa alphabet。Okay， is it word do。A a taught as list。And here we'll give a B， C。

 then we'll create here another list of type string again， name is and names is equal to。



![](img/af25830157e35371d8bd7722b0f6912a_27.png)

See A start eyess list。We'll give your sa。

![](img/af25830157e35371d8bd7722b0f6912a_29.png)

Said John， and。Audio。Then we'll create your stream。Of string type， say O3 is the object is equal to。



![](img/af25830157e35371d8bd7722b0f6912a_31.png)

Stream dot use concat， say alphabet。Dot。Stream， sorry。We have this string method， comma， names， dot。

Street。Okay， and then we say O string dot for each。And here we have SDR。

Print the value using system dot out dot print， SR。Without space。Okay。

 let's try and execute this wge。Everything concatenated together and printed。



![](img/af25830157e35371d8bd7722b0f6912a_33.png)

Right？So now we will see examples on stream filters in Java Okay so here the filter is the intermediatemittent operation that reads the data from a stream and returns a new stream after transforming the data based on the give it condition now let's take some simple examples on this so the first example will do is we will be creating a stream from a list of names using this stream method and then we are creating another stream of long names using your stream filter okay so the stream filter transforms the data of one stream into another so let us see how does it creates let's go here for a new Java class and in this we would be first of all importing。



![](img/af25830157e35371d8bd7722b0f6912a_35.png)

Jama dot uil dot Ar， then。Java dot， U dot list。Then， Ja dot， uil dot。Stream dot stream okay。

 and then here let's create first public static void main with string arguments。

And inside this well first create a list of type string same names is equal to。Sa， Ari st。



![](img/af25830157e35371d8bd7722b0f6912a_37.png)

As list and here be give us a name， we are giving here some big names， say meicandry Sana。John。And。

Cly。

![](img/af25830157e35371d8bd7722b0f6912a_39.png)

Okay， and then we'll create the stream of all names using stream of tight string。

 say all names is equal to name do stream and then well create stream。Of against string type。

 saying long names is equal to。All names dot filter。And here we use STR。STR dot say length。

 if it is more than 6， make all those together， and then we say long names dot。For each。

 use your STR and print those on system dot out dot print。Using STR and a space in between。

So youll get all the long names together okay thats how we have used the filter operation here now we will see another example for filter and collect so we will apply a filter in one line okay and the collect method to collect the final streams are converted to the list so now in this case let's create a new Java class here again。



![](img/af25830157e35371d8bd7722b0f6912a_41.png)

And we will。Have to first。Import the u dot。

![](img/af25830157e35371d8bd7722b0f6912a_43.png)

Aris and import Java dot u dot list。Import Java dot， U dot， stream dot。Collector。

Or collectors and then inside this class， we will create。Public static， void main。

String object arguments。

![](img/af25830157e35371d8bd7722b0f6912a_45.png)

And inside this we create string same names is equal to array do as list again well take here。



![](img/af25830157e35371d8bd7722b0f6912a_47.png)

Some same values。

![](img/af25830157e35371d8bd7722b0f6912a_49.png)

Okay， similarly。Last one。Say chare， then for converting the list to stream well use your list stream。

 say long names is equal to name dot stream， and then to filter the stream to create a new one well use here will not end this here well use dot filter and say STR。



![](img/af25830157e35371d8bd7722b0f6912a_51.png)

![](img/af25830157e35371d8bd7722b0f6912a_52.png)

Use your D lambda equation， STR dot length， more than 6。Again， dot values use collect using the。

Collector start。To list。Okay， to collect it and then we use here long names dot。For each in bracket。

 system dot out double colon。Print L so now if we execute。

 we again get all the names printed on the strip。

![](img/af25830157e35371d8bd7722b0f6912a_54.png)

Now lets see another example using the stream filter with multiple conditions okay now here we have only seen there is only one condition in the filter method。

 we can also have more than one condition in the filter okay so well see an example wherein we use the double and operator that is the logical operator and in the filter so let us create a new Java class here and we will start with first import statement so well have import Java dot u dot array is import Java dot uil dot list import Java dot uil dot stream dot。



![](img/af25830157e35371d8bd7722b0f6912a_56.png)

![](img/af25830157e35371d8bd7722b0f6912a_57.png)

![](img/af25830157e35371d8bd7722b0f6912a_58.png)

Again， collectors。And then， create。Public static void main。😔。

String arguments inside this main method， create first of type string same names。Is equal to。

Ari taught as list and will pass here again。The same names。First one， says Sansa。Sa John。Then。

 the last one。Say Jorey， then we'll create of type string again。

 and here well give say long names is equal to names dot。

Stream and here we use the filter condition for first STR， the ST dot length。

 if that is more than six is one condition here we are using and saying STR dot length if it is less than 8。

 so here there are multiple conditions given then we use a collect saying，Sa collector start。

Tool list。😮。

![](img/af25830157e35371d8bd7722b0f6912a_60.png)

End it with the semicola， then use long names dot for each， and here we use system dot。

Out double colon， print an。So now we get only one which is more than 6 and less than 8。

 so it is 7 that is why the output has been displayed so here we have used multiple conditions in the stream filter。

So now let's see another example for a stream filter and the map methodology Java。

 So let's create a new Java class and。

![](img/af25830157e35371d8bd7722b0f6912a_62.png)

We'll start with the import first， saying import Java dot u dot。Addice。Import Java dot， u dot。

List and import。Java dot。You till do。Stream dot。Collectors， then public static。Voide main。

With string arguments and now we'll give here in teacherger say nu is equal to array start as list let's give here some values。

 then let's create。Indija。And。C squares is equal to num dot。



![](img/af25830157e35371d8bd7722b0f6912a_64.png)

Stream。And here we use dot map， say N， n multiplied by n。And do。Collect is。Collector start tool list。

Then。System dot out。Dot print Ellen。Say squares to be printed so you get there the square of2，3，4。

5 and6 being printed， right。So now let's move on to the interface changes in Java 8 now prior to Java 8 interfaces in Java can only have an abstract methods all the methods of interface are public and abstract by default but Java 8 allows interfaces to have default and static methods also the reason to have default methods and interfaces is to allow the developers to add new methods to interface without affecting the classes that implement these methods。

 so let us see an example of default methods in interfaces okay。



![](img/af25830157e35371d8bd7722b0f6912a_66.png)

That is we have by the name default created and which we can implement and call it。

 so let us create a new Java class here。

![](img/af25830157e35371d8bd7722b0f6912a_68.png)

And。

![](img/af25830157e35371d8bd7722b0f6912a_70.png)

Now， here we we be adding an interface。 Okay， so let's add。



![](img/af25830157e35371d8bd7722b0f6912a_72.png)

An interface in my inter。And inside this will add a default void。New method。

Which we are using system dot out dot print L， say。



![](img/af25830157e35371d8bd7722b0f6912a_74.png)

Newly added default method。As a string being printed， okay， then we take here。

Another saying void existing method， which takes a string。STR as the parameter。

 which has no definition then in the new class okay here we will write down implements interface as my and then here we will be having。



![](img/af25830157e35371d8bd7722b0f6912a_76.png)

Say public void。Existing method。

![](img/af25830157e35371d8bd7722b0f6912a_78.png)

Okay， and this is taking string。

![](img/af25830157e35371d8bd7722b0f6912a_80.png)

StR as the parameter， which has to be implemented here。 So here we are saying。



![](img/af25830157e35371d8bd7722b0f6912a_82.png)

System dot out dot。

![](img/af25830157e35371d8bd7722b0f6912a_84.png)

Print Ellen， and we give here says string is the value of SR being printed and then。

We create here public。Static。Vmin with。String arguments as the parameter。

 and we create the object of the class。 C you class 15。N1 is equal to nu。New class 15。

Then we create N one dot。

![](img/af25830157e35371d8bd7722b0f6912a_86.png)

New method。And we create n1 dot existing method here we say Java 8 is easy to learn and let's execute we get both the methods called so this default method you cannot create prior to Java 8 if you have8 or the above version of it。

 you can create those in that similarly static methods in the interfaces now let's see another example of a static method creation in interfaces。



![](img/af25830157e35371d8bd7722b0f6912a_88.png)

So now in the same program， we have created the default method here， Similarlyly。

 we would add here another method， okay， that is lets add here。



![](img/af25830157e35371d8bd7722b0f6912a_90.png)

Say staticatic void。安那到。

![](img/af25830157e35371d8bd7722b0f6912a_92.png)

new。Metter。Which we are using your system dot out dot print， Aen， say。Newly added。Static method。



![](img/af25830157e35371d8bd7722b0f6912a_94.png)

After that we have again the existing method where we are implementing we have implemented this method。

 now we have called the new method okay and now to call static we can directly call my enter dot another new method and then call the existing method and now check the output for static。



![](img/af25830157e35371d8bd7722b0f6912a_96.png)

![](img/af25830157e35371d8bd7722b0f6912a_97.png)

Okay， similarly， well see another example for abstract classes versus the interfaces now。

 so now let us create a new。

![](img/af25830157e35371d8bd7722b0f6912a_99.png)

Java class。 And in this。We would be creating first interface。

 semi my enter1 here we have a default void。

![](img/af25830157e35371d8bd7722b0f6912a_101.png)

![](img/af25830157e35371d8bd7722b0f6912a_102.png)

New method。Then here you are adding。System dot out dot。Spriprint。Ellen， saying。Newly added。

Default method。Okay， then you have void。Existing matter with string ete。

And then you have another interface saying my inter。2 okay， and in this also。

 you have a default void。Sa妞。Metter。And here also you are printing system dot out dot。Print Elen。

Sewly added。Default method。Okay， and again here also you have void DISP， which is of type。String。

 STR。Create。Then in this class， you are going to implement。My inter one， and also。My inter2。Okay。

 so obviously you will need to add public void。Say existing。Metter with the。

String parameter STR implement this here saying the system dot out dot print All string is and the value of STR Similarlyly。

 then you say public。Vyd said DISP， again， a string。STR and here also you see system dot out print L。

 say string is again。Print the value of SR， then you have public void or sorry public。

Static void main。Which is taking string。Arguments。And inside this， we create the class object。

16 and2 is equal2。New。New class 16， and then we say N2 dot。New metal。Okay。

 now what is the mistake here you have here implementing both the interfaces。So public class。

 this implements my enter one and then my enter2 also， and my enter one has this existing method。

 which you have implemented and then you have this void displayplace string S。

 which also you have implemented。 So now if you try to execute。

 you will get here and error that is you are trying to execute here。

 duplicate which are incompatible， because both has the same new default method， Okay。

 so how do you solve this issue in that case。 what you will have to do is you will have to implement that。



![](img/af25830157e35371d8bd7722b0f6912a_104.png)

![](img/af25830157e35371d8bd7722b0f6912a_105.png)

Inside this new class， you will see， say after this， public void new。Metter。



![](img/af25830157e35371d8bd7722b0f6912a_107.png)

And here you will say。System dot out dot print L， say。Implementation of。Default method。Okay。

 so now if you try to execute you will get the output so now you will have to implement the default method also inside the implemented class so we'll continue more on such examples but in the next session that's it from this session thank you very。



![](img/af25830157e35371d8bd7722b0f6912a_109.png)

![](img/af25830157e35371d8bd7722b0f6912a_110.png)

![](img/af25830157e35371d8bd7722b0f6912a_111.png)