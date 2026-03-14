# 【EDUCBA】应用现代Java特性编写简洁高效的代码 ｜ Apply Modern Java Features for Clean and Efficient p09 03_03_01_弦论中的新方法 -BV1twFSzNEZ3_p9-

Okay so now let's see in this session the new methods which are introduced in string now the various new methods added to string in Java 12 is the first is your string indent that basically adjusts the indentation of each line of this string based on the values past as a parameter and normalizes the line termination character next you have is the R transform which allows the application of a function to this particular string then the following methods are also related to your JVM constant API you also have there some describe constantstable which returns an optional containing the nominal descriptor for this instance and you have to resolve constant DSC which resolves the instance of the constant or the description the result of which is the instance itself Now let's see an example on this string indent method that we have so let us add a new Java。



![](img/0645e02e139bb4dfb6a1e45cb4779982_1.png)

Class and we would need to remove the comment part and we will first go for say public static void mean。

 which will take string。Arguments and in this method， we would be creating a string variable。

 which we are giving the value as say life is too short to work。😊，So， hard。Okay。

 then let's give here system dot out dot print Ellen， let's print the value of S。Let's go for。

System dot out dot。Print Ellen。Say string length and we'll say S start length。

And then well give string s indent is equal to S dot， we give your indent， let's give a value as 5。

 and then well give system dot out print LN， say a slash and first and we give indented。

 then we'll print system dot out print L the value of s indent。



![](img/0645e02e139bb4dfb6a1e45cb4779982_3.png)

After we print this value in the print LN statement then let us give here system dot out dot print L will give s string length and will give s indent dot length and now let us execute this the first your length is 33 okay then you have intended it 5 so by default you have the5 spaces so five characters would have been increased so after that when you see the length it becomes 39。

Okay， so with this we have seen the value how it has inserted spacing into the given values。

 Similarlyly lets see a string in that is your multiline string in okay so now in this case what well do is lets create another new Java class and unlike this we will now there is no need for importing anything directly what well do is in this particular class will first create a static int sec count care method which will take a string。



![](img/0645e02e139bb4dfb6a1e45cb4779982_5.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_6.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_7.png)

S and a character C variable。Then we are saying int C and T is equal to 0。



![](img/0645e02e139bb4dfb6a1e45cb4779982_9.png)

Then we run a4 loop for and I equals to 0。 I is less than your S dot。Lth。And say， I plus plus。

Then we say if S dot sec care at I， and that is equal to C， then we are making your CNt plus。

 then this method， this for loopbe gets closed after which we are saying return the value of CNt semicole close this particular method。

 then we have public。

![](img/0645e02e139bb4dfb6a1e45cb4779982_11.png)

Static void main， which take this string arguments and inside this again。

 we have a string s we say your life is short。

![](img/0645e02e139bb4dfb6a1e45cb4779982_13.png)

Comma， we give slash， and we says so。I'm。Sa no。Exactly， where。I am putting my time full stop。 Again。

 we gave a slash and say， I don't。Want to， do。Ts， let's come on a new line。

 say that I don't have to do。With this we close it and we give a semicoin here。

 and then we say system dot out dot， print Allen， we print the value of s first and then we will print the value of s and we count we we call the count car method also。

 so here we will say system dot out dot print All first say string length colon and here we will say。

Etor L。And after this。System， not outdo。Print Ellen， let's give here。N double quotes， slash n。

 say count colon， and well call here， say count CAs pass s and now we give here in single code。

 slash n， that is what we want to count now after this we give another string， say S indent。

 we give here S dot indent and will give 5 as the length。

 then well print out print L saying slash n indent it。



![](img/0645e02e139bb4dfb6a1e45cb4779982_15.png)

Okay， and then。System dot out dot print L， say lets print the value of S indent。



![](img/0645e02e139bb4dfb6a1e45cb4779982_17.png)

After which we will say system dot Out dot print Ln here we again print string length。

And we now say the value of S indent dot length。To be printed and then we'll say out print L now we'll say slash n count colon and we'll again call the variable or the method but this time we pass S in then and we pass now in single code slash n okay now lets see well execute this now in the first one you are getting the total new lines are2 length is this much。

 then here again we have it on a new line and now we get there the the count of slash n is 3 and the length becomes 131。



