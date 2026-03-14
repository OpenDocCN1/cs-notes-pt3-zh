# 【EDUCBA】应用现代Java特性编写简洁高效的代码 ｜ Apply Modern Java Features for Clean and Efficient p04 02_01_01_蒸汽收集器类别 -BV1twFSzNEZ3_p4-

![](img/824b9a4e3845cecdad3fbce1316edf44_0.png)

So now let's see another part in Java here that is your stream collector classes Now this collector is basically a final class that extends the object classes okay so we'll see some more examples on Java stream collectors here we'll see an example for stream collectors grouping by and counting example okay so we'll be using the grouping the element of a list using grouping by method of a collectors's class and printing the occurrences of each element in the given list So for that we will have to create a new Java class and we's go for first import statements wherein the first import we'll have to use is Java do u dot Ar then import Java dot。



![](img/824b9a4e3845cecdad3fbce1316edf44_2.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_3.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_4.png)

Uutil dot list。Import Java dotut dot map。Then， Java dot u dot。

Function dot function and import Java dot U dot stream dot collectors。 And then in this class。

 we will have。Public static， void main。String。Arguments。Wherein we are creating list of type string。

 say names is equal to a is dot as list， and we give here some values。And。Tor， so let's add one more。



![](img/824b9a4e3845cecdad3fbce1316edf44_6.png)

We are adding again similar values but the order is different okay and then we are saying map width string and long。

As object is equal to name dot， stream dot。

![](img/824b9a4e3845cecdad3fbce1316edf44_8.png)

Collect。Using。

![](img/824b9a4e3845cecdad3fbce1316edf44_10.png)

Collectors。Dot use the grouping by， and here we are passing the。Function。Say identity。关芒。

We are passing the。Collector start。Couning。Okay， and end it with a semicolon， after which。

You say here， system dot out dot， print Alllen。P in the value of map。

So now if we try to execute to get Steve is one， John comes two times Aji comes three times。

 that is how we have used here grouping operation Similarlyly。

 let us see another example for Java stream collectors of fetching data as a list type。

 so let's create a new Java class and。

![](img/824b9a4e3845cecdad3fbce1316edf44_12.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_13.png)

Let's import。Sva dot uil dot， stream dot。Collectors。Java dot， u dot。😔。



![](img/824b9a4e3845cecdad3fbce1316edf44_15.png)

Audice。安java dot。You till do。List now we'll take here a list instead stuff of Ar Okay。

 now the first thing is we'll create here a class named student。



![](img/824b9a4e3845cecdad3fbce1316edf44_17.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_18.png)

Okay。And in this class， we are creating string name。 Okay， first， let's take an I， So int I。

 then string name。Then， we'll take end age。And here we create public student as a constructor and ID comma。



![](img/824b9a4e3845cecdad3fbce1316edf44_20.png)

String name comma int H。 And here we are saying this do I D。Is equal to ID。

This dot name is equal to name。 This dot H is equal to H close this class here。 Then in this class。

 we create public。

![](img/824b9a4e3845cecdad3fbce1316edf44_22.png)

Static void main。String。Arguments。And in this main method， we create list of type。



![](img/824b9a4e3845cecdad3fbce1316edf44_24.png)

Student。As a student。List。Is equal to new。Alist。Of type student okay， and then。We'll say here。

Student list dot I say here new。Student will pass here IDd。Name each。Similarly。

 student lists start add new student， say 22。Steve。H， similarly， student list taught add。



![](img/824b9a4e3845cecdad3fbce1316edf44_26.png)

New student， said 33， Lucy。22。Then， we'll add here two more。Say student let's start add。New student。

44。Sana。And say 23。

![](img/824b9a4e3845cecdad3fbce1316edf44_28.png)

And。Student list start a。Saing new。Student 55。Maggie and say 80。



![](img/824b9a4e3845cecdad3fbce1316edf44_30.png)

Okay， now after this， we'll say list of type string。And here will give。Names is equal to。

 say student list dot。哦。Stream， and then we use here， dot map。N as N dot。Name。And do。Collect， say。



![](img/824b9a4e3845cecdad3fbce1316edf44_32.png)

