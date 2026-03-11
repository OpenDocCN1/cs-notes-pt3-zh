# Python超全入门教程-p25-P25-Python-dictionaries-are-easy--BV1fcdLYXEw9_p25-

Everybody in today's video， I'm going to explain dictionaries。

 A dictionary is one of the four basic collection types for beginners。

 A dictionary consists of key value pairs。 They are ordered and changeable， No duplicates allowed。

 A few examples of key value pairs could be an I D and a name， an item and a price。

 But in today's example we create a dictionary of countries and capitals。

 Let's name our dictionary capitals， Capitals equals enclose your dictionary with a set of curly braces。

 much like what you do with sets。 The first country will be the USA。



![](img/db4e391228134f195e9685c04f60cfcd_1.png)

![](img/db4e391228134f195e9685c04f60cfcd_2.png)

To add a value to this key。Type colon， then some other value。

 The capital of the USA will be Washington， D。 C。

![](img/db4e391228134f195e9685c04f60cfcd_4.png)

Separate each key value pair with a comma。 Then we can add another key value pair。

 So the capital of India。

![](img/db4e391228134f195e9685c04f60cfcd_6.png)

That will be new deli。We'll add two more。China。The capital is Beijing。Russia。The capital is Moscow。

 I think that's good enough。

![](img/db4e391228134f195e9685c04f60cfcd_8.png)

Just as a reminder， if you would like to see all of the different attributes and methods of a dictionary。

 you can use the de function Pass in your dictionary capitals。



![](img/db4e391228134f195e9685c04f60cfcd_10.png)

![](img/db4e391228134f195e9685c04f60cfcd_11.png)

Then we'll need to print this。

![](img/db4e391228134f195e9685c04f60cfcd_13.png)

Here is all the different attributes and methods of a dictionary。

If you would like an in depth description of all these attributes and methods。

 you can use the help function。

![](img/db4e391228134f195e9685c04f60cfcd_15.png)

![](img/db4e391228134f195e9685c04f60cfcd_16.png)

That's her。

![](img/db4e391228134f195e9685c04f60cfcd_18.png)

Help， there we go。

![](img/db4e391228134f195e9685c04f60cfcd_20.png)

So yeah， that's just a reminder。All right， let's go a few of the methods。

To get one of the values from a dictionary， you would get the key。Type the name of the dictionary。

Capitals。ge， Let's get the capital of the USA。

![](img/db4e391228134f195e9685c04f60cfcd_22.png)

Then we'll print it。

![](img/db4e391228134f195e9685c04f60cfcd_24.png)

The value associated with this key， the USA。

![](img/db4e391228134f195e9685c04f60cfcd_26.png)

Is Washington， D。 C， If I picked a different country， like India。



![](img/db4e391228134f195e9685c04f60cfcd_28.png)

Well， then we would get that associated value， which is New Delhi。 Another thing。

 if Python doesn't find a key， this is what will be returned。Let's get Japan。

 which is not in our dictionary。This method would return none。 We can use this。

 within an if statement。

![](img/db4e391228134f195e9685c04f60cfcd_30.png)

If。Capitals dot get。Japan。If a value is returned。Then， we will print。That capital exists。



![](img/db4e391228134f195e9685c04f60cfcd_32.png)

Else。We will print。That capital。Doesn't exist。So Japan is not in our dictionary。

 That capital doesn't exist， but Russia is。That capital does exist。

That's how to check to see if a key is within our dictionary。 You can use the get method。All right。

 moving on。 Let's update our dictionary。Capitals dot update。 So within a set of curly braces。

I will add a key then a value。Germany。Followed by。Berlin。Then let's print our dictionary。

 I'll use a print statement。Print capitals。

![](img/db4e391228134f195e9685c04f60cfcd_34.png)

Yeah， there's Germany right there using the update method。

 we can insert a new key value pair or update an existing key value pair。

 Let's also change one of the existing values with our key USA。



![](img/db4e391228134f195e9685c04f60cfcd_36.png)

![](img/db4e391228134f195e9685c04f60cfcd_37.png)

Let's update the capital to be Detroit。

![](img/db4e391228134f195e9685c04f60cfcd_39.png)

![](img/db4e391228134f195e9685c04f60cfcd_40.png)

Yes， see， the value has been updated。 The capital of the USA is now Detroit， Michigan。



![](img/db4e391228134f195e9685c04f60cfcd_42.png)

To remove a key value pair， you can use the pop method。Then pass in a key。 Let's remove China。



![](img/db4e391228134f195e9685c04f60cfcd_44.png)