![](img/0645e02e139bb4dfb6a1e45cb4779982_19.png)

Okay， so now here we will also try one more thing。 Now。

 what we'll do is let us copy down the same thing。

![](img/0645e02e139bb4dfb6a1e45cb4779982_21.png)

Here we will only change the variables in this case because we will not use the same ones。

Okay so let's use here all the different variables and what are you going to do is instead of giving you a positive value for indent we will give you a negative value for indent and lets check here say for the count of a space okay similarly here also a space okay now lets try and execute this so in this case you see you are decrementing the spaces here。



![](img/0645e02e139bb4dfb6a1e45cb4779982_23.png)

if you give there a negative or a negative value in the indent method， right similarly。

 if you try to give here a value that is say0。

![](img/0645e02e139bb4dfb6a1e45cb4779982_25.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_26.png)

Okay， now。Let's do one more thing， let's change here all to S2。😔，And。Let's give your。

Will not use this count method in this case and here also will use S2 dot indent。

 but will give here 0。Will print intended revalue of S2 and the length of S2。Okay。

So again this is not required lets see after executing see the last time intended and then we get the length of the string becomes 116。

 so that is the basic use of your in now lets see another that is your transform function so this basically method fields the provided function with a particular string instance as an input and returns output returned by that particular function so now for this let us add another Java class here and in this we will first create a public static void main with string。



![](img/0645e02e139bb4dfb6a1e45cb4779982_28.png)

Arguments， and in this will create stringestt， say life's too short。



![](img/0645e02e139bb4dfb6a1e45cb4779982_30.png)

As a string will create here aware result， which is equal to say SR dot transform we will use。

 Now here we give input。

![](img/0645e02e139bb4dfb6a1e45cb4779982_32.png)

See。Input dot cond， say，2。Eat。Say bad fool。Then we use here dot。Transform， says string。

 double colon2。A bookcase。

![](img/0645e02e139bb4dfb6a1e45cb4779982_34.png)

Then， dot。Transform， say string。Double colon2。Ca A， and here will say outdot print Ellen。See， Adds。

Dot。Okay， now for this， you will have to import this Java or u dot aries and now if you try to execute。

 you will get the text that you have written with this you have concatenated this text and this all will come as a separate separate character as into an arrayri format。

That is what we are basically transforming your string into okay similarly we will see another example where we will use the describe constable method which is there into the strings which is created okay so now for using that we will create a new Java class and lets。



![](img/0645e02e139bb4dfb6a1e45cb4779982_36.png)

Go for the first import that is Java dot， U dot optional。



![](img/0645e02e139bb4dfb6a1e45cb4779982_38.png)

Okay， and inside this class， we will create public static void main。

And will give here string arguments。 Then will create string SR that is will give say life is。



![](img/0645e02e139bb4dfb6a1e45cb4779982_40.png)

Short and。We should。Respect every。Moment of it。Semicolon then will create here。

 say optional here will give string。Okay， say OT STR， which is equal to STR dot。

 say describe constable method， and then well use OT SR dot if。

Present and then we'll give your a value。

![](img/0645e02e139bb4dfb6a1e45cb4779982_42.png)

In saycho brackets will give here。System dot out dot print L， say value that will win double quotes。

Then。Well use your OPT STR dot get method。Okay， and。With this， we will close the method here。

 And now if we try to execute， we get the value as life is short。

 and we should respect every moment of it。 Now， this method returns an optional containing the nominal descriptor for the instance。

 now， which is the instance itself。

![](img/0645e02e139bb4dfb6a1e45cb4779982_44.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_45.png)

Now similarly we have another that is the resolve constant description method okay so now this method basically we will see how to use this and what is the output we are getting so lets add a new Java class in this case and here well go for creating public static void main say string。



![](img/0645e02e139bb4dfb6a1e45cb4779982_47.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_48.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_49.png)

Arguments， and then will create here S1 as say life is short， and it is here to be。Lift。

