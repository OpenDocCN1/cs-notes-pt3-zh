# 【EDUCBA】应用现代Java特性编写简洁高效的代码 ｜ Apply Modern Java Features for Clean and Efficient p05 02_02_01_数组并行排序 -BV1twFSzNEZ3_p5-

After which we are going for a meing of both the strings。 Okay。

 so here we are creating string joiner， say。

![](img/fa26a2e7d764e756452b84587ff71b0f_1.png)

Merge string is equal to we are saying here my string。Dot merch in bracket。My another string。

 and then we say system dot out dot print Elen。We print here the value of merge string。



![](img/fa26a2e7d764e756452b84587ff71b0f_3.png)

Now let us see the output first we get the first string that we have passed then the second string with a prean suffix and then merging of both the strings have been given to us Okay so that is how we have mergeed both the strings together Okay now let's see another example in the string joiner how to set the empty value length and two string methods of string joiner class So for that we will go for a new Java class and we will have to start from the import of Java dot uil dot string joiner。



![](img/fa26a2e7d764e756452b84587ff71b0f_5.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_6.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_7.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_8.png)

Then create here public static void main width。String。Arguments and inside this。

 we will have to first create this string joiner saying my string is equal to new string joiner。

 and we are giving here a comma separated for a deal as a delimiter。 Okay， now after this。

 we are saying my string。

![](img/fa26a2e7d764e756452b84587ff71b0f_10.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_11.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_12.png)

Dot says set the empty value and here we are saying this is a default string。

 okay after which we say system do out print Elen， say default string。

 and we print the value of my string here， then we say。My string don't add。

 Let's add here some values in Apple。My string dot add， say。Banana。Then my string dot add。Say orange。

My string dot add， saykiwi and my string dot add。See。Graraps， after this， we gave system dot out do。



![](img/fa26a2e7d764e756452b84587ff71b0f_14.png)

Print Allen the value of my string to be printer。 Okay， now， once we have done this。

 we create invariable name length， which is equal to we give my string dot。



![](img/fa26a2e7d764e756452b84587ff71b0f_16.png)

Length views the method， and then we say system dot out dot。Separ print L。Giving length of the。

String joiner。And we here print the value of the length variable as such。

 then we take a string variable S which is equal to say my string dot convert to string and we say system dot out dot print L length the value of S Now let us see first we get the default string。

 then we have added the value so then after that if we print the value of string joiner it print the value which are added then the length of the string joiner is 31 all characters and if we convert it to string and then again try to print we again get the values print right So here we have seen certain methods also of the string joiner So with this we move on to the array parallel sort examples which is the last topic in our Java8 Now here in Java 8 we had a new method that is a parallel sort introduced which is in the array class of Java dot U package。

This particular method is introduced to support some parallel sorting of array elements a given array is divided into some subars and the sub arrays are further divided into their subars and this happens until the sub array reaches is a minimum granularity okay now after the subarrows are sorted individually by multiple threads then a parallel sort uses your for and join framework for sorting sub array parallel and then the sub sorted subars are mergech together so well see first example wherein well see sorting of primitive data types with the parallel sort So for that we will create here a new Java class and let's remove the comment part and here we'll have to import。



![](img/fa26a2e7d764e756452b84587ff71b0f_18.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_19.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_20.png)

Saing， Java dot。

![](img/fa26a2e7d764e756452b84587ff71b0f_22.png)

Uil dot。Aris， okay， and here we will be creating public。Static void mean。

 it takes string arguments as the parameter。 and inside this we create into numbers。

 which is an array we give here some values。

![](img/fa26a2e7d764e756452b84587ff71b0f_24.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_25.png)

In any order， it is not sorted as such now。 Okay， then we say。



![](img/fa26a2e7d764e756452b84587ff71b0f_27.png)

Aris dot we use here parallel sort example and here we give the values that is number。After which。

 we give。A a dot， stream， say number dot for each we use here n。



![](img/fa26a2e7d764e756452b84587ff71b0f_29.png)

And use system not out do print N class user space。And print it okay so if we try to execute。

 we get it parallel sorted and the values are being printed as the output。



![](img/fa26a2e7d764e756452b84587ff71b0f_31.png)

Now lets see another example wherein we lose parallel sort by specifying the start and the end index。



