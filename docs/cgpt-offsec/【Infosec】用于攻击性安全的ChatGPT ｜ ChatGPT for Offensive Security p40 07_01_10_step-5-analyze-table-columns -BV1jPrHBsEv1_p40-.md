# 【Infosec】用于攻击性安全的ChatGPT ｜ ChatGPT for Offensive Security p40 07_01_10_step-5-analyze-table-columns -BV1jPrHBsEv1_p40-

![](img/92fd6b030cd7fbdd358dd5f863dcd50d_0.png)

the next thing I want to do is analyze the table column。

 so I'm slowly just drilling down in this information。So let's just cut the output of config。😔。

Not any， so you can see now that this contains the the SS log in password and the database password。

So the next command I want to run is I'm going to output the contents of that file and piper。To SGPT。

 I once again want to return a shell command。And the prompt is。So you kept that as a comment。

And the prompt is analyze the database config， create a command to remotely SSH into the server using SSH Pass。

 then for the remote server log into the SQl database。

 So it is following the same format of finding this prompt that works。

And then I want to list the user table column names and write the column names to a file users。

his or helpful I command there is outted， execute that。Now F LS。

 you might expect to see a user's dot text file， but remember we've run this script from remote from the server。

 so F LS here。I can see users dot text has actually output it to the server。

So what's the next steps I want to do， I want to。Retrive that file from the server。

And pull it to mine and then clean up my tracks。I'm going to use this command。 I'm going to。

 once again。C the SSH details， pipe to SGBT and then I want to return a shell command using SSH details provided。

 use SSH Pass so we can do it from the terminal or without having to enter a password to SSH asking to the server and extract the user。

tex file， delete it from the server afterwards， so I'm not telling it to do this and turning get to generate a command to do this。

And here it's created a password。 Carly I sync the file remotely。And then， SSH it again。And then。

 oh and then remotely remove the file。 So lets execute that。Mfi L on here。

 you see the users dot text file has been removed。And on hair。We have to foe。

And within the file I've got the column names of the database。

 So the reason that I've done this is because I want to craft an SQL air query。

 but I don' the I don't know the database structure I could just ask them as G to try and extrapolate this all at once but I would likely get confused Its much better to break it down into smaller steps。

