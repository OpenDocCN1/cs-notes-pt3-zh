# 【EDUCBA】应用现代Java特性编写简洁高效的代码 ｜ Apply Modern Java Features for Clean and Efficient p08 03_02_01_Java 12中的紧凑数字格式 -BV1twFSzNEZ3_p8-

Okay， so now let's understand the new concept introduced in Java 12。

 That is your compact number format。 Now this is basically a subclass of number format that formats a decimal number in a compact form Now number format is an abstract base class for all the number formats which provides the interface for formatting and passing your numbers。

 So number format also provides methods for determining which locals have number formats and what their names are Now an example of a short compact form would be writing say 10000 as 10 only requiring three instant of five characters So number format and the Java dot text spi do number format providers have been extended to include a new method that is get compact number instance Now we will see an example of number format example or the compact number format example in this case So let us create。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_1.png)

A new Java class， and。We would add it in this package itself， so after adding the Java class。

 we will have to write down the import， say Java dot text dot。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_3.png)

Number format， okay， and then we'll have to import。Java dot uil dot say local。

 and now well have a class created in which we would have public static void mean， which takes。

String arguments as the parameter， and into this we create object of number format say Nf is equal to。

Number format dot saying get the compact number instance， and here we are going to pass say。

Local dot， let's take it off US and then we take the number format dot style as shot。Okay。

 now after this， we say system dot out dot print Ellen， we use here printing。

 say number format dot style dot shot。And then we say system dot out do。Print LN， we give here。

 say result colon， and here we say Nf dot， use the format and we give here value as 10。

000 to be printer then we say system dot out dot， say print L again we say result colon and here we write down Nf dot format and this time we give the value in bracket。

 say 120300。Then。We see again。Outdo。Print Ellen， and here we give result。

CoL and this time we give Nf dot format in bracket C 212。Double zero， double zero then。

Say system dot out dot。Print L。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_5.png)

Result and here we write down NF dot format， say1，9，5， double 0， double 0，300。Okay， and now。Okay。

 now this error is coming here because we have not done Java dot u dot local。Okay， so after this。

 then let's create again Nf is equal to saying say number。Formatt， get the compact number instance。

 and here we again use say local dot， say US and we again use say number。

Format dot style dot Now we used long earlier we had used shot Now we used long style。

 and then again well write down system dot out dot。Say print Ln， writing number， format dot。

 style dot long， okay and then again well use all the same values above so we'll use here first print Ln saying say result colon and we'll use Nf dot format in bracket 10000。

Then。System dot out dot print Ellen。Result and。Well use your Nf dot format in bracket。And then again。

Print Ln result。Nf dot format。Then。Out thought。Print Ellen。NF dot format。

 say 195 double0 double0300 Okay so let us see in both the ways how the output comes now let us save it and let us execute this to check the output you get it first as say 10 k because it is short120 k2 m2 B when you use a long one it is 1000120000 or 2 or 2 billion that is how the result are basically coming right so now let us see another example okay can also specify some desired locals for our compact number format and it is the easiest to understand with the help of some example that we will see okay so now let us create again a new Java class first so let's add a Java class in this。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_7.png)

Wherein we would be first having to import。The package that is import Java dot， say text dot。

Number format and import。Java dot， Uil dot local， after which， in the class。

 we are first creating the constructor of the class by saying， say private。Static void。

 And here no views another method here， saying say print。Compact number format local。

 which takes a long variable number。And inside this， we create the object of number formats， Nf。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_9.png)

Default is equal to saying number format dot， get the compact number instance。

And then we create another， say。Number format object as a Nf US long， which is equal to again。

Number format dot get the number compact number format instance。

 but now here the instance will be for。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_11.png)

US， and it is。Using long。So after another object created we say here again。

 say number format now we use NF R and we use short now F is we have used it as a short form for France okay which is equal to we give here。

Number format dot get the compact number instance。 Now this is， we are going to write down of。

Say France， and then we want shot， though shot would be。

No issues this is as it is only we have to end it with a semicolon here， okay。

 now after the France shot we would be creating another object number format saying say NFFR now will take long。

 which is equal to again say number format。Dot get the compact number instance， and this is。Again。

 France。 and now this time it is not short but long。Ended with a semicolon。 Similarlyly。

 we would be using for China short and China long。 So now we would be creating。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_13.png)