Collector， start。To list， end it with the semicolon and then use system dot out dot print Elen。



![](img/824b9a4e3845cecdad3fbce1316edf44_34.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_35.png)

Names so now well get only the names being collected out of the given set of data Now let's see another example where we will be converting the list of students to a string and then we are applying this stream filters to get the selected records from the given string object okay so now in the same one we will continue okay as here we are having object collectors we have IRA list we have the list we also import here say Java dot uil dot set and in the class student we have ID we have name H this all remains same inside the class we have the main method wherein we create student list and we also add the values in that then we say instead of this list part okay then here we create set of say student。



![](img/824b9a4e3845cecdad3fbce1316edf44_37.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_38.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_39.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_40.png)

As students is equal to， we say student list dot。Stream。And then here well again use the filter。

 saying N。N dot I more than 22 and dot。

![](img/824b9a4e3845cecdad3fbce1316edf44_42.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_43.png)

Collect as。Say collector start to set now okay and after that， we use a for saying student S to U in。

Students and here value systemem dot out dot print Llen， say Stuu。 I。Then give us space， S to U dot。

Name， give a space and SD。 H。

![](img/824b9a4e3845cecdad3fbce1316edf44_45.png)

Okay， so with this， let us execute this and get the output。

 so here in the second one you get all the values ID， name and H printed。



![](img/824b9a4e3845cecdad3fbce1316edf44_47.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_48.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_49.png)

So now let's see another example of a Java collector where we'll getting the average age of student using the Averaging end method。

 so now let us create a new Java class。

![](img/824b9a4e3845cecdad3fbce1316edf44_51.png)

And。Let's remove the comment part Now here we'll have to import Java dot uil dot stream dot。

Collectors and Java dot U dot list。😔，Then Java dot， util dot。



![](img/824b9a4e3845cecdad3fbce1316edf44_53.png)

A list。 And then again， well be having a class。Student1。Now here well be again having the ID。

 then S string name。😔。

![](img/824b9a4e3845cecdad3fbce1316edf44_55.png)

And then say end age， then well have public。Student1， which will again take ID。

 then string name and in the age， and in this we would be assigning ID is equal to ID。



![](img/824b9a4e3845cecdad3fbce1316edf44_57.png)

This start name is equal to name， this start age is equal to H。And after this。

 then we close the class。 go to the existing class， create here public。



![](img/824b9a4e3845cecdad3fbce1316edf44_59.png)

Static void mean width。String arguments and inside this we again create the list of student seeing student list。

 Now this is student1。Okay， student list is equal to new。Ary list。Student1。After which。

 we create the。Student list dot add send new。Student one and again， give here some values。With each。

Similarly。Let's add some more values here。 Let's take 1213，14 and 15。Say Steve。し口。Say， pretty。

Shuutta， and let's give you some average age。 So we'll take here some damagems。😔。



![](img/824b9a4e3845cecdad3fbce1316edf44_61.png)

Okay， and。Say 90 okay， and now。

![](img/824b9a4e3845cecdad3fbce1316edf44_63.png)

To get their average age willll create here say a double variable。Seeing A VE。Or AVGH。

 which is equal to your student list dot。

![](img/824b9a4e3845cecdad3fbce1316edf44_65.png)

Stream。And here well use dot collect method using the collector dot using averaging int and here we use S。

 which is S dot H， then we say here system。The out print A， say the。Average age of。

Student is and you print here the value of AvG H let's save this and execute the average age comes to 20。

4 in this case okay using the method of the collector class that is averaging int so we'll continue more on such examples but in the next session that's it from this session Thank you very much So now we'll see about some examples on string joiners now in Java 8 a new class that is a string joiner was introduced it was in Java dot u package okay so using this class we can join more than one string with this specified delimiter we can also provide a prefix or a suffix to a final string while joining some multiple strings okay so we'll see some several examples of string joiner classes and we'll also see some methods of string joiner classes so let's。



![](img/824b9a4e3845cecdad3fbce1316edf44_67.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_68.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_69.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_70.png)

