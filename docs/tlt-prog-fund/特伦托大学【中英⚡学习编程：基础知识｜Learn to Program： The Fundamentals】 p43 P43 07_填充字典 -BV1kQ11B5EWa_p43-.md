# 特伦托大学【中英⚡学习编程：基础知识｜Learn to Program： The Fundamentals】 p43 P43 07_填充字典 -BV1kQ11B5EWa_p43-

![](img/d060903d40ac9fe58fec019321037a63_0.png)

In this lecture， we're going to combine some of the different topics that we've covered。

 We're going to read data from a file and store it in a dictionary。



![](img/d060903d40ac9fe58fec019321037a63_2.png)

In this lecture， we're going to work with the file on the left hand side of your screen。



![](img/d060903d40ac9fe58fec019321037a63_4.png)

It contains assignment 1 grades。 There are two columns， one for a student I D。

And a second for the grade that the student with that ID earned on the assignment。



![](img/d060903d40ac9fe58fec019321037a63_6.png)

If you watched the optional lecture from last week。

 the data will look familiar and the task will be a bit familiar， too。 But this time。

 we're working with dictionaries rather than with lists。



![](img/d060903d40ac9fe58fec019321037a63_8.png)

We're going to write the function。 regrades。 It has one parameter。

 which is a file that has been opened for reading。That file will start with a header that contains no blank lines followed by a blank line。

 and then the lines of the file with the student number and the grade。



![](img/d060903d40ac9fe58fec019321037a63_10.png)

The task that this function will complete is to read the grades information from the file and build a dictionary。



![](img/d060903d40ac9fe58fec019321037a63_12.png)

Each key is a grade and each value is the list of ID of students who earned that grade。



![](img/d060903d40ac9fe58fec019321037a63_14.png)

For example， for the grade 77。5 for that key。

![](img/d060903d40ac9fe58fec019321037a63_16.png)

There will be a list containing student ID 0052 and student ID 1311。

Because those two student Is earned that grade。There may be other students as well。

 later in the file who will appear in the values list for that key 77。5。



![](img/d060903d40ac9fe58fec019321037a63_18.png)

To implement this function， we need to perform two main tasks。

First is we need to skip over the header。Once we've skipped the header。

 we can move on to reading the grades from the file and accumulating them in the dictionary。

We'll begin by skipping the header。We have four ways to read from a file。

 and since we're only processing part of the file， we're going to use the Readline approach。

So we'll start by reading one line of the file。

![](img/d060903d40ac9fe58fec019321037a63_20.png)

And we want to keep reading the lines of the header until we reach the blank line。



![](img/d060903d40ac9fe58fec019321037a63_22.png)

A blank line isn't truly blank。 It contains the new line character。 So as long as the line is not。

 the new line character will keep reading。That would be part of the header。

Once the header has been skipped， we can move on to accumulating the grades into a dictionary。

The accumulator I'll use is grade2 Is， and it will initially be empty。



![](img/d060903d40ac9fe58fec019321037a63_24.png)

Well need to read the next line of the file。We can do that using Readline。



![](img/d060903d40ac9fe58fec019321037a63_26.png)

And we want to keep reading lines of the file until the end of the file is reached。

That would mean that the line would be empty， so we want to continue reading as line as line is not equal to the empty strength。

Once we've read a line， we need to extract the student ID and the grade。

The student IDs are all four characters， so we'll use that information。



![](img/d060903d40ac9fe58fec019321037a63_28.png)

Student ID will be a slice of the linell get the line from the beginning up to the fourth character。



![](img/d060903d40ac9fe58fec019321037a63_30.png)

So that will give us a string containing the four digits of the student ID。

The grade is going to be what it comes after that， although there are a couple of spaces before the grade and there's a new line character after the grade。

 So what we can do is we can take the rest of the line and strip out the white space that comes before and after it。



![](img/d060903d40ac9fe58fec019321037a63_32.png)

The grave will be a slice from index 4 to the end of the line。

 but will strip off the white space for the gra。

![](img/d060903d40ac9fe58fec019321037a63_34.png)

We aren't quite done working with G yet。We want grade to refer to a float， not a string。

 and currently， it refers to a string that contains a numeric value。

We're going to apply float to that string to get back a floating point number。

Now that we have the grade and student ID， we need to add them to the dictionary there are two scenarios to consider one is that the grade is not yet a key in the dictionary。

And the other is the case where grade is already a key in the dictionary。

We'll consider these two cases separately。We'll start with the case where the grade is not yet a key in the dictionary。

 So if grade。Is not in。Craade to ID。In that case， we need to add it for the first time。

We can access grade2 IDs。And set grade as a key assign to it the value， which is a student I D。

Student ID is just a string though， and the value associated with a key for this dictionary needs to be a list of strings。

 so we need to put student ID in a list。We can use the square brackets to do so。

The second case is the case where grade is already a key in the dictionary。

 So if that if condition is false， we need to do something different because grade already is a key。

Because it's a key already。 there already is a value associated with it。

 and that value is a list of strengths。 We want to add student I D to the list of strengths。

So we need to access that list of strings， and we can do that by looking at the dictionary and looking up the value associated with the key grade。

 This gives us a list of strings。And to it， we can append the student I。So in this case。

 we don't need to make a new list， we're just going to add student ID to the existing list。

Once we finished adding this grade and student ID to the dictionary。

 we can move on to the next line of the file so we'll read another line。

Once all of the lines of the file have been read， the while loop condition will become false。

 and we can return the grade to IDe dictionary。Now that we've finished writing this function。

 we can run it。To begin， I have to open upgrades file。Which happens to be stored at this long path。

And then I can call read grades， passing that grades file is the argument。



![](img/d060903d40ac9fe58fec019321037a63_36.png)

And it returns a dictionary。We can see in this dictionary that 77。

5 does have student ID 052 as one of its values， along with 1311。And actually。

 several other student IDs earned that grade。