# 【阿尔伯塔大学】问题解决Python编程和电子游戏 ｜ Problem Solving, Python Programming, and Video Games p73 08_03_01_create-algorithm-for-hacking-version-7 -BV1N5rLBWE1c_p73-

![](img/00c06224c4630689b877eac09cc8086e_0.png)

This is the final algorithm for hacking。 You will add two new features。

 embedding the passwords in random symbols and displaying hints。

 You will need two new panels for each of these features。😊。

You will also need to modify to existing panels。I'll start the steps for embedding the passwords。

 Your previous algorithm used a definite repetition control structure to display each password line。

I'll change the repeated step from display password line to display embedded password。

Since I must embed each password， the blank line that is displayed after the password list can no longer be an element in the password list。

 If it is， the blank line will also be embedded in random symbols。

I will add a step to display the blank line prior to selecting the password。

To display an embedded password， first， I must add symbols to the plain password。

 and then I must display it。 Each of these actions is complicated enough to have its own algorithm step。

Since you cannot put two consecutive steps inside a control structure。

 display embedded password must be expanded into a new panel。

You must also make an additional new panel to expand embed password。

 since it will require many program statements， including control structures。

Here are a few things to keep in mind。 Each embedded password string has 7 password letters and 13 random symbols selected from a set of 18 symbols。

 Since each line contains 13 symbols， A random number symbols between 0 and 13 will appear before the password。

 and the remainder will appear after the password。For example， here are three embedded passwords。

 The first has five before the password and 8 after。 The second has 0 before and 13 after。

 and the third has 13 before and 0 after。You must compute how many of the 13 symbols to add before the password and how many to add after。

This split in the random symbols where the password is added， will be called the split index。

 For example， in the lines above， the split indexes are 5，0 and 13。

You should use two separate definite repetition control structures。

1 to select and concatenate the random symbols that come before the password and one for the random symbols that come after the password。

To display hints， you will also need two new panels。

 add a display hint step to the appropriate place in the get next guest panel and expand it。

Displaying the two lines of the hint is straightforward。

 but you will need to use two different control structures to check if the letters in the guests match the letters in the password。

When you check a letter in the guess against a letter in the correct password。

 don't forget to ensure that the index you are checking is not beyond the end of the password。

You will finish your last hacking algorithm in the next activity。



![](img/00c06224c4630689b877eac09cc8086e_2.png)