The first example in string joiner wherein will join the strings by some specifying delimiter。

 so in this particular example， we will be concatenating multiple strings using string joiner and while creating the instance of the string joiner。

 we will specify the delimiter as a hyphen sign Okay。

 so for that the first thing we will do is well create a new Java class。



![](img/824b9a4e3845cecdad3fbce1316edf44_72.png)

And in this， we will first create need to import the package。

 so well first say import Java dot uil dot string。Joiner and once we have imported this package。

 then we'll create。The main method inside the class。So we'll say here public。Says static void main。

 which takes string arguments as the parameter， and inside this main method。

 we will first create object saying string joiner say my string is equal to new string。

Joiner and we'll pass here a hyphen as a string joiner。 Then we'll say my string dot add。

 Let's give you some parameter。 say loggan again， my string dot add。先买给你多。Then my string dot add。

 say wrote。Then my string dot add。Say strong okay， and then we'll say system dot out print Elen the value of my string Okay so now here let us execute this and check the output So whatever parameters we have passed they all will be joined together with the given delimiter that is a hyphen sign okay。

 that is what the output is now let us see another example wherein we'll see adding a prefix and a suffix to the given output string so again let us create here a new Java class and unlike the earlier program will have to import Java dot uil dot string joiner after which will create public。



![](img/824b9a4e3845cecdad3fbce1316edf44_74.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_75.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_76.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_77.png)

Static。Vide mean taking string arguments as the parameters。 and here we are seeing。String joiner。

 say my string is equal to new string joiner。 And now we are going to pass here， say a comma。

 Then we are going to pass here。A bracket， a comma again closing bracket and close this。

 so here we have given two parameters Okay， so if you pass a comma as a delimit and an opening bracket。

 it means it is as a prefix and a closing bracket as a suffix okay so then in this case。

 if we are saying say my string dot add again， let's add some value here。



![](img/824b9a4e3845cecdad3fbce1316edf44_79.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_80.png)

Again， my string dot add， say Ricky。My string。Dot and。是无限。And my string。Dot and。Sa， bracket。

Fourth name。 and then after which we try to。Print the value of out print L。



![](img/824b9a4e3845cecdad3fbce1316edf44_82.png)

Myice string， okay。And let us try to execute it now here you can see you have a bracket opening in a closing bracket and in between that it is separated by comma separated values right now let's see another example of a string joiner wherein will be merging the two string joiner objects together so currently we were working on only one string joiner object so let us create a new Java class and let's start with the importing of the u package dot string joiner。



![](img/824b9a4e3845cecdad3fbce1316edf44_84.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_85.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_86.png)

![](img/824b9a4e3845cecdad3fbce1316edf44_87.png)

And then let's create public static void Ma。String。Say arguments。As the bracket and then inside this。

 we are going to create the first string joiner as my string。

 which is equal to the new string joiner and here we are going to pass a comma then。Opening bracket。

 comma and closing bracket。

![](img/824b9a4e3845cecdad3fbce1316edf44_89.png)

Okay， after this， we are going to save my string dot add again， let's pass there some names。

 my string dot add。

![](img/824b9a4e3845cecdad3fbce1316edf44_91.png)

Let's pass my string dot ad and one more。😔，See my string。Dot add。Okay。

 now after passing some four names， we'll first say system dot out print Ellen。

 saying here first string and we print here the value of my string。 Then we are creating another。

String joiner saying my another string is equal to new string joiner。 Now。

 here we are passing a hyphen， then a p and。

![](img/824b9a4e3845cecdad3fbce1316edf44_93.png)

Suffix So S UFF， after which we are saying。My another string dot add。 Let's add here。

 also some values。

![](img/824b9a4e3845cecdad3fbce1316edf44_95.png)

Myy another string dot a。Say IMP。Myy another string dot a。See John。



![](img/824b9a4e3845cecdad3fbce1316edf44_97.png)

And by another string dot add。Say Ned， then we'll say here。



![](img/824b9a4e3845cecdad3fbce1316edf44_99.png)

System dot out dot print Allen， saying second string。

And we print here the value of my another spring。

![](img/824b9a4e3845cecdad3fbce1316edf44_101.png)