![](img/fa26a2e7d764e756452b84587ff71b0f_33.png)

Now， this was the default one that we have seen。 so let us create another file。

And let us import Java dot uil dot arrayris。

![](img/fa26a2e7d764e756452b84587ff71b0f_35.png)

And let's have a public static void main with。String。



![](img/fa26a2e7d764e756452b84587ff71b0f_37.png)

Arguments。And inside this， we are creating int numbers again wherein we are giving your values。Again。

 in any order， it is not sorted as such because we want to sort it and then we are using here。



![](img/fa26a2e7d764e756452b84587ff71b0f_39.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_40.png)

Saari start。Parael sort， and we give here numbers we also give from one to 5。 We want to sort it。

 Then we say array start stream in bracket numbers dot user for each loop。



![](img/fa26a2e7d764e756452b84587ff71b0f_42.png)

Use N and print it， using out print。And here we say n plus。A space。And then semico。

 so now here if you see the first one is notzz all because we have told it should be from1。

 so one means index 1， index 1 is the second element， so from the second element till this is0，1，2，3。

4，5 so from second you want to go till the fifth element okay so you are going to sort only the value of123 and 4。



![](img/fa26a2e7d764e756452b84587ff71b0f_44.png)

Till5， suppose you say here。

![](img/fa26a2e7d764e756452b84587ff71b0f_46.png)

Till 6。See here，6， okay。So now you get from one till all the elements are sorted。

 but if you specify here5， then in that case it will be sorted till4。

 so the first and the last element are remaining unsorted。



![](img/fa26a2e7d764e756452b84587ff71b0f_48.png)

Okay so in this way we can specify what elements you want to sort if you want to sort all。

 don't specify there the start and the end index just give there the am that you want to go as a parallel sort example so we'll continue more on such examples in the next session thats it from this session Thank you very much now let us see some examples on the new topics that are introduced in Java 9 out of Vi first is your private methods in the interfaces Now even we know that Java 8 allows us to create some default and static methods in the interfaces Now the intention was to have new methods added to interfaces without breaking the classes that already implemented those methods So Java 9 has introduced another new feature that is from Java 9 SC onwards we can have private methods in interfaces also so we'll see why Java 9 allows us to have private methods and interfaces。



![](img/fa26a2e7d764e756452b84587ff71b0f_50.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_51.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_52.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_53.png)

Basically have introduced private methods to remove the redundancy by sharing the common core of multiple default methods through the private methods Now to understand this。

 we have to take an example in Java 8 without private methods and then we will take the same example with Java 9 but using the private methods so here well see an example in Java 8。

 which is multiple default methods with duplicate code Now in this example we will see how default methods can have duplicate core which unnecessary increases the line of code and makes the code less readable so we can take the same example again using private methods to see how can private methods help us to avoid the duplicate core so the first thing is let us create a new Java class here。



![](img/fa26a2e7d764e756452b84587ff71b0f_55.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_56.png)

And。Let's remove the comment part。And here will first see and interface see my。Interface。P1。

 for example， and here we are creating default void。



![](img/fa26a2e7d764e756452b84587ff71b0f_58.png)

Sa method1。Whichch is having some。System dot out print， Allen。



![](img/fa26a2e7d764e756452b84587ff71b0f_60.png)

Say starting method。Then。System do out do print， Elen， say doing。Something。Again。

 system dot out dot print El， say。This is。Methodd 1。Okay， after which we have another default void。

 same method too。And here also， we are using system dot outer。Print， Elen， say。Starting。Mtterd。Then。

 system dot out dot。Print Elen。And here we see。Doing。



![](img/fa26a2e7d764e756452b84587ff71b0f_62.png)

Something。And then system dot out dot。Print Ellen， saying。This is。Methd2。



![](img/fa26a2e7d764e756452b84587ff71b0f_64.png)

Okay， now after these two default methods， we have a new class here that is。Implementing the。

My inter。And here， we are having public。

![](img/fa26a2e7d764e756452b84587ff71b0f_66.png)

Static void main with string。Arguments and inside this。

 we are creating the object of sinu class 26 as L1 is equal to new。See。Glass， 26。

