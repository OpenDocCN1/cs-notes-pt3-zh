# 【EDUCBA】构建嵌入式系统 ｜ ARM Cortex (STM32) Fundamentals： Building Embedded Systems p07 01_02_03_scanf练习实现 第二部分 -BV1KjcTzUEeY_p7-

Mail owners， welcome back。 So now let's discuss our next topic in this particular session from where we have left in the earlier video。

 so I'll continue it from the same。Now， what happened over here was after the last printf。

 the command was not steady right it the screen was not hold there over here。

 what we have to do is after this printf actually this statement is not needed will have to write down some logic over here so that our program will hang on after printing the result。

 what we can basically do is we can make the application wait until the user presses any key from the keyboard that is with the help of getca。

 which is a function available getca basically is a function that stays onto your screen till the user presses any key whenever the user press any key。

 the keyboard character would be caught by this particular function and then that will be utilized to exit your program over here I have given get care open close bracket and then just the semicolon nothing has to be given over here once you have given this particular syntax Now just build this project。

Here and then go back to your debug and open this and。



![](img/e2df4fa2f61bc21fdee706fa89193f41_1.png)

![](img/e2df4fa2f61bc21fdee706fa89193f41_2.png)

You know， try to enter some numbers。And now I just pressed key multiple times。



![](img/e2df4fa2f61bc21fdee706fa89193f41_4.png)

![](img/e2df4fa2f61bc21fdee706fa89193f41_5.png)

Let me just do it again。And now， as soon as you press enter， they still not holding。

Let me do it a thing。 after this sf。We print this particular average。I give。I flush a steady out。

 and then I use a get care。 I build this， and。I open up this。

What mistake we are doing is after printing this， I am giving heroes Earth command， saying press。

Anarch key2。Exit thee。Application， and then below that I am giving a get care。

Now let me build this and let me open this。

![](img/e2df4fa2f61bc21fdee706fa89193f41_7.png)

![](img/e2df4fa2f61bc21fdee706fa89193f41_8.png)

Okay， now this problem could be solved by giving here two get care solutions or two get care functions。

Now， this is not a generic solution。 I am only adding this getcare to show you the effect that you can be looking under if you give multiple getca。

 because here you are printing this particular line after that。

 this gets printed one gettca will not hold the particular application。 Now。

 if you give the second getca because of that， the application would hold your screen till you enter any particular character then Now。

 if I try to build this and I try to。Open up this， and I enter。



![](img/e2df4fa2f61bc21fdee706fa89193f41_10.png)

And see， print the average and gives me the message and the cursor is still death。 Now。

 if any key I press from the keyboard， my application will stop okay， even if I press enter key。

 I press any character key and I enter whatever。 Now over here。

 as I told you earlier that this is not something that is generic solution over here。

 normally what we do is we use a loop normally。😊。

![](img/e2df4fa2f61bc21fdee706fa89193f41_12.png)

In this particular application， instead of giving you multiple get cat statements。

 I basically give here a loop， something like I say。Sa well cover this in the later on session。

 but I am just showing it to you so where getca is not equal to， let's say。New line。

 And then inside this， basically。We can give some particular statement。

 We can input some data over here。 Then this get care statement is not needed。 Now。

 if I have given this and I try to build this。 Okay， and I go here。I open the application。



![](img/e2df4fa2f61bc21fdee706fa89193f41_14.png)

![](img/e2df4fa2f61bc21fdee706fa89193f41_15.png)

嗯。

![](img/e2df4fa2f61bc21fdee706fa89193f41_17.png)

![](img/e2df4fa2f61bc21fdee706fa89193f41_18.png)

Let me try to build this again。And。

![](img/e2df4fa2f61bc21fdee706fa89193f41_20.png)

![](img/e2df4fa2f61bc21fdee706fa89193f41_21.png)

Once I have given this of high loop here。Then again， I am giving her a get care statement。

 and I am building the project。

![](img/e2df4fa2f61bc21fdee706fa89193f41_23.png)

And now should hold my screen。De I。See the。Average。

 now it is saying press any key to exit the application。

 and my screen is still on the saving command。 So if I press any key， my screen is gone。



![](img/e2df4fa2f61bc21fdee706fa89193f41_25.png)

Instead of using two get care， this is actually a more generic solution to use it。 Now。

 there is another way in which you can accept the three numbers in just one single printf statements and scanf or other one single scanf statement I can say。

 I don't have to write that many scanf statements。 and I don't have to create all this bigger program。

 which I can do it in a very smaller one as such。 So what I'll do is in the same program。

 I'll modify。 I will keep all this。I'll just。Make this as commed to give an entire comment。

 You have your addda。Block command for this。I'm giving you another option which you can do that。

 Okay， I don't want to create a separate file for this。 That's not needed over here。

 I'm giving the first print of statement that I'm saying here， enter4。Numbers。

 if I'm going over here。Im giving this particular statement over here， and after that。

 I basically want to do a scanf for all the numbers in one single scan below this。

 I can use one scanf statement。And inside this， I am writing here the first scanf for the first format specifyifier as percent。

Second， third and fourth for phone numbers。 Then Im putting here。Numb one。Numb 2。Numb 3。Numb 4。

 once I have given that， then I have the average。 I print the average。

 and this everything remains same。 Let me save this。

 Let me build this and let me go here and execute this。



![](img/e2df4fa2f61bc21fdee706fa89193f41_27.png)

And see， I can do it over here。 I don't have to give a separate print of statement。

 I can simply give it over here。Or I can also give it like this。Give a space and give phone numbers。

 then press enter。 Even that is possible。 I get average value。

 and then the screen stays till I enter a particular key from my keyboard。

 This was another way doing the same programme。 You can just see how many lines of code we completed this and the earlier one。

 We had used some 4，5，6 lines extra， which were not needed。

 It is a reason like you should be aware about how to create programme in more easier manner instead。

 you know， just creating it muff in multiple lines of code。

 That is how you can actually do it and see the particular scanap statement， how it worked。

 Try out the programs and stay tuned with me for more such videos till then have a nice day。

 Thank you。

![](img/e2df4fa2f61bc21fdee706fa89193f41_29.png)

![](img/e2df4fa2f61bc21fdee706fa89193f41_30.png)