# 【Net-Ninja】Git入门教程-p04-P04_Git_Crash_Course_#4-暂存文件--BV1fkvtBcERR_p4-

Or rather than gang。 So in this lesson， we're going dive into how Git actually organizes and tracks your project files。

 Now， this is probably the most important concept to understand in Git， because once you get this。

 everything else just kind of falls into place around it。

 and we're going to be working with this project to see how all of this works。

 So then the way Git tracks your files is by organizing them into three distinct areas and understanding these three areas is kind of crucial for using Git effectively。

 So the three areas are the working directory， the staging area and the repository itself。

 The working directory is just your project folder where you create and edit files。

 The staging area is where you line up changes you want to include in your next commits。

 and the repository is the history of all the commits that Git has stored。😊。



![](img/02986e60fa43bbb48d3c5bb8f8c4c322_1.png)

Then by using Git commands， you can decide when changes move from your working directory into staging and when stage changes are committed to become part of the repository's history For example。

 you would start by editing a file in your project folder that's the working directory when you're happy with that change you add it to the staging area so Git can track it which is almost like putting a product in a shopping cart before you decide to buy it then when you're ready to make it permanent you commit the change and that takes everything in the staging area and saves it into the repository's history and using that shopping cart analog again this would be like buying the product I guess。

So that's the general flow of things right， we edit the files。

 we add them to the staging area and then we commit the changes or to put it more simply， we edit。

 then we add， then we commit， and you'll be using this whole workflow quite frequently。 editit。

 add to staging commit。😊，In our project we already had a project folder with the files inside it and when we initialized a Git repository for that project using Giting it。

 Git became aware of everything inside that project folder the working directory but currently it's not tracking any of these files because we've not added them to the staging area so if we wanted to store our current version of this project to the repo history。

 we'd have to add whatever files we want to track to the staging area first of all。

 most of the time that's going to be all or if not most of these files for the first version you want to commit to Gis history unless there's something specific you don't want Git to track。

Then once we're happy with the files inside the staging area。

 we'd make what's called a commit to commit this version of the project to the repo history Now we'll talk more about commits later but for now let's try adding our files to the staging area。

Alright， so let's have a little look at what's going on in our project so what I'm going to do is first of all run a command which is Gisdaus and when you run that you're going to see we have all these un tracked files okay。

😊，Now untractracked files in a Git repo basically mean new files that you've created that Git hasn't tracked yet。

 so there's no commit for these files。😊，So in order for them to be tracked files， we first of all。

 have to add them to the staging area and ultimately later it commit them。😊。

So let's clear down here and then try adding some files to the staging area。 How do we do that？ Well。

 we use the command Git add， followed by whatever file we want to add。 So， for example。

 index dot HTML。 And if I press enter and then run git status again。

 we should see that now we have this green file right here。

 it's a new file called index HTML and that is now in the staging area。

 And it has this heading Change to be committed。 So anything that's staged will be shown right here。

😊，Now you can add multiple files at once， so let me show you how to do that we can say gi add again every time you're adding something to the sta and area it's always git add and then you can just list out the different files so for example。

 about dot HTMLt and then contact do HTMLtm。😊，So if I press enter it out and then run a git data scan。

 they should all be listed inside the staging area right here。

 A Now I actually want to add everything to the staging area。

 and this is pretty typical when you're first out in out a project。

 if you initialize a repository normally you want to add all the files to the staging area to make some kind of initial commit Now there are cases when you don't want to add every single file and we'll cover those later but for me right now I want to add every single file and we can run a command called git add again。

 but this time。😊，We're going to use a dot after this。 And what this does is say， look。

 I want you to take every new file that you've created or every changed file。

 And I want you to add all of those things to the stagearian。 So when I run this now。

 everything should now be in the stagearian。 So if I run Git status。😊，Like so and press enter。

 we can see now all of those are in the staging area。😊。

So just really quickly then let me just go over what we've done using these slides We had a project folder which was nothing to do with GitI and then we created a Git repository inside it when we did that Git became aware of all the files in the working directory but it wasn't tracking any of them initially not by default right that is the default behavior for any new files in the repo whether it's when you first initialize the repo or you could add new files later on they always un trackracked to begin with。

😊，Then because we won't get to track every file in the working directory。

 we added them all to the staging area by using the command Git addd followed by a dot add every file。

 And this means all those files and how sitting in the staging area waiting for us to commit them to the history。

 Now， at this point， you might be asking well， why even bother with a staging area。

 Why can't we just run one command to commit a version to the history directly and skip out this staging area。

 And the answer to that question will come naturally， I guess， as we work through this course。

 But essentially， the staging area lets us be really precise about what files and changes we want committed in a particular version。

 I guess you might have made changes to say10 different files。

 But maybe you only want to save three of them right now because they're all related to one single feature。

 The staging area lets you group related changes together。 And again。

 as we practice more with this workflow over the common lessons。

 you're going to see some examples of this。 For now。

 the two biggest points are want you to take away from this lesson either。😊，Firstly。

 all new files in the working directory are on tracked to begin with and two the second point is that we have to add files to the staging area when we won't get to track them before we commit them to the repository history Allright so now we've added the files to staging let's try making a commit in the next lesson。

😊。

![](img/02986e60fa43bbb48d3c5bb8f8c4c322_3.png)