Another object NF will use for China， say CH and short。Which is equal to say。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_15.png)

Number format， dot get the number compact instance。 and this time it is for。China and this is short。

 so no changes。 Now the next one we would take that is for NFC H long。

 which is equal to number format dot get the compact number instance， sorry。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_17.png)

![](img/ee09b2c2e51f74aee8e63de8e19cacca_18.png)

And。G back number。Instance， and here we would be using say local dot China。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_20.png)

And then we would be using the number format dot。Style dot long or this time。 Okay。

 so we have taken for basically one is for the default one and the rest are we have created a specific local and specific number for math style。

 So now we start with the first system dot out dot print All and we use here， say compact。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_22.png)

![](img/ee09b2c2e51f74aee8e63de8e19cacca_23.png)

你能不。Foratting4 and we print here first value of number give colon okay。

 and then we start here saying system dot out dot print Ellen。

 say default would be how so we are printing here using Nf default dot format and we pass that number similarly。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_25.png)

Saying out thought。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_27.png)

Print Ellen， how it would be for US long。 So here we are using Nf。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_29.png)

US long dot format number。Similarly， we are checking it how it would be for a far shot。And for that。

 we are using a far short dot format and number。Similarly。

 we use here print Ln for FR long how it would be， so this time we use FR long dot format number。

Similarly， we'll check it。For how it would be for China short and for that。

 we would be using China short dot。Format number and the last one， we will check it if it is。China。

 long， and now it will be C H long dot。Format number。Okay。

 so after we have printed for all the values， we end the method here， and then we have the public。

Static void main， which takes this string。Arguments， and in this， we call。Oh， sorry。We'll have to。

Place this here， okay。F， so inside this we call the print compact number and this time we pass some value in the bracket similarly again。

 we call the same method， we pass some different value here。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_31.png)

So let us pass here， say 23450000 and again we try to call the same method and we pass here1，2。

3 double 0 double0，3 times 0 okay so now we will try to execute this and check how the output is coming you can see for everywhere the default one is 346 k 346000 if it is France if it is France long it is this China short China long。

 similarly formatting number formatting for a particular number。

 how it would be in all the6 given number format exception a number format that we have taken and you would be able to see the output proper right。

Okay， now well see another example to get all the locals available Okay。

 using the instance method of the number format。 So for that now let us create a new Java class and。

We would first have to import。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_33.png)

Saying say Java dot uil dot star。And import Java。tex dot star and then in this class we'll create public static void main with string arguments and here we would be creating object local say list which is equal to we use date format dot get the available locals and then we use a4 loop saying local object a local in list。

 and here we will say system dot out dot print L， say a local。Dot two string。Okay。

 so now let us try to execute this and we'll get all this available formats for date format now similarly if you want to use something same number format。

 so let's create here another， say local list one， which is equal to。Your number format dot。

 get the available locals and here we write down for local B local。In your list one。Okay。

 here you are seeing system dot out dot print Ln the value of。Be open。Okay。

So now you would get there all the available formats for number formats also。

 so if you wish to you can segregate by just putting here one more line， system dot out print LN say。

Number， format。Locals。And similarly。We will put here。See。Date format locals， Okay。

 so these all are your number format locals， if you wish to see。Many you are having it。Similarly。

 you would be having the date format also， so these all are your number formats same way you will be having your date formats。

 same option， no differences Okay， so we will continue more on this number formats。

 but in the next session that's it from this session Thank you very much。

 So now we will continue with some number formats wherein we willll see some fraction digits also。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_35.png)

Okay， now you have some method that is says set the maximum fraction digit and set the minimum fraction digit。

 Now in the maximum fraction digit， you can set the maximum number of digits allowed in a fraction portion of a number and it must be more than my minimum fraction digits Similarlyly in the method set minimum fraction digit。

 you can set the minimum number of digits allowed in the fraction portion of a number and that minimum fraction digit must be less than the maximum fraction digit。

 Okay， so we will see an example on this。 So let us add a new Java class here。

 and the first thing is we will have to go for the import part。 So let us。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_37.png)