China no longer exists within our dictionary。 It's gone。

 You can remove the latest key value pair within a dictionary by using the pop item method。



![](img/db4e391228134f195e9685c04f60cfcd_46.png)

Capitals dot pop。Item with pop item。 you don't need to pass in a key。



![](img/db4e391228134f195e9685c04f60cfcd_48.png)

Pop item will remove the latest key value pair that was inserted。



![](img/db4e391228134f195e9685c04f60cfcd_50.png)

Then， we have clear。Capitals do clear。

![](img/db4e391228134f195e9685c04f60cfcd_52.png)

That will clear the dictionary。 It's pretty self explanatory。



![](img/db4e391228134f195e9685c04f60cfcd_54.png)

The next few methods are a little tricky to explain to get all of the keys within the dictionary。

 but not the values。 There is a keys method， capitals dot keys。



![](img/db4e391228134f195e9685c04f60cfcd_56.png)

I think I'm going to insert this within a variable。



![](img/db4e391228134f195e9685c04f60cfcd_58.png)

Keys equals capitals， dot keys。Let's see what happens when we print this。



![](img/db4e391228134f195e9685c04f60cfcd_60.png)

The keys method will return all of the keys within our dictionary。 Technically。

 keys is an object which resembles a list。 I haven't discussed object oriented programming yet。

 This is a little bit above our level。 If you ever need the keys in a dictionary。

 you can use the keys method。 One use is that we can use that within a For loop。 They're iterable。



![](img/db4e391228134f195e9685c04f60cfcd_62.png)

![](img/db4e391228134f195e9685c04f60cfcd_63.png)

![](img/db4e391228134f195e9685c04f60cfcd_64.png)

For every key in capitals dot keys method。Let's print every key。



![](img/db4e391228134f195e9685c04f60cfcd_66.png)

If at any time you need to iterate over all the keys。

 you can use a for loop to iterate over every key that is returned from the keys method of your dictionary。

 There is also the values method。

![](img/db4e391228134f195e9685c04f60cfcd_68.png)

![](img/db4e391228134f195e9685c04f60cfcd_69.png)

![](img/db4e391228134f195e9685c04f60cfcd_70.png)

To get all of the values within your dictionary， there is a values method。



![](img/db4e391228134f195e9685c04f60cfcd_72.png)

Values equals capitals dot values method。Then， let's print our values。



![](img/db4e391228134f195e9685c04f60cfcd_74.png)

Like before， with the keys method， the values method will return an object， which resembles a list。

 Let's iterate and print over every value within our dictionary for every value in。



![](img/db4e391228134f195e9685c04f60cfcd_76.png)

![](img/db4e391228134f195e9685c04f60cfcd_77.png)

Capitals dot values。

![](img/db4e391228134f195e9685c04f60cfcd_79.png)

Print every value。

![](img/db4e391228134f195e9685c04f60cfcd_81.png)

Here are all the values within our dictionary。This next one is probably the most tricky。

 It is the items method。Capitals do items。I will assign what is returned to a variable named items。

Then we will print items。

![](img/db4e391228134f195e9685c04f60cfcd_83.png)

Items returns a dictionary object， which resembles a 2D list of tuples。 It's really complicated。

 How might this be useful， This time， we're going to use a for loop to print every key comma value in。



![](img/db4e391228134f195e9685c04f60cfcd_85.png)

![](img/db4e391228134f195e9685c04f60cfcd_86.png)

Capitals dot items method。

![](img/db4e391228134f195e9685c04f60cfcd_88.png)

We have， in essence， two counters this time。I will print using an F string， every key value pair。

I will print every key。As well as every value in our print statement。



![](img/db4e391228134f195e9685c04f60cfcd_90.png)

So there's our dictionary laid out。 We have iterated over every key value pair。

 It's kind of an advanced topic， but I thought I would at least bring it up now。 So yeah。

 that's a dictionary， everybody， It's a collection of key value pairs。

 They are ordered and changeable。 No duplicates allowed。 You have a bunch of different methods。

 such as get update， pop， pop item clear。 Then you can get the keys。 The values。

 or both which is the items method， We'll be using dictionaries and a few game programs we'll be making in the future。

 And， well， yeah， those are dictionaries in Python。😊。



![](img/db4e391228134f195e9685c04f60cfcd_92.png)

![](img/db4e391228134f195e9685c04f60cfcd_93.png)

![](img/db4e391228134f195e9685c04f60cfcd_94.png)

![](img/db4e391228134f195e9685c04f60cfcd_95.png)

![](img/db4e391228134f195e9685c04f60cfcd_96.png)

![](img/db4e391228134f195e9685c04f60cfcd_97.png)