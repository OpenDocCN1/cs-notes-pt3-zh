# Python超全入门教程-p15-P15-Format-specifiers-in-Python-are-awesome--BV1fcdLYXEw9_p15-

Hey， everybody， in this topic， I'm going to explain format specifiers。 format specifiers。

 when used in the context of F string， they allow us to format a value based on what flags are inserted。

 following your value。 You would type a colon and then some flags。

 depending on what flags you insert， It will format your output a certain way。

 You could add decimal point precision。

![](img/430574d3a031a6a2ebda2fe02f026c51_1.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_2.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_3.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_4.png)

Alloccate space，0 pad values left。 justify， right， justify， center line， all sorts of things。



![](img/430574d3a031a6a2ebda2fe02f026c51_6.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_7.png)

Let's have some practice。 I'll create three prices， price  one。Price2。Price 3。Price 1 will be 3。

14159。 These values aren't 10 and cents yet， but they will be。Price 2 will be negative 9，8，7 dot6，5。

 As you can see， I'm just making up numbers here。Price 3 is 12 dot3，4。Let's display our prices。

 using some up strings。Price 1 is。

![](img/430574d3a031a6a2ebda2fe02f026c51_9.png)

Placeholder， price1。Then we will do this for price 2 and price 3。



![](img/430574d3a031a6a2ebda2fe02f026c51_11.png)

Price 2 is price 2。 Price 3 is price 3。

![](img/430574d3a031a6a2ebda2fe02f026c51_13.png)

Within our placeholder， following the value， we can add a colon。 then some flags。

 Those flags are the format specifiers。 They will format our value a particular way。

 depending on what we insert after the colon to add a decimal point precision。

 you would type after the colon。

![](img/430574d3a031a6a2ebda2fe02f026c51_15.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_16.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_17.png)

Dot。😡，Thenhan the amount of decimals to be displayed。 maybe two。

 then F meaning floating point number。 Let's do that with price 2 and price 3。



![](img/430574d3a031a6a2ebda2fe02f026c51_19.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_20.png)

Colon dot2 F。Price 1 is now 3。14。 Price 2 is negative 987 dot 6，5。 Price 3 is 12。34。



![](img/430574d3a031a6a2ebda2fe02f026c51_22.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_23.png)

I think I'm going to add some dollar signs before the placeholder。



![](img/430574d3a031a6a2ebda2fe02f026c51_25.png)

Yeah， that's much better。

![](img/430574d3a031a6a2ebda2fe02f026c51_27.png)

For less precision， maybe one decimal place， you can change the two to a one。So point1 F。

Each number only displays one decimal，01。6。3。

![](img/430574d3a031a6a2ebda2fe02f026c51_29.png)

Whereas in 03 F would display three decimal places。t142。650。340。

 Even though price 2 and price 3 only have two decimal places in the original numbers。

 we will concatenate some additional zeroes。

![](img/430574d3a031a6a2ebda2fe02f026c51_31.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_32.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_33.png)

To allocate space to display a value after the colon， add some number。

 some number for that many spaces。 How about 10。

![](img/430574d3a031a6a2ebda2fe02f026c51_35.png)

Each value now has a total of 10 spaces to display the output，1，2，3，4，5，6，7，8，9，10。

If you were to pre see it， a number with 0， well， these numbers would be0 padded。

Each number is now zero paded。To left justify a value， you would use a left ankle bracket。

All these numbers are now left justified。 Then we have all of the space after。They're all uniform。

Right justify would be a right angle bracket。And I believe that's the default。Central line。

 I believe， is the carrot symbol。Yep， our numbers are now centered。



![](img/430574d3a031a6a2ebda2fe02f026c51_37.png)

If you have any positive values and you would like to display a plus sign， just use plus。



![](img/430574d3a031a6a2ebda2fe02f026c51_39.png)

Any positive number is preceded with a plus sign。 Any negative number is preceded with the negative sign。

 or you could use a space for any positive numbers。 So colon space。



![](img/430574d3a031a6a2ebda2fe02f026c51_41.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_42.png)

These numbers are lined up evenly， even though we have a negative number in here。

 There is a000 separator， which is a comma。

![](img/430574d3a031a6a2ebda2fe02f026c51_44.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_45.png)

We should probably increase the availability of our prices。



![](img/430574d3a031a6a2ebda2fe02f026c51_47.png)

3000 negative 9871200。

![](img/430574d3a031a6a2ebda2fe02f026c51_49.png)

Each thousands place is now separated with aa。 We could also mix and match flags。

 I would like 1000 separator， along with decimal point precision of two decimal places。



![](img/430574d3a031a6a2ebda2fe02f026c51_51.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_52.png)

And why not？ I will precede each number with a plus sign of its positive。



![](img/430574d3a031a6a2ebda2fe02f026c51_54.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_55.png)

Yep， here we are。So based on what you're looking for， you can add some combination of flags。 So yeah。

 those are format specifiers， everybody。

![](img/430574d3a031a6a2ebda2fe02f026c51_57.png)

![](img/430574d3a031a6a2ebda2fe02f026c51_58.png)

Within your placeholder。Insert your value， a colon。

 then certain flags based on what you're looking for exactly。



![](img/430574d3a031a6a2ebda2fe02f026c51_60.png)

But yeah， those are just a few format specifiers in Python。



![](img/430574d3a031a6a2ebda2fe02f026c51_62.png)