And then we are saying here L1 dot， say method 1， and L1 dot， say method 2。

 and now if we see the output here， we are getting starting method doing something method1 again starting method doing something method 2 now this is using your Java 8。

 but now if we see another example wherein we will use some default method sharing the common code using them as a private methods okay。

 so then in that case we will create here another Java class and let us remove the comment part and again we will create here an interface。

 say my interpretpy 2 and inside this we are creating a default void。



![](img/fa26a2e7d764e756452b84587ff71b0f_68.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_69.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_70.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_71.png)

Same method one。

![](img/fa26a2e7d764e756452b84587ff71b0f_73.png)

Whi is saying。We are calling here separate lines。And then we are saying system dot out dot print。

 Elen， say this says。

![](img/fa26a2e7d764e756452b84587ff71b0f_75.png)

Methodd 1。Then we have another default void。Methtterd，2。Which here again， we are saying。



![](img/fa26a2e7d764e756452b84587ff71b0f_77.png)

We are calling print lines and then we are saying here system dot out dot。Print Ellen。

 say this is method 2。After this， we have here private void separate lines method。

 and in this method we are going to say system dot out do。Sa print L say。Starting。Methd。Then again。

 we say out out print。Ellen， saying doing。

![](img/fa26a2e7d764e756452b84587ff71b0f_79.png)

Something。These two lines have been printed and then in this class where we implement the my interpy 2。

 we have public static void main we create here string arguments。

 and here we create the object of new class 27， n2 is equal to new。



![](img/fa26a2e7d764e756452b84587ff71b0f_81.png)

Class 27， and then we say n2 dot Me 1 and N 2。Dot method2。 and now we execute。 So now again。

 we are getting the same output because the common line of code we have put inside a private method and we are calling those those private methods in this two default methods。

 which we are calling inside the main method So this is how we have seen a total difference。

 what was done in Java 8 and how it has improvised itself in Java 9 version。

 so now let's see another example in Java 9， which is introduced that is a private static methods。

 now till now we have learned how to use private methods and interfaces to share some common code of default methods。

 Now even Java 9 allows us to have some private static method in interfaces。 now since Java 8。

 we can have static method in interfaces along with the default methods also we cannot share the common code of static methods using nont private methods we must。



![](img/fa26a2e7d764e756452b84587ff71b0f_83.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_84.png)

Have to use private static methods to do that。 So now let's take an example to understand this。 now。

We'll start here with a new Java class， so let's add a Java class here and let us remove the comment part first。

 and then well have to create here an interface saying say my enter P3 for example。

 in which we will be first having。

![](img/fa26a2e7d764e756452b84587ff71b0f_86.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_87.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_88.png)

Static void method 1， okay， then here we are saying print lines we are calling here and then here we say system dot out dot print All。

 say this is。

![](img/fa26a2e7d764e756452b84587ff71b0f_90.png)

Methd 1。Then we have static word。Method 2， again here we are calling print lines。

 and we are saying system dot out dot。

![](img/fa26a2e7d764e756452b84587ff71b0f_92.png)

Print Ellen， saying。

![](img/fa26a2e7d764e756452b84587ff71b0f_94.png)

This is。Methodd 2。Okay， after this， we are calling here a private static void。



![](img/fa26a2e7d764e756452b84587ff71b0f_96.png)

Print lines and in this we are saying system do out or print element。Say starting。Metter。

Then system got out or print All saying doing。

![](img/fa26a2e7d764e756452b84587ff71b0f_98.png)

Something。Okay， after this we create here a default method。Said default word。



![](img/fa26a2e7d764e756452b84587ff71b0f_100.png)

My。Methods and inside this， we just call method1。And method2。 Okay。

 so now when we create here a class and we say here。Implements your my inter P3。

 and you have your public static void main width。

![](img/fa26a2e7d764e756452b84587ff71b0f_102.png)

Spring。Arguments inside this when we are creating the object of new class28 is equal to new new class 28。



![](img/fa26a2e7d764e756452b84587ff71b0f_104.png)

And when we say n3 dot， we call my methods here， it is going to call the default methods default methods are going to call the private static methods here Okay。

 that is how we can implement this in Java9 alright， so now。



![](img/fa26a2e7d764e756452b84587ff71b0f_106.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_107.png)

![](img/fa26a2e7d764e756452b84587ff71b0f_108.png)