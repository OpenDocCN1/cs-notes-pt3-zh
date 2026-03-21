# 【全集】慕尼黑工业大学 计算机编程：从入门到实战 中英字幕 p02 Lecture 2 - 使用调试器 -BV1WFrTBZExY_p2-

The debugger allows you to inspect what your program is doing， while it is running。



![](img/1d095a81a56817284a009bb44bebba87_1.png)

The first step to using the debugger is always to set a bright point。

 A break point indicates to intelligent that you would like to pause execution of your program when it hits that break point。



![](img/1d095a81a56817284a009bb44bebba87_3.png)

![](img/1d095a81a56817284a009bb44bebba87_4.png)

In our case， I'm going to put one here on line 24。

![](img/1d095a81a56817284a009bb44bebba87_6.png)

And then click the little green arrow again。 but this time pick the debug option。



![](img/1d095a81a56817284a009bb44bebba87_8.png)

When we do that， we will see that the line is highlighted in blue。

 which means that execution is paused on that line。Down here in this pane。

 we can see all the variables which are currently in scope。 So， for example， our deed。

 our seal citizen。 And if we click on this arrow， we can also see the attributes that our seal citizen has。



![](img/1d095a81a56817284a009bb44bebba87_10.png)

![](img/1d095a81a56817284a009bb44bebba87_11.png)

If we want to continue execution， we have a couple of options with this arrow。

 we can step into the methods being run on the current line。 So in our case， check history with code。



![](img/1d095a81a56817284a009bb44bebba87_13.png)

I'm going to click that once， and now we're inside this method。

 and I would like to go further into the search with code method。

 So I'm going to click the same arrow again。

![](img/1d095a81a56817284a009bb44bebba87_15.png)

![](img/1d095a81a56817284a009bb44bebba87_16.png)

Here we already have an idea why we are returning null because we are checking all the citizens and none of the codes are matching。



![](img/1d095a81a56817284a009bb44bebba87_18.png)

In that case， we can set a break point here on this line and click the green arrow to resume our program until it hits the next break point。



![](img/1d095a81a56817284a009bb44bebba87_20.png)

Now we're here and we can actually see， yes， it is returning null。And if we know that。

 we can step out of the method again。

![](img/1d095a81a56817284a009bb44bebba87_22.png)

And pop back up。And now we can step over this line。



![](img/1d095a81a56817284a009bb44bebba87_24.png)

Which just means to go to the next line， basically。

And we can actually see that citizen isnll down here in our variablesables pane。



![](img/1d095a81a56817284a009bb44bebba87_26.png)

And that tells us that because we're calling preded history on this citizen that we're getting a nonmentary exception。



![](img/1d095a81a56817284a009bb44bebba87_28.png)

We can verify that if we resume our program。

![](img/1d095a81a56817284a009bb44bebba87_30.png)

And then in the console， it will give us the same output as before。



![](img/1d095a81a56817284a009bb44bebba87_32.png)

Now we know that on this line here， we have to make sure to check that the citizen is not null and if it is null。

 then we have to find something else with you， for example。

 we print that there is no seal to be found。

![](img/1d095a81a56817284a009bb44bebba87_34.png)

If after debugging， you still don't know why your code is failing。

 you should also check the discussion on ArtIS， of course， or ask your tutor。



![](img/1d095a81a56817284a009bb44bebba87_36.png)

I hope this helps。