Let's close this， Then we'll create another string。s S2， which is equal to we give here S1 dot。

 say resolve the constant and we'll give here null value initially then we'll try to use system dot Out print Ln S2 dot equals say S1 and system dot Out print Ln S2 equals S1 now lets see the value so both the values are coming to true in this case okay it basically comes from the method resolve constant description which marks the loadable constant value in this case which is a string itself so with this we have done the new methods introduced in string class now the last and this is we will see a new switch arrow form which is introduced in Java to L which will basically help you to override the original or the earlier the way we use。

down the switch cases， you can overwride the whole sequence and you can use another new way of writing the switch case。

 so now what we'll do is we'll see an example on that。

 so let's create a new Java class here and let's remove the comment part here now here we will first create public static void main with string。



![](img/0645e02e139bb4dfb6a1e45cb4779982_51.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_52.png)

Arguments， okay， and in this。We will first create here now we are going to have a method here which we would be creating。

 so let's first create that method that is public。Static void get grade。

 which will take a character variable grade for that and inside this method we are going to write down some sequences。

 but now for this we will first call here get grade we pass here a as a value similarly the next value will pass says C。



![](img/0645e02e139bb4dfb6a1e45cb4779982_54.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_55.png)

Next value will pass say B， say E， and。Last， say X。 okay， and now what are we going to do here。

 is we are going to use here。

![](img/0645e02e139bb4dfb6a1e45cb4779982_57.png)

。A switch case for grade and in this switch case we would be using case a， the arrow operator。

 and here we print system dot out dot。Print Ln。And we'll give here。Saying excellent。



![](img/0645e02e139bb4dfb6a1e45cb4779982_59.png)

Similarly， we will say。If it is not a， you will check if it is equal to。B。😡。

Then we'll print here the value good。Then， for third one will give here。Say standard。

 and this will be C。Then well give say low and this will be say D。

 okay after which we will give here say very low and here we'll use E。Then we'll use here。

 say default， and here well give system dot out dot print L say。Inval。

 anything apart from that you get that is invalid。 Okay， and after this， we say here， get。Result。

 and we pass their grade as the parameter。 We end this method here。

 And here we have another public static void， get。

![](img/0645e02e139bb4dfb6a1e45cb4779982_61.png)

Result wherein we are passing the character grade as the parameter。

 and here again we are using switch for grade。Wem going to put here。

Now here we are getting the value error for this switch case。We are printing。

 opening the bracket here， checking if it is case a， then system not output print Ln。Yeah。

So then in this switch we are going to say another option in which we can do is save it this case a。

Bc。Im going to say here， say system dot out dot。Trint Ellen， saying。Double quotes say。

Success and case the。OrE。We are going to see here。System dot， out dot print L。Say your double colon。

 fail and。Default。Well say system dot out dot print L， say no。Result。Okay。😊。

Let's save it and let's try to execute this。

![](img/0645e02e139bb4dfb6a1e45cb4779982_63.png)

It is a gama。B， comma， C， all in single quotation marks that is correct。

 Then we use system dot out dot print Ellen。 and here we give success Similarlyly here。

 it is also this way。

![](img/0645e02e139bb4dfb6a1e45cb4779982_65.png)

Let's check it again。 No， again， some issues in this case。



![](img/0645e02e139bb4dfb6a1e45cb4779982_67.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_68.png)

Okay， so here if we try to execute， run anyways， you will get here the values。

 if it is a that we have passed it comes here excellent， then again here we call the result。

 it checks if it is a it concates with that success Similarlyly we have passed the next value as C that comes to standard and again gets your success then we pass here another value which is D that comes to low and if it is low we say it is feel Similarlyly E comes in very low again it gives you the result here as feel。

 and if it is anything apart from the given value that is a default one。

 it gives you invalid and says here in default no result that's how we have basically concateated the two things and with a more advanced feature used for a switch case which was not used in earlier to Java to L versions right so with this we have seen how to use all the new enhanced features available in Java。



![](img/0645e02e139bb4dfb6a1e45cb4779982_70.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_71.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_72.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_73.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_74.png)

![](img/0645e02e139bb4dfb6a1e45cb4779982_75.png)

12，8，9 versions that we have covered in this particular sessions。 That's it from this session。

 Thank you very much。😊。

![](img/0645e02e139bb4dfb6a1e45cb4779982_77.png)