Right down here， input， say Java dot。Text dot first number format。

 and after this we will import the U dot local package also。And once we import the package。

 let's add a semicolon， we say import Java dot u dot local。 and now inside this class。

 we will take public。Static void main will take string。Arguments。

 and here we will first create the object of say。Number format。

As N F is equal to saying number format dot get the compact number instance。

 and here we will set the。Local to US and format style would be shot。 After this。

 we will say system dot out do print Llen。 We will print here， say。Minimum。

And we will print the value of Nf dot get。Minimum fraction digit。Okay。

 and then we will say here out do print Elen， say。Maximum。

And we will say Nf dot get the maximum fraction digit after that we will end it with the semicolon。

 then we will say system dot out dot print L now here we will first use a slash n， say here result。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_39.png)

Call in and will print your NF dot format will give here 3，4，5，4。And again， system dot out dot。

Print Elen， let's give here。Result and Nf dot。Format and well give your say 5156835 something a bigger number okay now after this we will again set here using Nf dot。

 set the maximum fraction digit and well set it here to1 and then well say again system dot out dot print El。

 say slash n and again well print the result。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_41.png)

Call in and will print your NF dot format， say will again give your 1，2，3。

454 to be printed and will check again out dot。Print El， say result。And we'll see here Nf dot format。

 say 5156835 and then we will set here Nf dot， set the maximum fraction digit now to say2。

 and after setting it22， we will again print system dot out dot print L， say slash n。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_43.png)

Result and Nf dot format。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_45.png)

Okay， similarly。Print a。Result。And any thought format again。5，6，8，3，5。Okay。

 and then we will set here the。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_47.png)

Minimum fraction digit and that we are setting it to2 now and will set Nf dots set the maximum fraction digit also to2 and then well try to print。

Again， the slash n say result。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_49.png)

Coin and NF thought。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_51.png)

Format 1，2，3。454 and out dot print L。See result and NF dot format5156835。 Okay。

 now let us check here the output we would execute this。

And lets view the output The first one we are only printing the minimum and the maximum fraction digit so that is initially equal to 00 both。

 So when we are printing the values we are getting here 1235 and then we set the fraction digit to 1 so then we are getting 123。

5 okay because then it is dividing it into the given fraction digit similarly here 5。

2 we are getting it then we set it the fraction digit to 2 so when we set it to 2 we get here both2 and when we set the minimum also a maximum also to 2 we get again the similar value here so initially when you have not assigned any minimum maximum fraction digit by default it is equal to 0。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_53.png)

So now let us move around the next one in this that is your number formats rounding now by default rounding mode that is half even is used okay。

 we can set the rounding mode by calling the set rounding mode method which is available so in set rounding mode the parameter taken as rounding mode which sets the rounding mode used in this particular number format so now let us see an example on this rounding mode method so let us create a new Java class and unlike others we will first go for import Java dot math dot rounding mode now and well say import Java dot text dot number format and import。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_55.png)

![](img/ee09b2c2e51f74aee8e63de8e19cacca_56.png)

![](img/ee09b2c2e51f74aee8e63de8e19cacca_57.png)

![](img/ee09b2c2e51f74aee8e63de8e19cacca_58.png)

Java dot u dot local Okay， and then in the class we will first create。Public static。

 void main string arguments and then。

![](img/ee09b2c2e51f74aee8e63de8e19cacca_60.png)

We create here， say number format match Nf is equal to saying number format dot get the compact number instance and again here we want to get it for US and that is in short style。

 then we are first printing。System dot out dot print L， we are giving here。

 say a slash n saying result。Call in and we are printing your NF dot format。

 let's give here a number to be formatted， Similarlyly out dot print El。

 we say result and NF dot format。Six， eight，3，5。Okay， now after this。

 we are going to set here the minimum and the maximum fraction digits。

 So well first set the minimum fraction digit to2 and will set the。Maximum fraction digit， sorry。

 not the integer length， but N F dot set the maximum fraction digit to 2 and。NF dot said the。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_62.png)

Minimum fraction digit also22 and after setting both， lets print this again。Okay。

 with the same values and now we will set Nf dot says set the rounding mode and we give here rounding mode dot we give use here。

 say up okay， and then we will again print both the system dot Out printer and then we will set the。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_64.png)

Minimum fraction digit to1 will also set the。Maximum fraction digit to one。 And again。

 we will print the same values。 And now we will say， said the。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_66.png)

Rounding mode and now we give the rounding mode to down and again。

 we will print the same format here。 Okay， let us save and try to execute and see the output see。

 that is how we are getting the values without any rounding digit with two digits。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_68.png)

Then rounding method with two digits。 So here we are saying rounding it is making46 in this case Similarlyly when you make it one and you try to round it off。

 it makes5 because466 is more than5 so it by default makes it to5 here when you go for down it is making it till4 not one up but one down to that is what the rounding mode is basically applying for so let us continue with another method we have that is the par method Now basically this par method it takes from the beginning of the given string to produce a particular number so basically we are passing some string into number that is your basically a par method for returning a number from the given text so let us see one example on that so well create here a new Java class and let us import here first Java dot text dot number。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_70.png)

![](img/ee09b2c2e51f74aee8e63de8e19cacca_71.png)

Comat import Java dot text dot par exception in this case， okay， similarly。

 import Java dot uil dot local and then in the class we will have public static void main string arguments and inside this let's create。

Say number format as Nf is equal to number format dot。

 get the compact number instance and we will get it US and again short。

 then we will say here system dot out dot print Ln， save we printing here U slash。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_73.png)

Short。And parsing。Okay， and then we will say。System dot。Our dot print L。

 let's give her Nf dot parse will give you 1 k。Now this， we will give in。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_75.png)

The normal double quotation marks， Okay， similarly。

 let's copy down it here below and now system out dot print L， we are using Nf dot。Ps in bracket。Now。

 this is in double quotes we have given。Here， let's try to give1 M。Okay。Now。

 what we'll have to do is say here， throws your。Pase exception。 So then this will be gone。 Okay。

 similarly， this， we will take it as a 1 B in this case and then。

We say Nf is equal to say number format dot get the compact number instance。

 and now we will take here as long and will take it again off US Now after this again。

 we will take here， say system dot out dot。Print Len。Saying slash n。

 say U s long and then saying here parsing， after which we again say system dot out dot print L and we give here same double quotes first as NF dot parse and then we give in bracket double quotes save1。

Thousand。对。Okay， and then let's copy down this now here well give 1 million and here we give 1 billion okay。

 now let us save this and lets check out the output see。

Thats how you are getting it if it is 1 k is 000 million billion。

 that's how the values are coming when you are using the the par value in your or the par method we can say in that case Okay。

 now lets see another example similarly on parsing。Okay。

 so we' will see an example of par with grouping now Now my default the grouping used is set to false。

 and this may default passing behavior does not allow a grouping separator until your grouping used is set to true。

 So to change the grouping used value， we can use the method set grouping used an which is a boolean type method。

 So now in this set grouping used method we can set whether or not the grouping will be used in this particular format or not。

 So let's see an example on the same。 So let us add first of all a new Java class in this。

 and after adding the Java class， let's remove the comment part。

 and we will first import Java dot text dot， say number format then we will import Java dot text dot parse exception。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_77.png)

And then we will import Java dot uil dot local， and after this inside the class we create public static void main with string arguments and this will。

Through the。Paarse exception。Inside this method， we are going to create a number formats Nf is equal to the number format dot get the compact number instance and will get here for say。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_79.png)

US and the style will be short。 then we say here system dot out dot say print L we are printing here。

 say without。Yeah。Grouping。Okay， and then after this， we print system dot out dot print L。

 say Nf dot。Parts we give here in double quotes 1。Thous0 key Similarlyly lets write down here as 1000 m and similarly below we will write down 1000 B and after this we will say Nf dot said the grouping used to true and after that let us copy down the same system do out but here we will give now this is with grouping and lets give here a slash n and again this all values will remain C so now if we try to execute this this is how you get the value this is without the grouping values we are getting and this is with the grouping values we are getting the actual instance okay so now we'll continue in the next session with with more new method which are introduced in Java to2 which are represented basically with your spring methods so we will see those examples in the next session that's it from this session Thank you very much。



![](img/ee09b2c2e51f74aee8e63de8e19cacca_81.png)